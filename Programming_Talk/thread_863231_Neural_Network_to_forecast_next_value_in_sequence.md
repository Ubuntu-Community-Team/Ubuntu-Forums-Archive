---
title: "Neural Network to forecast next value in sequence"
date: 2008-07-18
forum: Programming Talk
---

### Post by KarT on 2008-07-18
Hi there!

Maybe this is not "a simple question" like the section describes it, but I've searched a lot and still have nothing useful to start with.

I worked with Neural Networks in fingerprint recognition a while ago, and now I wanted to implement a simple network in C (or C++, or Java, or anything else, as long as someone helps me :)) that guesses the next value in a sequence.

For example:

1 2 3 4 5 6 7 8

The network would tell me that the next value would probably be 9. Of course, we're talking of a more complex sequences than this one.

The implementation and philosophy behind this forecasting thing is very different from the one behind fingerprint recognition, and all I can find on the web is paid software, but I want to implement this myself.

Any help?

Thanks.

---

### Post by Wybiral on 2008-07-18
How many previous values does it take to predict the next one? Figure that out, then you can use those as your input nodes. But, if there's nothing to generalize about the sequence, you'll just be using the network as a hashtable, so make sure you need a network first.

---

### Post by KarT on 2008-07-18
The issue is that the NN I used for fingerprint recognition had X inputs and 3 outputs. It just told me what were the odds of a fingerprint belonging to one of the 3 individuals. Now I don't want an odd, I want a number...

---

