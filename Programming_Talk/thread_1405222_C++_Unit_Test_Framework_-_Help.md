---
title: "C++ Unit Test Framework - Help"
date: 2010-02-12
forum: Programming Talk
---

### Post by pholding on 2010-02-12
[COLOR=black][FONT=Verdana]I'm looking for a unit test framework for a C++ program I'm working on, the program uses several other boost libraries, so ideally I'm planning to use Boost unit test framework library. The problem is I've never really used a unit test framework before and I'm having trouble getting my head around how best to use it in a real program rather than an example “1+1=2 ok or 1+1=3 fail” tutorial type program.[/FONT][/COLOR]
 
 

[COLOR=black][FONT=Verdana]Could someone please help with the following questions?[/FONT][/COLOR]
[LIST]
[*][FONT=Verdana]Should the unit test code go in the same source files as the application code, or should I have a separate source file containing the unit test to accompany the application’s source file e.g application code goes in my_code.cpp and the testing code go in my_copy_tests.cpp. Or is there a better way of structuring unit test code?[/FONT]
 

[*][FONT=Verdana]All of the examples I've seen look at the value returned by a function to estiblish whether a test has been passed or not. How do void functions get tested? - I could test the result of running the void function (e.g create record in database) but I could see the test case code being longer than the code being tested. The program I’m working on uses exceptions rather than return codes[/FONT]
 

[*][FONT=Verdana]Finally are there any good examples of open source program that use a testing framework (ideally boost.test, but something like cpptest would be ok)? I figuring it might be easier to look at how a real program uses a unit testing framework rather than just tutorial/example code.[/FONT]
[/LIST]

---

### Post by dwhitney67 on 2010-02-12
> **pholding said:**
> 
[LIST]
[*][FONT=Verdana]Should the unit test code go in the same source files as the application code, or should I have a separate source file containing the unit test to accompany the application&#8217;s source file e.g application code goes in my_code.cpp and the testing code go in my_copy_tests.cpp. Or is there a better way of structuring unit test code?[/FONT]
 

[*][FONT=Verdana]All of the examples I've seen look at the value returned by a function to estiblish whether a test has been passed or not. How do void functions get tested? - I could test the result of running the void function (e.g create record in database) but I could see the test case code being longer than the code being tested. The program I&#8217;m working on uses exceptions rather than return codes[/FONT]
 

[*][FONT=Verdana]Finally are there any good examples of open source program that use a testing framework (ideally boost.test, but something like cpptest would be ok)? I figuring it might be easier to look at how a real program uses a unit testing framework rather than just tutorial/example code.[/FONT]
[/LIST]

For question 1:
The unit test should be separate code from the application.  If you need to test the interfaces of a class, then your test program would need to instantiate one of these class objects.

For question 2:
There are probably several ways around this.  On a program I supported in the past, we made our unit test (classes) a friend member of the class we wanted to test (yes, I know... this contradicts the answer given for Q1 above).  This friendship relationship was only enabled in debug mode; to turn off debug mode, we defined the NDEBUG preprocessor directory (ie. -DNDEBUG).  Anyhow, with the friendship relationship, the test class was able to examine the private data members of the class being tested.

For question 3:
I've used cppunit test before; it was quite simple to set up.  It's been quite a few years since I used it, but it was not that difficult.  Sorry, but I don't have any examples.

---

### Post by MadCow108 on 2010-02-12
I also only recently dived into the field of unit testing, so my answers may differ from those of more experienced people.
I too still have the problem that all these examples you find on the net are hardly applicable to a larger scale project.

1. The test source should definitely not be in the same source file. Write separate test files and link it with production release compiled binaries/libraries (if possible).
The production code should be completely free of testsuite code/dependencies.

2. How you define a failed test is up to you and the problem your code solves.
You can test the return codes, you can test the exceptions thrown (most frameworks provide assertion for this), you can check the function calls called by the testee, you can compare results to a golden file etc.
It all depends on what you want to test.
But the more side effects a function has (and a void returning function usually has these) the harder it gets to write a unit test.

In case of a database write, a good way to test would be to mock the database interface and check if the interface was called as you would expect.
There are frameworks for mocking like google-mock (related to google test which I recommend)
Of course you could also check the database itself if it contains what it should after the test.

To shorten the testcode write yourself some reusable fixtures and value parametrized tests. Often you can write few fixtures and then the tests them selfs transform to sub 10 lines. But remember to keep each test independent of the others.
Unfortunately the length of tests does depend on the quality of the code your testing. Its a pain to test code which has lots of global state and intertwined dependencies, I'm still trying to figure out how to solve this efficiently ;)
I currently utilize a mix of dependency tree of fixtures rebuilt for each test and mocked dependencies.

Also try to write tests which are as independent from the implementation as possible. That way you can refactor your code without having to change the testsuite (as long as you don't change the interface). This is again dependent of our to-test code actually has a good interface.
(Of course sometimes implementation tests are useful too, e.g. for debugging when applying test driven development)

---

### Post by unittesting on 2011-07-12
I know this is a bit late, but there's a new commercial framework for C/C++ unit testing which is even more powerful than others, called [Isolator++ for Linux]("http://www.typemock.com/isolatorpp-product-page?utm_source=ubuntuforum&utm_medium=cpp-unit-test-framework&utm_campaign=forum-post").

It lets you test your code without changing a line of it and also test legacy code. 

It may be worth checking out.

---

