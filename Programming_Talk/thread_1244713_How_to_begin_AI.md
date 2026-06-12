---
title: "How to begin AI?"
date: 2009-08-19
forum: Programming Talk
---

### Post by jacensolo on 2009-08-19
Hi, I want to make some type of learning ai for a school project. I'm not really sure what it will do, maybe learn paths? But I don't want it to just be pathfinding. 

I've been googling for a while but can't find any information on how to start.

---

### Post by soltanis on 2009-08-19
AI is a highly theoretical subject. If you're looking to get into it practically, you have a lot of options to start off with:

Artificial Neural Networks: [http://en.wikipedia.org/wiki/Artificial_Neural_Network](http://en.wikipedia.org/wiki/Artificial_Neural_Network) - programs that simulate the connections of neurons in the brain, including algorithms for making and breaking new connections, in an attempt to create networks that are capable of learning and solving problems.

Cognitive-based approach: [http://en.wikipedia.org/wiki/Good_old_fashioned_artificial_intelligence](http://en.wikipedia.org/wiki/Good_old_fashioned_artificial_intelligence) - attempts to simulate intellect by modeling the high-level behavior of cognitive architectures, like pattern recognition and matching, categorization of objects, recognition of relationships between objects, etc. by encoding them as symbols in computer memory. Use of Lisp highly recommended if you take this approach, since the relationship between data architectures, symbols, and program structure is all one of the same (i.e. lists) here, so getting down to the nitty-gritty is much easier.

Fuzzy-logic based: [http://en.wikipedia.org/wiki/Fuzzy_logic](http://en.wikipedia.org/wiki/Fuzzy_logic) - use of more statistical methods for determining truth and falsity that finds a lot of application in AI-type systems.

You have a lot of topics to tackle, and I would really suggest you narrow down the field before you consider handing in your project proposal. What you really want to do is find a small, well-defined issue that you can technically understand and formulate a meaningful and well-defined solution to and then express it in code. That's really the key to not getting in over your head.

I can offer you some suggestions as to what specific problem you want to look into, although they won't be easy -- depending on how much time you have to do this, and just how committed to it you are, you might find them too difficult. I took a class in Cognitive Science so naturally, we had to do a lot of this kind of b.s. -- so I have some stuff to offer. I've never really delved into AI myself, though, so my practical experience is limited.

---

### Post by Lux Perpetua on 2009-08-19
Russell & Norvig wrote the standard textbook (*Artificial Intelligence: A Modern Approach*), which your local library might have and Amazon/Barnes & Noble almost definitely have. I think that would be a good place to start.

---

### Post by jacensolo on 2009-08-19
> **soltanis said:**
> AI is a highly theoretical subject. If you're looking to get into it practically, you have a lot of options to start off with:

Artificial Neural Networks: [http://en.wikipedia.org/wiki/Artificial_Neural_Network](http://en.wikipedia.org/wiki/Artificial_Neural_Network) - programs that simulate the connections of neurons in the brain, including algorithms for making and breaking new connections, in an attempt to create networks that are capable of learning and solving problems.

Cognitive-based approach: [http://en.wikipedia.org/wiki/Good_old_fashioned_artificial_intelligence](http://en.wikipedia.org/wiki/Good_old_fashioned_artificial_intelligence) - attempts to simulate intellect by modeling the high-level behavior of cognitive architectures, like pattern recognition and matching, categorization of objects, recognition of relationships between objects, etc. by encoding them as symbols in computer memory. Use of Lisp highly recommended if you take this approach, since the relationship between data architectures, symbols, and program structure is all one of the same (i.e. lists) here, so getting down to the nitty-gritty is much easier.

Fuzzy-logic based: [http://en.wikipedia.org/wiki/Fuzzy_logic](http://en.wikipedia.org/wiki/Fuzzy_logic) - use of more statistical methods for determining truth and falsity that finds a lot of application in AI-type systems.

You have a lot of topics to tackle, and I would really suggest you narrow down the field before you consider handing in your project proposal. What you really want to do is find a small, well-defined issue that you can technically understand and formulate a meaningful and well-defined solution to and then express it in code. That's really the key to not getting in over your head.

I can offer you some suggestions as to what specific problem you want to look into, although they won't be easy -- depending on how much time you have to do this, and just how committed to it you are, you might find them too difficult. I took a class in Cognitive Science so naturally, we had to do a lot of this kind of b.s. -- so I have some stuff to offer. I've never really delved into AI myself, though, so my practical experience is limited.

Thanks for the info. Basically, the class I'm taking allows us to create our own project and do it, so I have about 4 hours a week for 3 months of garunteed time + outside time. I'll read up on some of that. The neural network sounds the most interesting, but way over my head. 

@Lux

I'll look into the book.

---

### Post by mess110 on 2009-08-20
> **jacensolo said:**
> Thanks for the info. Basically, the class I'm taking allows us to create our own project and do it, so I have about 4 hours a week for 3 months of garunteed time + outside time. I'll read up on some of that. The neural network sounds the most interesting, but way over my head. 

@Lux

I'll look into the book.

Neural Networks ain't that bad as you think. Try starting with something simple. If you know Java try this:
```
http://www.heatonresearch.com/online/introduction-neural-networks-java-edition-2
```

A very basic neural network is the Hopfield neural network. It ain't complex but once you truly understand it, you will understand how neural networks work.

I think there is a C++ tutorial as well. Didn't read anything about the other 2 suggestions but they both seem pretty interesting. Especially the cognitive one.

Also try to implement a chatterbot. That is always pretty fun and it can get quite complex.

---

### Post by lisati on 2009-08-20
How about a program which learns a strategy for a simple game as it plays? One similar to something I've done in the past is described here: 
[http://www.atarimagazines.com/v3n1/matchboxttt.html](http://www.atarimagazines.com/v3n1/matchboxttt.html) (BASIC)
[http://www.delphiforfun.org/Programs/tic_tac_toc_machine.htm](http://www.delphiforfun.org/Programs/tic_tac_toc_machine.htm) (pascal)
[http://www.codeproject.com/KB/cpp/ccross.aspx](http://www.codeproject.com/KB/cpp/ccross.aspx)  (c++)

---

### Post by CptPicard on 2009-08-20
I have a feeling that machine learning may be a bit too complex a subject and perhaps something like searching algorithms (game trees and so on) might be a more manageable field of AI.

If you do want to investigate learning though, neural networks are nice... but I would suggest starting with the simple perceptron, trying to understand it, and then perhaps move over to backpropagation-trained nets.

---

### Post by bender1234 on 2009-08-20
> **jacensolo said:**
> Hi, I want to make some type of learning ai for a school project. I'm not really sure what it will do, maybe learn paths? But I don't want it to just be pathfinding. 

I've been googling for a while but can't find any information on how to start.

Hi I'm not sure what you're doing making a game, robot or just want to mess about, but yes I would start with pathfinding/shortest path algoritms. I would advice you to have a look at the basic algs from comp. eng, and I guess those c.s guys use them to :)

Have a look at graphs weighted and not, and the different and the various ways to traverse them etc, what you are interested in is the shortestpath problem.

a link if you don't got any books
[http://en.wikipedia.org/wiki/Shortest_path](http://en.wikipedia.org/wiki/Shortest_path)

you can consider forinstance a room/house a grid of connected nodes, which forms a graph, where wheights are levage(mm english, floor that angles up or downwards) etc.

Know there are better algoritms for game stuff but I hope this explains some basics :)

cheers
bender

---

### Post by Zugzwang on 2009-08-21
> **bender1234 said:**
> Hi I'm not sure what you're doing making a game, robot or just want to mess about, but yes I would start with pathfinding/shortest path algoritms. I would advice you to have a look at the basic algs from comp. eng, and I guess those c.s guys use them to :)


What does this has to do with a "learning ai", the OP asked for? Note that we are not talking about computer games.

---

### Post by UbuKunubi on 2009-08-21
> **jacensolo said:**
> Hi, I want to make some type of learning ai for a school project. I'm not really sure what it will do, maybe learn paths? But I don't want it to just be pathfinding. 

I've been googling for a while but can't find any information on how to start.

Hello!

I was wondering if you have seen this:
[http://cogprints.org/3705/](http://cogprints.org/3705/)

and if so is it of any use?

On the topic of A.I. simply dont be afraid to think outside the box - while neural networks, chatbots, path finders are both established and very useful in the real world, its the combination of ALL these elements (plus ingredient 'X') that sometimes seems to make the occasional program seem smart - for example the expert systems that are used by the emergency services, as well in many other roles.

During an old project of my own I had an automated search-and-register function that would ask questions on my behalf in various forums (pre-captcha!), the lesson I learnt the hard way was I had given little consideration about when the program should give up asking a question.

I have been wondering what would happen if sufficient computing power where deployed to run large quantities of all the various AI elements, and then linked to monitor the input from a M.R.I. scanner? Kind of like a brute-force solution to the actual problem of 'how'.

Just my 5 pence worth!

All the best,
Ubu

---

