---
title: "Help with python HMMs"
date: 2016-07-24
forum: Programming Talk
---

### Post by DBQ on 2016-07-24
Hi Everybody.

So, I would like to learn how to use Hidden Markov Models (HMMs) in Python. It seems that [hmmlearn]("http://hmmlearn.readthedocs.io/en/latest/index.html") is among the few functional libraries out there.

I tried implementing a basic example found [here]("http://sujitpal.blogspot.com/2013/03/the-wikipedia-bob-alice-hmm-example.html").  It looks like this example has been implemented using the sklearn package that is now deprecated and is succeeded by hmmlearn.

Below is my attempt to port it to hmmlearn.

```

from __future__ import division
import numpy as np
from hmmlearn import hmm 

states = ["Rainy", "Sunny"]
n_states = len(states)

observations = ["walk", "shop", "clean"]
n_observations = len(observations)

start_probability = np.array([0.6, 0.4])

transition_probability = np.array([
  [0.7, 0.3],
  [0.4, 0.6]
])

emission_probability = np.array([
  [0.1, 0.4, 0.5],
  [0.6, 0.3, 0.1]
])

model = hmm.MultinomialHMM(n_components=n_states)
model.startprob_ = start_probability
model.transmat_ =  transition_probability
model.emissionprob_ =  emission_probability

# predict a sequence of hidden states based on visible states
bob_says = [0, 2, 1, 1, 2, 0]
logprob, alice_hears = model.decode(bob_says, algorithm="viterbi")
print "Bob says:", ", ".join(map(lambda x: observations[x], bob_says))
print "Alice hears:", ", ".join(map(lambda x: states[x], alice_hears))

```

The problem is that when I run it, I get the following error

```

usr/lib64/python2.7/site-packages/sklearn/utils/validation.py:386: DeprecationWarning: Passing 1d arrays as data is deprecated in 0.17 and willraise ValueError in 0.19. Reshape your data either using X.reshape(-1, 1) if your data has a single feature or X.reshape(1, -1) if it contains a single sample.
  DeprecationWarning)
Traceback (most recent call last):
  File "hmmbobalice.py", line 30, in <module>
    logprob, alice_hears = model.decode(bob_says, algorithm="viterbi")
  File "/usr/lib64/python2.7/site-packages/hmmlearn/base.py", line 313, in decode
    state_sequence[i:j] = state_sequenceij
ValueError: could not broadcast input array from shape (6) into shape (1)


```


It would be great if somebody could shed some light on this (or suggest a better library for Python!)

Thank you!

---

