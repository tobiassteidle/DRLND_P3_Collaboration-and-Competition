## Learning Algorithm

My learning algorithm is a Deep Deterministic Policy Gradient.  

DDPG is an actor-critic algorithm and primarily uses two neural networks.  
One for the actor and one for the critic. These networks calculate action vectors for the current state and and generate 
a temporal-difference error signal each time step.

DDPG uses a stochastic behavioral policy for good exploration and a deterministic target policy for estimating.

The current state is the input of the actuator network and the output is a single value representing the action. The deterministic policy gradient theorem provides the update rule for the weights of the actor network.  

The critic's output is simply the estimated Q-value of the current state and the action given by the actor.
The critic network is updated from the gradients obtained  from the TD error signal.

My implementation is based on "[DRLND_P2_Continuous-Control](https://github.com/tobiassteidle/DRLND_P2_Continuous-Control)" and extended by details like e.g. batch normalization and modfied hyperparamters.

In my implementation the Actor network contains two hidden layers of 128 and 64 units with ReLU activation applied to both layers and a tanh on the end.  
In addition, a batch normalization is applied to the input and between the hidden layers.  

The Critical network also has two hidden layers with 128 and 64 units and ReLU Activation on both layers.


More general information about DDPG in [this](https://arxiv.org/pdf/1509.02971.pdf) paper.   

### Hyperparameters
Parameter | Value
--- | ---
replay buffer size | int(1e6)
minibatch size | 256
discount factor | 0.99  
tau (soft update) | 1e-3
learning rate actor | 1e-3
learning rate critic | 1e-3
L2 weight decay | 0
epsilon | 1.0
epsilon decay | 1e-6

### Plot of Rewards

Episodes | Average Score | Max | Min | Time
--- | --- | --- | --- | ---
... | ... | ... | ... | ...
Episode 181 | Average Score: 33.59 | Max: 39.64 | Min: 30.34 | Time: 23.88
Episode 182 | Average Score: 33.76 | Max: 39.45 | Min: 30.88 | Time: 23.98
Episode 183 | Average Score: 33.92 | Max: 38.23 | Min: 20.35 | Time: 23.96
Episode 184 | Average Score: 34.08 | Max: 38.29 | Min: 27.17 | Time: 23.83
Episode 185 | Average Score: 34.24 | Max: 39.54 | Min: 30.72 | Time: 23.93
Episode 186 | Average Score: 34.40 | Max: 39.38 | Min: 34.30 | Time: 23.97
Episode 187 | Average Score: 34.55 | Max: 39.53 | Min: 34.66 | Time: 23.94
Episode 188 | Average Score: 34.69 | Max: 39.40 | Min: 31.07 | Time: 24.11
Episode 189 | Average Score: 34.85 | Max: 39.59 | Min: 33.47 | Time: 24.00
Episode 190 | Average Score: 35.00 | Max: 39.47 | Min: 30.89 | Time: 24.00
Episode 190	| Average Score: 35.00 | | |  

Environment solved in 190 episodes!	Average Score: 35.00

![Solution](report/Score_Plot.png)

## Ideas for Future Work

- Change network sizes and choose different hyperparameters
- Trying other algorithms like PPO, A3C or D4PG
  





