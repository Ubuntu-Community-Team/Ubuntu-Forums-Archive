---
title: "First time programmer"
date: 2009-11-11
forum: Programming Talk
---

### Post by fatum on 2009-11-11
My entire life I have been the computer guy to my family and friends. I finally have started working on programming. I have started with Python, I know everyone has their own opinion on what to start on, for the main reason on MIT open course for programming is using it. I am watching the classes and taking many notes, looking at all the handout for the classes and doing research on my own. The way the course is set out a lot of research on my own is required in order to understand fully. 
I just started this week and I understand that it is going to take time to fully understand how to program. I am wondering how long it took for you guys with your first language before you didn't feel like an idiot and get frustrated?
I wrote the code for the first problem set that they give thinking it was a good way to get the solutions needed. Took a look at their code and it is more than half the code lines and using options that I hadn't heard of or read about to this point. Wish they would do one of these courses where you could send in your code and see what they would have graded it. 
Any suggestions are welcome. And thank you for reading my post.

---

### Post by froggyswamp on 2009-11-11
> 
I am wondering how long it took for you guys with your first language before you didn't feel like an idiot and get frustrated?

Learning only implies doing less stuff the wrong way, but "less" never means none, unless you'll always program in one small area.
But then again, "frustration" is too subjective to give an objective answer on this issue.

---

### Post by shadylookin on 2009-11-11
Unless you stop trying to solve new problems you'll be left frustrated at times. 

Though at a certain point you should stop having problems using the language. When I started learning java I don't think I really understood it for at least 6 months if not longer.

---

### Post by sam191 on 2009-11-11
I don't know about you, but I tried following that class too a while back and it was BORING! lol 

You should try to have more fun. You actually sound a lot like me when I first started. "MIT uses it so it must be good" and "getting frustrated quickly". You get frustrated because it doesn't click right away, but believe me it will soon. Just learn and have fun, let it marinate because concepts will start clicking soon enough. 

You have a good language, and I think the book they are using is good too. For me, I found it much more interesting to get a beginners Python book, and think of a project that I wanted to do. Then after completing the beginner book, work on the project and pick up stuff along the way. Trust me, doing homework gets boring really quickly :D And if it helps, I still feel like an idiot.. But I know a hell of a lot more than I did when I started. The feeling of incompetence is good, because that will drive you to keep learning. You should never feel like you know everything ;)

---

### Post by wmcbrine on 2009-11-12
Well, my first program looked something like this:

```
10 PRINT "HELLO! ";
20 GOTO 10
```

so it was pretty much instant gratification there. :) I didn't get frustrated until much later... That was one of the great advantages of 8-bit BASIC: instant gratification. Python kinda brings that back.

My recommendation is to start up the interactive interpreter and just play for a while.

```
while True:
    print 'Hello!',
```

---

### Post by A_Fiachra on 2009-11-12
I think I wrote my first Pascal programs in 1983 ... it was for a math class on non-Euclidean geometry -- I did a program that played Pong on a hyperbolic plane, it was fun.

The first career language I learned was C.  I had a book and a 486 and I lot of time because I had just dropped out of grad school.  It took a few weeks to solve a problem:

Given a stack of index cards numbered 1 through N, shuffle the deck by cutting k cards off the top (call this the cut) leaving N-k cards (call this the deck) then laying the bottom card of the cut down, lay the bottom card of the deck down and so on until you run out of cut or deck, then lay the remaining cards down.  You have a new deck (no longer numbered 1 to N).  For a given N and k how many times would you have to repeat this process to get the deck back in order?  Specifically, given N = 1001 and k = 100, how many "shuffles" will it take to get the cards back in order?

The task was to write a program in C that solved the problem in less than 1 second.

I spent weeks pounding my head to get it, but I got it.  In the process I learned most of what I needed to do to be efficient at C (not necessarily pretty) and got a job parsing RS-232 feeds of financial data.

I swear I was much smarter then.  Over time I've just gotten stupid.

* shrug *

---

