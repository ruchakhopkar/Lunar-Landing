# Lunar-Landing
Using Deep Q-Learning for Landing a Rocket


https://github.com/ruchakhopkar/Lunar-Landing/assets/70127769/880d0699-0aae-42c2-b0c0-1869cead5035

Increasing the learning rate from 5e-5 to 2e-5 helped us achieve the perfect lunar landing.

https://github.com/ruchakhopkar/Lunar-Landing/assets/70127769/c98206d3-19da-47c7-a45e-1dde5b8e8b94

<br> I have used one of the environments from [gymnasium](https://gymnasium.farama.org/content/basic_usage/) called LunarLander-v2.
<br> I built a neural network containing linear layers which gives as output, the action values(size 4). 
<br> The input in this case is a vector of size 8 describing the position of the satellite as well as linear and angular velocities.
<br> I then create an agent with 2 functions: act and learn(step)
<br> In the act function, given a state the agent will take some action based on the output from the neural network. The action is chosen based on a epsilon greedy policy for exploration-exploitation.
<br> In the step function, the agent actually learns. We get the current Q values from the local network and the target Q values from the target network. Having 2 networks helps to stabilize the learning process. Since the environment of the agent is continuously changing, it is good to have a target network which is only updated once in a few steps. The loss is calculated as the MSE loss between the target Q values and the expected Q values. 
<br> I used Adam as an optimizer. 
<br> I also maintain a memory that holds the experiences of the agent. When the agent learns, we can uniformly sample mini batch size number of experiences from this memory to train the agent on. This ensures we are not biasing the agent on tasks that occur frequently. 
