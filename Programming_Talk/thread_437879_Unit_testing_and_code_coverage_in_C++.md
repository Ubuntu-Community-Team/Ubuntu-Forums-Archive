---
title: "Unit testing and code coverage in C++"
date: 2007-05-09
forum: Programming Talk
---

### Post by freefrags on 2007-05-09
Hi all,

Ive been looking around on the internet for a good testing framework. Ive noticed that there are several test frameworks for C++ around and it seems like CPPUnit is the most commonly used test framework.

the thing is im looking for a way to:
[LIST]
[*]unit test my code
[*]see the code coverage
[/LIST]

I found lcov which is an extension of gcov. lcov seems to be able to generate a coverage report in html, pdf etc. 

My next search was for an IDE or a plugin for an IDE which could at least run the unit tests and give some visual feedback. However i have had no luck.... 

does anybody know a good tutorial for setting up a test environment like this?? or could you please help me out a bit

thanks in advance

Raymond

---

### Post by treak007 on 2007-05-10
Look at a tool called graphviz, it lets you automate the generation of visualizations. Also, I believe boost has a pretty nice unit testing framework.

---