### Post by fatum on 2009-11-12
Its very refreshing to hear that mostly everyone get frustrated with their first language. The frustration also gets me discouraged to continue and with no one to go to on the subject I have given up in the past (a couple years ago I tried C++.) Im going to go to my local library today with hopes that they have a python book. I want to get into programming for a couple very specific reasons and I know python is not necessarily the best language but my theory is once one is known a second and a third will be easier to learn. 
First I have to find my programming way of thought. Which is different and complete thought compared to regular day life, at least I think so.

---

### Post by ve4cib on 2009-11-12
I'm on my 11th language (give or take, and depending on your definition of "language") and I still get frustrated at times.  Every language has its own quirks and oddities that need to be worked around/worked with.

Likewise the same problems can have many different solutions.  Depending on the solution you start out with you may or may not run into unforeseen side-effects, bugs, or simply cases you never thought could even exist.  But dealing with those kinds of problems is ultimately the point of programming.  Getting flustered at times is just par for the course.

---

### Post by maximinus_uk on 2009-11-12
There are several stages to programming. The first stage is full of fail, where you are bad, and you know you are bad.

Then there is the wonderful second stage, where you start to realize that you can actually do it - this is the point where you understand the language.

Then the infamous third stage, where maybe you've mastered your first language and even learnt a few others. You also know a few libraries. You feel you could take on any coding challenge. Non-programmers praise your skills. Many (most?) programmers tend to reach this level and stay there.

You could maybe reach this level in a year or 2.

However, a real programmer will carry on, and start to read more and more. As they develop their skills they begin to doubt themselves: there is such a vast ocean of knowledge to learn.

Finally, the zen like expert level is obtained: these people will say that all of their code is rubbish. They are never happy. Can anything be written properly?

As a very simple example; when I was 22, programming in C and machine code, design patterns meant little to me, thus I never worried about it too much. Also, since I'd never heard of Lisp style macro's, I was never struck by the thought that a particular segment of code could be better written with one.

Nowadays, doubt fills my code, whereas in the past I was filled with an optimistic ego.

But one solid piece of advice I learned on the way( and apologies for paraphrasing Arthur C. Clarke):

If a competent programmer tells you that he has to use C++ for a job, then he may be right. If he tells you that C++ is the best tool for the job, he is almost certainly wrong ;)

---

### Post by Can+~ on 2009-11-12
The more you learn, the more you realize how much you don't know.

---

### Post by rplantz on 2009-11-12
> **Can+~ said:**
> The more you learn, the more you realize how much you don't know.

And if your think you know a lot, try teaching it.

I spent years in industry, mostly writing low level code in assembly language. I have a PhD in EE from Berkeley. I thought I was pretty good.

Then I took a university position as a CS professor. Wow, did I have a lot to learn!! One of the most humbling things was realizing that some of my (undergraduate) students knew more about some aspects of CS that I did.

Fortunately, I enjoy learning new things. I'm retired and still learning. And, yes, I still encounter frustrating problems. It's finally finding the solution that I enjoy.

---

### Post by fatum on 2009-11-12
> **Can+~ said:**
> The more you learn, the more you realize how much you don't know.

That is definitely the truth

Thank you all for your wisdom and antidotes. I will keep going on and one day be able to contribute to the computing environment for the better, I hope.

---

### Post by BloGTK on 2009-11-13
The biggest challenge is learning to think like a programmer. You have to learn to break down problems into discrete elements and then figure out how to build up to whatever you're working on. It's not an easy thing to do.

Python's a good language to start with because it tends to get in your way less than others. But don't be stuck in only one language -- the more you pick up, the more basic concepts you get and the more you understand the way in which modern operating systems work. It's like studying languages, once you understand the basic elements of how language works, it becomes easier to pick up others.

---

### Post by maximinus_uk on 2009-11-13
> **BloGTK said:**
> But don't be stuck in only one language

So true. After you've learned one language, pick another that's pretty different and learn that. I.e, after Python learn maybe C or Scheme. You'll learn more and not only that realise what sort of language you like to code in.

Then you can have a decent stab at guessing what actual language might be your favorite :D

---

