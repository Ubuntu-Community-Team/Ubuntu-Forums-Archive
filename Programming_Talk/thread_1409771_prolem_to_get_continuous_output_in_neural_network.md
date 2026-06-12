---
title: "prolem to get continuous output in neural network"
date: 2010-02-18
forum: Programming Talk
---

### Post by tokime on 2010-02-18
hi.. 
i have to predict an equation using neural network in matlab. i use continuous input and need to produce continuous output. But, i have problems here. how can i have continuous output because the neural network that i have learned before just produce discrete value output such as 0 or 1 only..i don't know what code i have to write.. 
please help me..what should i do to have continuous output?? please kindly email me [email]tokime_ee@yahoo.com[/email] asap..tq

---

### Post by Zugzwang on 2010-02-18
Check the description of the MATLAB toolbox you use for neural networks that it actually supports non-binary output. Then check if you used the correct functions for learning the network. Inspect the weight vectors you obtain from learning if you see anything special. Then compute an example using this weigths by hand from which you think that it should result in a value other than 0 and 1. Does it fit? Finally, note that MATLAB has variable types. Check that your input values are all of a type that allow fractional values.

Note that it is not common to ask for a reply by e-mail and somewhat defeats the purpose of a forum. So if you want to receive answers by e-mail, you should setup your forum account such that you get notified by e-mail on new messages for threads you wrote to.

---

