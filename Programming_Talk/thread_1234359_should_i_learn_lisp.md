---
title: "should i learn lisp?"
date: 2009-08-07
forum: Programming Talk
---

### Post by jero3n on 2009-08-07
I was thinking to start messing with semantic networks in my free time ( [http://en.wikipedia.org/wiki/Semantic_network](http://en.wikipedia.org/wiki/Semantic_network) or [http://pi7.fernuni-hagen.de/forschung/multinet/multinet_en.html](http://pi7.fernuni-hagen.de/forschung/multinet/multinet_en.html) )  

I had some ideas and I was thinking to write something in C and a relational database as a back-end. However I know that Lisp is good at lists and such projects, but I dont know how to write a hello world program in it.

Is it worth learning a new language for something like this? Would it be much better from a C implementation?

Thanks

---

### Post by CptPicard on 2009-08-07
The answer would be two-fold.

I do not necessarily believe that you should learn a whole new language just simply for a new kind of project -- most importantly not Lisp for the reasons you are so far able to state.

However, yes, you should most definitely learn Lisp. It makes you a better programmer in all your future projects.

---

### Post by JordyD on 2009-08-07
By the way:
```
(format t "Hello, world!")
```

---

### Post by Can+~ on 2009-08-07
+1 on learning LISP (maybe with Scheme) for the functional paradigm goodness.

As for your problem goes, I would definitely stay away from C(++) for this one. Not because of particular hate (I like C, C++ not so much) or anything, but this problem would be solved with ease having more advanced data structures.

I would normally say go with python, but in this case, go with Java, C#, Perl, PHP, anything which provides high level tools (Python being included), as I feel you'll be using them a lot (Semantic analysis is a high-level subject) and using low level would hamper your work more than help.

Even if you go with C for speed, you're still being dragged down if you're using a database to pull information from the hard disk (access time in milliseconds) (Yes, I know it can be cached).

---

### Post by CptPicard on 2009-08-07
Regarding the database... Java has an awesome OR-Mapper in Hibernate. It really abstracts your object-model totally, although it has a bit of a learning curve...

---

### Post by soltanis on 2009-08-07
Actually, I would say go with python, or perhaps go with perl. You want something that gives you the power to express complex ideas in a few lines (perl is *really* good for this -- provided you spend the time to learn it).

Lisp actually doesn't make stuff easier to express -- it actually makes the form in which you express it much more intuitive.

If you want to become a better programmer, I suggest learning a Lisp, like the others here have, but if you aim to do just one program (or set of programs) you might consider going with the language you know best.
If this happens to be C with databases, more power to you, but there is probably some better way.

---

### Post by jero3n on 2009-08-08
> **Can+~ said:**
> I would normally say go with python, but in this case, go with Java, C#, Perl, PHP, anything which provides high level tools (Python being included)
I guess you are right. It seems C# is the winner. System.Collections.Generic should provide convenient tools this purpose. At least for a start there is no need to rediscover the wheel. Regarding database, I now I could use something like an OR Mapper, but at a first glance it seems easier to convert from and to a relational model.

However I am interested to give Lisp a try, if it would made me a better programmer if you say so :) 

I will google for a beginners tutorial, please provide a tutorial link if you know anything good.

---

### Post by nvteighen on 2009-08-08
Hmm... I think Common Lisp would be really useful for this, actually. As a semantic network essentially is the relationship between meanings in a language, you could take those meanings as objects and the relationships as generic methods of all those objects... as "lives in" can be applied to any living being, for example... That seems a job for CLOS (Common Lisp Object System).

But, another argument for using Lisp is clearly the relative triviality of modelling trees and other graphs in it. Moreover, my intuition tells me the semantic network could be programmed in a pure-functional way (at least the representation part of it... if you plan to load stuff from a file or other stuff to "prepare" things, those may not be pure-functional).

Arguments against Lisp... well, if you want to some kind of text-analysis, like trying to deduce the semantic network from a text file, well, you better have the text-analysis portion written in Perl (which IMO is still unbeatable at this task). And if you plan to use a database, which seems inevitable if you plan to do this in a large scale, I honestly don't know what bindings are available for Common Lisp...

This project seems to be a case for a multilingual project, in my very honest opinion.

Now, to the other issue. Learning Lisp is a great experience. In my opinion and experience, the best is to start with one of the so-called "Lisp-1". These are the Lisp dialects that try to get as closest as possible to the first and original Lisp by McCarthy, which was mainly pure-functional and really really simple (it was thought as an algorithmic language). The most widespread of the "Lisp-1" family is Scheme; you'll find plenty of resources for it.

The sad thing is that Scheme isn't that practical to use as Common Lisp. I recommend you to learn Common Lisp too, after Scheme... but be prepared for a bit more complex version of Lisp. The fundamentals will be exactly the same (Scheme is better in teaching them than CL), but the stuff built on top those fundamentals will be different.

Good luck! :)

---

### Post by jero3n on 2009-08-08
> **nvteighen said:**
> Hmm... I think Common Lisp would be really useful for this, actually. As a semantic network essentially is the relationship between meanings in a language, you could take those meanings as objects and the relationships as generic methods of all those objects... as "lives in" can be applied to any living being, for example... That seems a job for CLOS (Common Lisp Object System).

Well my intention was not to write a semantic network and such graphs in lisp but a "framework" to construct semantic networks. Then my idea is to develop a simple language which instructs that "framework" things like
Create entity "Socrates"
Create entity "mortal"
Connect Socrates to mortal with an "is" relationship

And then to develop something like a compiler which turns a natural language to that formal language with hints and driven by the semantic framework. And then some experiments.. I don't know yet.. It is summer and it seems I have lot of free time :D

> This project seems to be a case for a multilingual project, in my very honest opinion.

I think so, too.. I'll try to keep it as simple as possible. Up to know I imagine C# and SQL

> **nvteighen said:**
> Good luck! :)
Thanks!

---

### Post by cmnorton on 2011-08-23
> **jero3n said:**
> I was thinking to start messing with semantic networks in my free time ( [http://en.wikipedia.org/wiki/Semantic_network](http://en.wikipedia.org/wiki/Semantic_network) or [http://pi7.fernuni-hagen.de/forschung/multinet/multinet_en.html](http://pi7.fernuni-hagen.de/forschung/multinet/multinet_en.html) )  

I had some ideas and I was thinking to write something in C and a relational database as a back-end. However I know that Lisp is good at lists and such projects, but I dont know how to write a hello world program in it.

Is it worth learning a new language for something like this? Would it be much better from a C implementation?

Thanks

I was taught many years ago, that you go solve the problem or at least delineate the steps you would use to solve the problem and then find a programming language that is best suited to help you do that. 

There are several languages that have functional programming properties, Scala, Python, and Clojure come to mind. I don't recommend that you go out learn a new language and implement in it.

---

### Post by cgroza on 2011-08-23
Learning it could allow you to write extensions for powerful editors like Emacs. 
The only task I employed a lisp-like language is in Emacs to make my editing experience more pleasant.

---

### Post by cmnorton on 2011-11-28
> **cmnorton said:**
> I was taught many years ago, that you go solve the problem or at least delineate the steps you would use to solve the problem and then find a programming language that is best suited to help you do that. 

There are several languages that have functional programming properties, Scala, Python, and Clojure come to mind. I don't recommend that you go out learn a new language and implement in it.

After this response in June, I started learning Clojure and implemented a small applet in it for property address verification. If you want to learn a Lisp variant, I suggest Clojure or CL.

---

