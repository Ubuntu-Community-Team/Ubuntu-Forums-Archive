---
title: "Kelly strategy"
date: 2010-11-13
forum: Programming Talk
---

### Post by pitiburi on 2010-11-13
Sorry to bother you guys, but i was interested in the subject so i guess there are very, very insightful persons here to ask them about it... 
So suppose you did an amazing job developing some software/toolkit for betting analysis. My question is, how did you get yourself into the ins  and outs of kelly strategy to make that software of yours?
I mean,  someone wanting to get into that area, what should she read (other than  the Kelly paper and the Thorp book/s)? From a programming interest  perspective i mean.
Thanks, and sorry for not doing this through personal messages, but because of my lack of posting, i am not allowed to use that feature.

---

### Post by CptPicard on 2010-11-14
I've actually been involved in exactly this kind of stuff; I collaborated with a professional sports betting guy as his right-hand technical man, writing his tools.

The Kelly criterion is not really rocket science; what I managed to do was to extend it beyond the basic case though so we were able to  analyze more complex games. Then it was just coming up with efficient computation strategies to actually make it feasible to get the numbers in a tolerable time.

There are a couple of things to remember though 

[LIST=1]
[*]There is no crystal ball, don't assume you know more than you do
[*]In a lot of games, the distribution you'll be playing will be surprisingly "easy"; for example in soccer most small-scoring results are always grossly overplayed
[*]The strength of Kelly betting comes from distributing lots of money over a large number of base cases where you have an edge. Thus you're placing lots of tiny bets.
[/LIST]

Most of the coding really was just making sure that the entire process from analysis to placing the bets and paying out the winnings to clients happened correctly.

---

### Post by pitiburi on 2010-11-15
Thanks, I know you've been working on this. I wanted **you** to answer, but I had to use the forum because I am not allowed yet to write PM.
Thanks again, I am trying to use that on some learning simulation for a neuroscience project of mine. The whole idea is to model some actual neural circuits as one/some betting agents over world and self behavior. Still deciding what to use, but Erlang looks promising, with processes in C for optimization.

If you have some ideas, I am always listening.

---

### Post by CptPicard on 2010-11-15
Hmm, I suppose you're trying to train a neural network to detect an edge that you could then exploit to the max by Kelly betting. It is interesting that what we are actually doing is no to try to predict all that much, but to really throw a lot of money, repeatedly, at a game that is, on the whole and in total, profitable in the long term.

You would be surprised if you just knew how little actual predictive ability is required to get enough of an edge that you can then make Kelly-style use of, as long as you've got the discipline and the bankroll...

---

