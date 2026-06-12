---
title: "Taking an artificial intelligence class"
date: 2006-05-12
forum: Programming Talk
---

### Post by otake-tux on 2006-05-12
We will be utilising 2 programming languages, prolog and LISP.  Can anyone give me their impressions on on these languages and point to good internet tutorial.  I have already found tutorials for both but if there is one ou guys recomend, I would definetly prefer that one. :)

---

### Post by daneel_olivaw on 2006-05-12
Definitely a must to have an open mind in programming. I don't know LISP, but I know Prolog; it gives you really a big clue of what declarative programming is. I like math so I like such things... and with this language you learn even recursion much better (at least it was like that for me).

As for online tutorials I remember I took one like [this]("http://www.csupomona.edu/~jrfisher/www/prolog_tutorial/pt_framer.html") (if not that), but this was before doing the artificial intelligence exam; when I (a month ago) did the exam I studied on a book here and it was obviously much better.. so I suggest you read a book your teacher tell you :P

---

### Post by rplantz on 2006-05-12
[QUOTE=daneel_olivaw].. so I suggest you read a book your teacher tell you :P[/QUOTE]

From a teacher's perspective, this is good advice. In my 21 years as a cs prof. (now retired), I learned a lot about textbooks.

1. Your teacher has probably picked a book that matches his/her teaching style after reviewing many books on the subject.

2. My students often told me that they found a better book. When I first started teaching, I would check out the "better" book. I finally realized that reading a second book on any subject will almost always be easier to understand.

3. My students often complained that they had to read the book several times. Uh, me too! Technical books cannot be read like a novel. I read several books, several times each, before I got a really good understanding of the subject.

Finally, asking your teacher is generally a good way to establish a rapport with him/her. We teachers enjoy working with students who actually want to learn the subject -- as opposed to simply getting a degree.

---

### Post by otake-tux on 2006-05-12
Problem is, the book my prof chose does not teach prolog or lisp!

---

### Post by daneel_olivaw on 2006-05-13
Well that's not good.. :P my book is in italian and I don't think it has been translated.. try maybe ask your teacher to suggest you one

---

### Post by lnostdal on 2006-05-13
[http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/) .. is a very good book

oh, and there is an example of Prolog implemented in Lisp in the book "On Lisp" available here: [http://www.paulgraham.com/onlisp.html](http://www.paulgraham.com/onlisp.html)

Common Lisp is truly one of the greatest things i've come accross when it comes to computers .. i'm never looking back :)

---

### Post by otake-tux on 2006-05-14
thank you, that book seems pretty useful!

btw- I found a nice prolog tutorial!  its [here]("http://ktiml.mff.cuni.cz/~bartak/prolog/contents.html"). I recomend using swi-prolog. GNU prolog seems flaky to me. :-k

---

### Post by [h2o] on 2006-05-15
Ah, Lisp was the first language thrown at us in the university (Comp. Engineering) and all students quickly divided into two groups:  those who loved it, and those who hate it.
I like Lisp. It is consistent and easy to work with once you get used to the syntax ('(' and ')' everywhere!). It's a (almost strictly) functional programming language, which might be confusing if your mind sternly believes that all programming languages should behave like C :P
Conclusion: Lips is nice and from what I've heard it is very common for AI progrraming since you can use Lisp code to generate and evaluate new Lisp-code. Confusing, but neat.
Good luck on your course, I will probably be reading something similar in a year or two. :mrgreen:

---

### Post by Resurrection on 2006-05-15
I fall into the "hate Lisp" crowd from my CS degree.  In my opinion Lisp has a very large "hump".  The hump is essentially an understanding Lisp beyond just the syntax, i.e. understanding what you can really do with the language and how to apply it to a real-world situation.  I never got over this hump.  Therefore I always just struggled with Lisp.  Given more time, I think I could have learned to like it, but it was only one semester, and my prof ruined it for me.  He was one of those guys who teaches you concepts "A" and "B" and then expects you to just automatically make the jump to concept "Q", by figuring out all the concepts (C-P) on your own.  Very painful for me.   You can't learn Lisp in this manner, in my opinion.  It isn't very intuitive especially if you already have a solid background in C++, Java, VB and other OOP languages.

---

### Post by pharcyde on 2006-05-15
LISP is very powerful for doing data transformations (i.e. LISP -> List Processing) From what I can tell is a lot of people would love LISP if they weren't brought up on ALGOL type languages.  I too was raised on C/C++ but have seen many instances where LISP is far superior for code management and maintainability.  I am not well versed in LISP but am starting to learn more about it recently.

---

### Post by daneel_olivaw on 2006-05-16
Well i never studied nor seen a single line of LISP, but i suppose and i heard that Prolog it's an evolution of LIPS. From a Java-background point of view, Prolog is really complementary as a set of programming concepts and abilities in respect of Java and OOP, so I guess you (Resurrection) can enjoy learning it, but from a good book, which gives you the right prospective and background.

But as I said it's quite a math-context so it even depends on how much you like math :P it's not anywway necessary to dive into that to know Prolog well.. so you can choose the level of immersion you prefer.

Just to think of "what you can do" with Prolog, think of all the cases you need a rule-based engine working under your software layer and giving it rules of behaviour changing depending on the situation: Prolog gives you a great tool for doing it.. you can do what you do with, for example, the policy and strategy patterns in Java, much easily and in a much more readable and changable way.

---

