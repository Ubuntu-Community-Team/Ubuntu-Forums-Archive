---
title: "tcl for underwater wireless sensornetwork"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by eng dina on 2013-03-09
i need to know how to write a tcl for 50 nodes to build an underwater wireless sensor network using VBF routing protocol. and how to write the scenario fo this network

---

### Post by tgalati4 on 2013-03-09
I'm not sure why this is in absolute beginner, but normally when tackling a complex problem, you need to do a couple of things:

Write down the Explicit Requirements:  What is the system supposed to do?  How do you know it is working?

Write down the Implicit Requirements:  What additional things have to work to meet the Explicit Requirements?  What things need to happen, but are not primary to the function of the system?

Now take the Explicit and Implicit requirements and write specifications for each:  What characteristics must each piece of hardware and software possess to meet the requirements?

Now take the specifications and make a block diagram showing the interactions of the specifications--how are the pieces of the problem connected?  Some call this demodularization--taking a big problem and breaking it down into a bunch of smaller problems.

Once you have shared the above, the coding for the individual pieces becomes easier to describe.

Many times, accurately describing the problem is the first step to solving it.

---

