---
title: "best performance language for programming with sqlite"
date: 2011-10-07
forum: Programming Talk
---

### Post by dimitrp on 2011-10-07
hello,
i want to develop an extension to Firefox, which will use sqlite, and i want to have the best possible performance.
do you know any programming language which would suggest for really fast transactions??
i am more familiar with javascript and firefoz add-on are developed in javascript, so i thought of using either this (javascript) or c++ for alternative
any idea??

thanks in advance

---

### Post by lovinglinux on 2011-10-10
If you can, I would advise to stick with javascript, because if you develop your add-on with C++ you will probably need re-build and release a new version of your add-on with every new Firefox release, which occurs every six weeks. 

This should help you getting started:

[https://developer.mozilla.org/en/Storage](https://developer.mozilla.org/en/Storage)


Although I develop Firefox add-ons and I make extensive use of sqlite, I not an good programmer. However I might be able to help you once you have a prototype. When I was starting, I had a lot of trouble with sqlite databases, specially performance. Now, although my code is probably not elegant, I have managed to build some decent stuff.

---

### Post by Tony Flury on 2011-10-10
Also if you have a lot of data in your database, and your application is simply fetching and displaying (and not doing much processing), you might well find that most of your execution time is spent actually executing the SQL, and that the programming language you use is probably (mostly) immaterial.

Bear in mind the maxim : Premature optimisation is the root of bad design.
So : Design the right way - develop it using the tools that are most suitable (sounds like javascript in this case), and optimise the slow bits - if that means converting some of your processing to a C++ library which you call from javascript - then do so, if that means adding indexes etc to your database, do that - but most of that stuff you should do after you know where your performance issues are.

---

### Post by dimitrp on 2011-10-11
thanks for the reply, i will start with javascript.
the main purpose of the project is to minimize any delay, that;s why i thought of using sqlite, do you know any other db which you be more appropriate for delay optimization?

---

### Post by Tony Flury on 2011-10-11
dimitrp : All I can say is start with what you know.

If your database is likely to be large, then the biggest source of delay is likely to be things like disk access time, index efficiency etc - so you might need to look at a more robust Server approach (rather than SQLite), but I would develop using sqlite and only refactor to another system if you find you need too - you might only see effects if your database is going to have many tables, and many tens of thousands of rows, and your application will need complex queries, with a lot of different updates.

If you are really worried about your database delays, or even if you just want a clean design, then you would be wise to wrap your DB access code into a class/module of it's own (i.e. abstract your db access, and it's associated SQL) - that way you only have one module to port if you decide that sqlite is not for you - and your database, table structure etc become a implementation detail within one module/class rather than a dependency of your entire application.

---

