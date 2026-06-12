---
title: "Art of Unit testing"
date: 2012-09-04
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-04
Hey,
I know that unit testing is where you test individual units of code to test defects, features etc.

From your experience, can you give me a few ideas for Unit testing. I'm not talking about frameworks like CUnit, JUnit etc. I already know I'm going to be using CUnit. I'm talking plainly about unit test cases/features etc.

I have a few ideas like
1)Looking for memory leaks
2)Closing file descriptors
3)Checking if the feature is performed based on some program variables etc.

But I was looking for something different. Is there a test feature you saw in a software and was really impressed ?

If you could give me a few links/tutorials(preferably not entire books) as staring point, it would be helpful too.

Thanks.

---

### Post by ofnuts on 2012-09-04
> **IAMTubby said:**
> Hey,
I know that unit testing is where you test individual units of code to test defects, features etc.

From your experience, can you give me a few ideas for Unit testing. I'm not talking about frameworks like CUnit, JUnit etc. I already know I'm going to be using CUnit. I'm talking plainly about unit test cases/features etc.

I have a few ideas like
1)Looking for memory leaks
2)Closing file descriptors
3)Checking if the feature is performed based on some program variables etc.

But I was looking for something different. Is there a test feature you saw in a software and was really impressed ?

If you could give me a few links/tutorials(preferably not entire books) as staring point, it would be helpful too.

Thanks.
1) and 2) aren't unit testing, there are code analysis/validation. There is software for this (valgrind et al.).

---

### Post by IAMTubby on 2012-09-04
ofnuts,
okay! I understand. Can you give me a few examples of good unit testing ?

---

### Post by Tony Flury on 2012-09-04
Unit test is about ensuring that as a black box the unit (module/class) does what you expect.

So you test for failure and success conditions - does the unit do what you expect, and almost as importantly does it fail sensibly.

Does it work on corner cases : Empty strings, zero length buffers etc.

Does it execute correctly up to it's limits.

You are not trying to test every possible combination of input values, but you are trying to pick specific tests which give you confidence that the thing works, and does not fail in a nasty way.

Your unit tests should test not only the return values, it should also check for expected side effects - files being created, database rows created/modified/deleted.

One useful technique (once you have defined the interface to your unit) is to write your test cases first. Once you have a decent set of test cases written, then you write your code so that all your test cases pass.

---

### Post by IAMTubby on 2012-09-04
TonyFlury,
thanks for that.

1.Can we say that UnitTesting is same as WhiteBox testing ?
2.In UnitTesting, say if the value of i is changing 10 times within the unit/module that you are checking, you can only get the value of i when the module has finished running right ? You cannot get the intermediate values, correct ?

---

### Post by ofnuts on 2012-09-04
> **Tony Flury said:**
> 
One useful technique (once you have defined the interface to your unit) is to write your test cases first. Once you have a decent set of test cases written, then you write your code so that all your test cases pass.Coding is debugging an empty source file :)

---

### Post by spjackson on 2012-09-04
> **IAMTubby said:**
> 
If you could give me a few links/tutorials(preferably not entire books) as staring point, it would be helpful too.

What I'd suggest is downloading the source for several software packages where unit tests are used and studying the tests. Outside of the Java world, my best suggestion would be Boost (C++). I think the Boosts tests are quite understandable without knowing C++ or Boost. I don't know which C programs include good unit tests (or bad ones either).

I know you don't want books, but I'll mention some anyway. Most of the literature on Test Driven Development is Java based. The principles are not exclusive to Java, but the detailed examples tend to be Java.

Kent Beck's [Test-driven development: by example]("http://books.google.co.uk/books/about/Test_driven_development.html?id=O6FUu8c4HooC") is the definitive work.

I can recommend [Growing Object-Oriented Software Guided by Tests]("http://www.growing-object-oriented-software.com/").

Anything by Uncle Bob is worth reading, e.g. [TheThreeRulesOfTdd.]("http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd")

---

### Post by IAMTubby on 2012-09-04
spjackson,
I shall look into Boost. Although I am supposed to be working on CUnit!

> **spjackson said:**
> What I'd suggest is downloading the source for several software packages where unit tests are used and studying the tests.

That's a really good suggestion Sir. Can you help me in this regard ? Can you name a software that has Unit testing functionality ? 

Thanks.

---

### Post by spjackson on 2012-09-04
> **IAMTubby said:**
> 
I shall look into Boost. Although I am supposed to be working on CUnit!

Can you name a software that has Unit testing functionality ? 

