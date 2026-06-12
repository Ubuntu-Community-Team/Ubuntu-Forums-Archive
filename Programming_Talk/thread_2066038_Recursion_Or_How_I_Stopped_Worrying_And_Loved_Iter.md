---
title: "Recursion: Or How I Stopped Worrying And Loved Iteration"
date: 2012-10-03
forum: Programming Talk
---

### Post by Majorix on 2012-10-03
I am a CS student.

It should be clear that I should have at least introductory level understanding of C.

I love C. I love iterative approach. I am creative and can find algorithms fellow students would have trouble with.

However... And it starts now... I, for the life of me, can't figure out recursion!

I have researched a bit, and found out that languages like Python or Ruby (my fav) have awkward recursion implementations and work terribly slow working out recursion. This made me think recursion is dying.

My question is, do professionals use recursion? If yes, please, please, tell me how/where I can learn it.

I need help.

---

### Post by satsujinka on 2012-10-03
Well, I'll point you to where I learned recursion: [Structure and Interpretation of Computer Programs]("http://mitpress.mit.edu/sicp/")

Recursion isn't going away anytime soon. Recursion is (once you understand it) a much more concise and elegant solution to most problems. It is, however, mostly an expressive entity as any *proper* language will optimize recursion into an iteration.

---

### Post by Stovey on 2012-10-03
Hi.  If it makes you feel any better, I too am having difficulty understanding recursion.  But here are a couple "snippets" out of my text that add clarity for me:

*- There are some similarities between iteration (looping) and recursion.  In fact, recursive functions are a generalization of loops.  Anything that can be done with a loop can also be done by a simple kind of recursive function.*

For me, I think of recursion as a loop with the dynamic variable being passed to the function.

- *Recursion is closely related to mathematical induction, and it requires practice before it becomes comfortable.  As long as you follow the rules and make sure that every recursive chain of calls eventually reaches a base case, your algorithms **will** work.  You just have to trust and let go of the grungy details.*

I hope I am not violating any rules by posting these excerpts from Zelle's ["Python Programming: An Introduction to Computer Science"]("http://www.amazon.com/Python-Programming-Introduction-Computer-Science/dp/1590282418/ref=sr_1_2?ie=UTF8&qid=1349289602&sr=8-2&keywords=python+programming+an+introduction+to+computer+science").

---

### Post by satsujinka on 2012-10-03
I'm not sure that having "faith" is the correct way of going about learning recursion.

It's probably better to start off with a few small examples and use substitution to figure out what's going on, usually operations on lists are done because they're generally of the correct form. This in turn makes functional languages a nice choice for learning recursion because lists are usually the collection primitive in such languages.

A trivial example: find the length of a list.
We'll call our function *length*. If we give it the list [1,2,3] it should return 3.
A quick definition for *length*
```
length list = 
  if list == []                    --is list equal to an empty list
    then 0                         --an empty list's length is 0
    else 1 + length (tail list)    --tail removes the first element of a list
```And the expansion of *length* [1,2,3]:
```
(length [1,2,3])
1 + (length [2,3])
1 + 1 + (length [3])
1 + 1 + 1 + (length [])
1 + 1 + 1 + 0
1 + 1 + 1
1 + 2
3

```Here's a couple example problems for you to start with:

[LIST]
[*]determine if an element is in a list (if you're using a static language, use integers for simplicity)
[*]reverse a list
[/LIST]

---

### Post by pcman312 on 2012-10-03
Speaking as someone who has been in the "real world" for some time now, I can say with confidence that recursion is something that is useful in certain instances. However in most of the coding that I have done, it hasn't been necessary nor more useful than doing an iterative approach. Naturally recursive problems (such as traversing a linked list that doesn't have a random access ability, traversing a directory tree), recursion is extremely useful and something that I have used in the "real world".

One thing that a professor told me once is that every problem that can be solved using a regular loop can be refactored to use recursion, and vice versa. They are merely different ways to solve problems with their own advantages and disadvantages. Each language does it in a different way. For instance, from my limited experience with Ruby, it tends to be a fairly slow language, so it doesn't surprise me that you'd find recursion in it to be slow. As an example, recursion in Java is quite fast. I've used it to traverse large directory trees without any sort of slow down. The main problem is eventually your stack will grow to be too big for the JVM to handle (and that is probably true of many languages, so you'd have to do some optimization if you were to ever run into that problem).

---

### Post by satsujinka on 2012-10-03
> **pcman312 said:**
> Speaking as someone who has been in the "real world" for some time now, I can say with confidence that recursion is something that is useful in certain instances. However in most of the coding that I have done, it hasn't been necessary nor more useful than doing an iterative approach. Naturally recursive problems (such as traversing a linked list that doesn't have a random access ability, traversing a directory tree), recursion is extremely useful and something that I have used in the "real world".

One thing that a professor told me once is that every problem that can be solved using a regular loop can be refactored to use recursion, and vice versa. They are merely different ways to solve problems with their own advantages and disadvantages. Each language does it in a different way. For instance, from my limited experience with Ruby, it tends to be a fairly slow language, so it doesn't surprise me that you'd find recursion in it to be slow. As an example, recursion in Java is quite fast. I've used it to traverse large directory trees without any sort of slow down. The main problem is eventually your stack will grow to be too big for the JVM to handle (and that is probably true of many languages, so you'd have to do some optimization if you were to ever run into that problem).
Arguably, the language should optimize it for you. I know a lot of languages don't guarantee it (C and Java don't,) but many compilers do it anyways (since it's a fairly easy optimization to make.)

---

### Post by trent.josephsen on 2012-10-03
> **satsujinka said:**
> Arguably, the language should optimize it for you. I know a lot of languages don't guarantee it (C and Java don't,) but many compilers do it anyways (since it's a fairly easy optimization to make.)
That's a bit of an overgeneralization, don't you think? Tail recursion may be pretty easy to optimize, but most other cases aren't so simple. (And, obviously, when a function calls itself more than once per call, you'll need more than a trivial optimization to limit the stack growth.)

There are only 3 reasons I've ever used recursion:

1) because I was told to;
2) because the problem itself is necessarily recursive -- traversing a directory tree comes to mind;
3) because the recursive solution is easier to understand than an iterative one.

In case (3) it may be to your benefit to consider rewriting the algorithm iteratively for performance reasons, but remember not to optimize prematurely.

---

### Post by satsujinka on 2012-10-03
@trent
It's not an overgeneralization. I never said convert all recursion to iteration. I said the language should take care of optimizing recursion for you. This almost entirely means tail calls.

I'm more or less the opposite of you in terms of usage. I almost always use recursion and only don't when the language doesn't do "the right thing".

---

### Post by rai4shu2 on 2012-10-03
It seems to me like recursion is mostly for math or for sorting, and those are nearly all optimized in C, nowadays (math.factorial or list.sort in Python spring to mind).

---

