---
layout: post
comments: true
title:  "Let's learn reinforcement learning! Part 2: Q-learning"
excerpt: "In this post I describe Q-learning, a popular reinforcement learning algorithm, and how it can be used to "
date:   2018-04-18 11:31:00
mathjax: true
comments: true
---

UNDER CONSTRUCTION

In my last post, we investigated what reinforcement learning is and how CEM-ES, a simple evolutionary algorithm, can be used to solve certain environments. In this post, we will investigate a technique called Q-learning and its successes.

Q-learning is a reinforcement learning algorithm popularized by Mnih et al. in 2015, with their article *Human-level control through deep reinforcement learning*. These researchers were able to use a neural network to achieve superhuman performance on many Atari 2600 games, based off of only the screen data and scores of these games, without any change to the network's architecture. It achieved a superior performance to the best linear methods on most games.

<img src = "/images/dqn_article/performange.png">
(image from Human-level control through deep reinforcement learning, Mnih et al. 2015)

While having been invented by other people, Mnih et al. were the first people to popularize Q-learning with a deep neural network. The goal of Q-learning is to use a neural network to predict the expected rewards from a given state-action pair. Essentially, we want to map from a given state to whichever action will yield the highest expected sum of rewards, using a neural network. 

$\pi_\theta(s) = max_a(Q(s,a))$

Where $Q(s,a)$ is the value of an action $a$ at a state $s$, so $Q(s,a)$ is the value of the state-action pair. The values of state-action pairs are called q-values. We want to build a neural network that maps from states to expected values for each action, so our neural network will approximate $Q(s,a)$. We will test out how q-learning performs on the pole balancing problem before moving to something more complicated.

It might seem that we would want our neural network to predict the sum of rewards like so:
$Q(s,a) = \mathbb{E}[r_t + r_{t+1} + r_{t+2} ...]$
essentially predicting the sum of all rewards throughout the whole training episode.