I didn't mean for you to use the boost.test framework instead of CUnit. I meant for you to look at, for example, boost_1_51_0/libs/date_time/test which contains 9 source files which are the unit tests for the Boost Date and Time library. These give you a flavour of the sort of things that are tested via unit tests. One is attached as an example.

Without going hunting for them, I don't know of any examples that use CUnit. I would guess that there are some, and out of those that exist, some may be good examples.

---

### Post by IAMTubby on 2012-09-04
spjackson,
That is really very helpful. Thanks a lot.
I shall go through the rest of the files.

Thanks.

---

### Post by muteXe on 2012-09-04
google "examples of unit testing".

---

### Post by Tony Flury on 2012-09-04
> **IAMTubby said:**
> TonyFlury,
thanks for that.

1.Can we say that UnitTesting is same as WhiteBox testing ?


I would say that Unit Testing is more like black box testing at a unit/module/class interface level - i.e. you care about what goes into the interface (parameters and other initial conditions - what files, database records etc exist) and what comes out (return values, and side effects files, database, screen etc etc), but not how it does it inside the interface.

With WHitebox testing you know about the internals as well and you ae watching them, as well as the interfaces.

> **IAMTubby said:**
> 
In UnitTesting, say if the value of i is changing 10 times within the unit/module that you are checking, you can only get the value of i when the module has finished running right ? You cannot get the intermediate values, correct ?

Why do you need to - if you are unit testing a function and it returns the right result and does the right things to the system, why do you care if a particular variable gets incremented once, twice or a million times. If you do care (for instance for optimisation reasons) then you aren't unit testing in my opinion, you are either optimising (because your code is slow or inefficient), or you are debugging the code.

The benefit of Unit Testing is that you keep your unit test suite secure with the souce code ideally, and then if you change the code say to fix a bug or implement a new feature, you add a new unit test to your suite for that module/class which proves the bug is fixed, and then you re-run your entire suite - thus proving you have no broken anything else.

You can of couse combine you unit test suite with a good debugger to help you find a bug, as a good suite of unit tests will always do things in a known order with known results, which helps when you are trying to debug your code.

---

### Post by IAMTubby on 2012-09-04
Thanks TonyFlury.

I understand what you said about Unit Testing being like BlackBox Testing within a module.

> **Tony Flury said:**
> 
With WHitebox testing you know about the internals as well and you ae watching them, as well as the interfaces.

How do you do WhiteBox testing then ? Just curious, although this was not the scope of the initial post.

Thanks.

---

### Post by Tony Flury on 2012-09-04
> **IAMTubby said:**
> Thanks TonyFlury.

I understand what you said about Unit Testing being like BlackBox Testing within a module.


How do you do WhiteBox testing then ? Just curious, although this was not the scope of the initial post.

Thanks.

I would use a liberal sprinkling of logging type calls (print/printf/echo depending on your language of choice), or use a good debugger to step through the code and trace what is going on internally.

---

### Post by IAMTubby on 2012-09-04
Okay, so you basically modify the original source code itself right ? Isn't that a not-so-good practise ?

---

### Post by Tony Flury on 2012-09-04
> **IAMTubby said:**
> Okay, so you basically modify the original source code itself right ? Isn't that a not-so-good practise ?

It depends - it may just mean turning on a deeper level of logging which you have already implemented. Also i don't see a problem with adding a few prints here and there. In my code it is always clear what has been added as debug and what hasn't. It depends what you are debugging and why - if you are tying to debug a text based console pogram, then adding prints is a pain, but if you are debugging a GUI based pogram, then a few useful lines of text squirted into the teminal can be very useful, as you can run the gui next to the terminal window, and see the trace as it gets generated and as you interact with the GUI.

When you are debugging an application running in the background then you will almost certainly have to have logging to files - and run something like "tail -f" on the log file in an open terminal.

---

### Post by IAMTubby on 2012-09-04
Ok Tony. Got it! 
Thanks :)

---

### Post by ofnuts on 2012-09-04
> **IAMTubby said:**
> TonyFlury,
thanks for that.

1.Can we say that UnitTesting is same as WhiteBox testing ?
2.In UnitTesting, say if the value of i is changing 10 times within the unit/module that you are checking, you can only get the value of i when the module has finished running right ? You cannot get the intermediate values, correct ?
No but you don't care... If you want to know what happens because the test fails then you  can use your debugger (and in big Java aps, it's a lot easier to debug a small isolated test case than the whole application). 

But basically the (useful) unit tests will be run thousands of times in the lifetime of the code, and noone wants to spend time looking inside each time they are run.

---

