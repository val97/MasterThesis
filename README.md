Nowadays, Recommender systems play a key role in managing information overload, particularly in areas such as e-commerce, music and cinema. However, despite their good-natured goal, in recent years there has been a growing awareness of their involvement in creating unwanted effects on society, such as creating biases of popularity or filter bubble. This thesis is an attempt to investigate the role of RS and its stakeholders in creating such effects. A simulation study will be performed using EcoAgent, an RL-based multi-stakeholder recommendation system proposed by Zhan et al[1], in a simulation environment that captures key user interactions, suppliers and the recommender system in order to identify possible unhealthy scenarios for stakeholders. In particular, we focus on analyzing the document catalog to see how the diversity of topics that users have access to varies during interactions. Finally, some post-processing methods will be defined on EcoAgent, one reactive and one proactive, which allows us to manipulate the agent’s behavior in order to study whether and how the topic distribution of documents is affected by content providers and by the fairness of the system. 

## References
<a id="1">[1]</a> 
Ruohan Zhan et al. “Towards Content Provider Aware Recom-
mender Systems: A Simulation Study on the Interplay between
User and Provider Utilities”. In: Proceedings of the Web Confer-
ence 2021. 2021, pp. 3872–3883


The code is organized into the following subdirectories:
* environment: implementation of a gym ecosystem based on RecSim.
This ecosystem consists of users, creators, and an agent, and models the
interaction among these three parties.
- To create a gym environment, call
`env = environment.create_gym_environment(env_config)`.
An instance of env_config can be found in environment.ENV_CONFIG.

- To adjust the environment setup, change the corresponding hyperparameters in
the env_config. To see the definition of different hyperparameters, please refer
to the creator.DocumentSampler() and user.UserModel().
Interesting hyperparameters may include:
-- creator_recommendation_reward
-- creator_user_click_reward
-- creator_is_saturation
-- creator_topic_influence
(whether creator.topic_preference is influenced by the user-consumed documents.)
-- copy_varied_property (whether to create two identical creator groups)

- To change the user reward function, see user.py in one of the following:
-- UserState.score_document()
-- UserModel.create_response()

* recommender: implementation of user/creator RNN utility models
(both in value_model.py) and policy gradient actor model in agent.py.

* experiment: implementation of running RandomAgent(value_model_experiment.py)
and EcoAgent(ecoagent_experiment.py).
