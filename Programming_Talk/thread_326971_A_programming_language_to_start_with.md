---
title: "A programming language to start with"
date: 2006-12-28
forum: Programming Talk
---

### Post by fasoulas on 2006-12-28
Hey all this is my first time in the progamming talk section.

i decided to post here  because i want opinions about what programming language to start with.I currenly have little expirience with visual basic and pascal.

But i am interested in learning other more usefull programming languages and i want your suggestions

I am thinkin of starting with C/C++ or Python that is also used on linux

---

### Post by meng on 2006-12-28
It's a matter of personal preference, and I'm sure you'll get many different responses, but I have recently converted to Python with a great deal of enthusiasm. It is a good general-purpose language with easy to learn intuitive syntax and good cross-platform support. Perhaps you could elaborate on what sort of tasks you envisage programming, because depending on what these are you may wish to choose another language.

---

### Post by amo-ej1 on 2006-12-28
The programming talk forum is filled with similar questions, I think that hitting the search button will enlighten you the most. But  the one answer you will find is that it is 100% personal

---

### Post by fasoulas on 2006-12-28
I want some links about C/C++ or Python to start with

---

### Post by meng on 2006-12-28
[www.awaretek.com](www.awaretek.com)

---

### Post by maxamillion on 2006-12-28
I think Java is a very good language to start with because it is safe, object oriented, and has C/C++ style syntax so converting over to others will not be entirely difficult. Many Universities globally are beginning to teach Java as the intro courses for computer science majors for these exact reasons.

Java doesn't generally have the best reputation in the open source community and I think alot of peoples complaints were phased out in Java5, they just never took the time to read the release notes. Also, it is open source now ... 

Is Java my favorite language? ... no, I actually python is but I don't think it should be where a programmer starts because python has some unique syntax traits that we all know and love but the reason we love them is because we appreciate what all the language is doing for us because we have suffered through chasing pointers in C.

That is my opinion ... again, there is no "best language" and therefore, no "best language to start with" ... you will essentially learn all the same concepts in any language and the rest is just syntax so read a few short tutorials and just pick one. :)

---

### Post by maddog39 on 2006-12-28
As far as a first programming language, C/C++ is VERY VERY challenging. I've been an active PHP developer for almost 3 years now and I started doing C++ with a few books and I'm trying to make a pretty simple GTKMM application with it and its becoming a really big challenge. PHP and C++ are very similar and almost the same in syntax yet I continue to have problems learning it. So very very high learning curve on C++. I also started learning python, I learned most of the language and understood it in 2 weeks, and in one day I made a fully working application using wxPython and no online help from tutorials, etc. So i'd definetly recommend python from personal experience. Although i'm not bashing C++ in anyway, I still love it, just a very challenging langauge.

---

### Post by pmasiar on 2006-12-28
> **maxamillion said:**
>  there is no "best language" and therefore, no "best language to start with" ... you will essentially learn all the same concepts in any language and the rest is just syntax so read a few short tutorials and just pick one. :)

I agree that there is not single "best language" - if it was, we would have substantially less than current 8K+ programming languages. But I strongly believe there is couple of best languages to start with. They are all dynamically typed scripting languages, like Python and Ruby, and Python is my preferred because of readability and simplicity. Regardless of being used in universities, IMNSHO Java is less suitable as first language because of static types, static exceptions and forcing objects before student is ready. Learn basic of programming in python, and then you can upgrade to java if you feel so - or not, because Python will scale up :-)

This horse was beaten to death in at least dozen threads on this forum only in last month. I don't think many people are willing to repeat that they said, we read each other opinions and responded to them - check  previous posts, ask questions in context, but there is not much more to be said.

If you want to learn python, you may want to take a look at [learn Python wiki]("http://learnpydia.pbwiki.com") - with links to tutorials, data structures, and tasks  with special preference for needs of  beginners.

---

### Post by meng on 2006-12-28
Not to mention that python university courses are on the rise.

---

### Post by Wybiral on 2006-12-28
I'm going to throw in my two cents as usual...

If you plan to migrate to lower level stuff like ASM or even C, BASIC might be a good start. FreeBASIC, Basic4GL/SDL, ect...

If you are going to migrate to higher level stuff... Python!

Python code can easily be converted to many high level languages (including C++) and is very easy to learn, and will teach you good programming habits, mainly structure and layout.

It is also easy to optionally code OOP, or procedural and has many many good examples to learn from on the internet.

---

### Post by rekahsoft on 2006-12-28
I would recomend Python.

---

### Post by SuperMike on 2006-12-28
Go with PHP5. That's what I did after wasting time with Kylix, JSP, Java, C#, C++, C, Perl, and Python. I like getting work done rather than worrying about how to do something in a language or sitting in long meetings doing academic discussions.

sudo apt-get install apache2*
sudo apt-get install php5*
sudo apt-get install sqlite3*
sudo apt-get install mysql*
sudo apt-get install postgresql*

However, when you get around to web development stick with:

* Use heavy CSS on your pages instead of coding all the formatting options into the HTML.

* Use Javascript and AJAX very sparingly where it makes sense to use it, and test it in all browsers on all platforms. Also, read up on security risks with AJAX and the preventative measures for that.

* When not doing tabular data, use DIVs instead of TABLE tags, but test on all browsers and watch what happens when someone changes their font size -- you don't want text overlaps into areas you didn't expect. DIVs, when done right and when you learn the proper CSS formatting techniques for them, can make beautiful lightweight pages that can be "skinnable" (changed easily by simply changing the CSS page). You'll learn to appreciate that when you finally pull it off.

* If someone asks you to do web services, consider going with the more modern and recently popular (as well as easier) REST standard instead of SOAP or XML-RPC.

* Use a variable naming convention like $sFirstName and $nTicketCount and $oMyObject or something like that.

* Think of your web page as a collection of gadgets or widgets. Put the gadgets into functions. Stick the functions into object classes. Do not intersperse PHP and HTML back and forth -- it creates spaghetti code that will make you unpopular among PHP programmers.

* Always use a database class that abstracts your native database calls from your PHP. That way, if you need to switch databases, you just switch one database class out with another and *poof* (hopefully) your code still works.

* Avoid XSLT -- it slows your page down tremendously when hit by thousands of users.

* Do timed tests when evaluating PHP frameworks -- don't believe the hype. Evaluate several and find the one that works best for you and yet is the most popular of those remaining choices.

* Get used to using PEAR when coding -- it's a timesaver sometimes. However, it's not perfect and you might be able to do it better occasionally.

* When programming, think of your code in objects, but don't go crazy because it can slow the performance down and become a fruitless academic exercise that delays project timelines. I mean, throw everything into at least one set of object levels, but I find very few cases where it makes sense to have objects being composed so that they could be fed into other objects as method parameters. I only do the object feed into other objects when it makes good sense to do so.

* PHP has special variables that begin with $_ and usually are followed by an uppercase word like COOKIE, SERVER, etc. When you need to use these, always put them into an object like $web and create a special method (function) for it. This is because you'll often find yourself calling these things with not just one line, but several lines, such as with encryption/decryption, error checks, etc. By doing this, you can encapsulate that repetitive logic into a simple set of object methods and can shorten your project schedule.

* Turn off something called Magic Quotes. They suck.

* Always read up on how to secure Apache and PHP and try some things out to improve your page security.

* Learn these databases: SQLite, MySQL, and PostgreSQL. SQLite makes a great database for very tiny projects or when you're building a standalone application on a workstation (such as a "Quickbooks Pro" knockoff or something). MySQL is popular on many projects, but is slower than PostgreSQL when you have more than about 10 heavy duty transactions going on at the same time. PostgreSQL is harder, but more rewarding with a richer API, an API that's more like ANSI/92 standard SQL, and can handle higher workloads. (Note that PostgreSQL is slower than MySQL when doing less than 20 simultaneous, minimal transactions.) For me, I just stick with PostgreSQL and SQLite, but I keep up on MySQL because I might need to join a team using it on a project.

* Learn when it makes sense to introduce a Message Queue into your project and get used to using it.

* Use the eXtreme Programming (XP) methodology *ONLY* for prototyping or doing inhouse or personal projects, *NEVER* for creating stuff to push out quickly to a customer. You could end up costing a company several thousand dollars with costly mistakes.

* Learn the advantages of not only database normalization, but when it makes sense to do database *denormalization*. Most newbie developers right out of college don't even realize that database denormalization makes a lot of sense in certain cases too.

* On massive projects, or projects that may become massive, always consider breaking up the databases into 3 separate databases or database servers. One is for data entry transactions and is tuned to be heavily normalized. The data entry database is temporary and stores records only for a day before pusing them to production. One is for data mart / warehouse / historical / reporting and is often fairly denormalized. The data warehouse database stores data over a longer period of time and is usually used for doing lots of processor-intensive queries and for reports, and usually has data that is a few hours old, or a day old, and older. And finally, you have the production database. This usually is tuned with a nice blend between normalization and denormalization on certain tables. This is the master database that stores the most current data when the data entry database records are eventually fed into it. The business' events and processes will often run off the production database. By using these techniques, you can create a system that can be brought down for maintenance in sections without affecting other departments.

* For doing web reports, consider 'html2pdf php script' on SourceForge. It's a fork of the popular FPDF framework for generating PDF reports on the fly. Also consider that some report PDFs may need to be created by scheduled jobs (because they take too long to build and might be a popular daily download) and not done dynamically.

* Comment your code simply but religiously. If you write more than 15 lines of code and haven't added at least a one line comment, you're likely not being very nice to the next programmer who comes along to work with your stuff.

* Practice KISS (Keep It Sweetly Simple) principles when programming. Not everything has to be an exercise in how cool you are, or an academic exercise, or a 4 line masterpiece that very few people will understand when they inherit the code after you.

* Learn about Super Affiliate Marketing (SAM) when you get nice and good. These are forum or interesting sites on the web that make all their money on Google AdSense revenue. It can help you generate a lot of cash on the side while you do a programmer day job (if that's what you plan to do). As well, you can also build $2000 - $6000 websites for people -- I get these oddball gigs every once in awhile that make my day. Political candidates often pay good money for these too.

* When asking for help with programming, try to look it up first and then ask politely. If someone flames you (because sometimes that can happen unfortunately), then I've found the best policy is to just not reply, and if I'm strongly compelled to reply, I try to work it out professinoally in private messages (email, forum private messages, etc.). And when you learn how to do something, blog it so that others can do it too -- you give a little to get a little when using the Internet. By blogging it, you also reduce having to ask the same question more than once again. Another alternative to blogging it is to find a document storage, code snippet, knowledgebase, or FAQ site on the web and post your procedures there.

So there, that's all I know. Now go forth and learn how to make some big money.

---

### Post by fasoulas on 2006-12-28
> **pmasiar said:**
> I agree that there is not single "best language" - if it was, we would have substantially less than current 8K+ programming languages. But I strongly believe there is couple of best languages to start with. They are all dynamically typed scripting languages, like Python and Ruby, and Python is my preferred because of readability and simplicity. Regardless of being used in universities, IMNSHO Java is less suitable as first language because of static types, static exceptions and forcing objects before student is ready. Learn basic of programming in python, and then you can upgrade to java if you feel so - or not, because Python will scale up :-)

This horse was beaten to death in at least dozen threads on this forum only in last month. I don't think many people are willing to repeat that they said, we read each other opinions and responded to them - check  previous posts, ask questions in context, but there is not much more to be said.

If you want to learn python, you may want to take a look at [learn Python wiki]("http://learnpydia.pbwiki.com") - with links to tutorials, data structures, and tasks  with special preference for needs of  beginners.

I now that is a subject that is taught a lot in this forum so can someone post me links from threads

---

### Post by n.aggel on 2006-12-28
i would suggest c althougn it isn't easy, it is a very "clear" and "clean" language.And if you learn it, you will be able to learn almost any other language.

If you want to write good programms soon after you start learning, try java or visual basic...

---

### Post by pmasiar on 2006-12-28
> **fasoulas said:**
> I now that is a subject that is taught a lot in this forum so can someone post me links from threads

If you cannot be bothered to read forum past first page (hint: click on page 2, 3 etc on the bottom), and read thread names, sorry i cannot be bothered to post links for you

---

### Post by compwiz18 on 2006-12-28
Not a language per say, but HTML: very very useful, and very easy - once you have that down, Python :D

C++ comes way later - most of the time you can do everything in Python.

---

### Post by zorglab on 2006-12-28
> **pmasiar said:**
> I agree that there is not single "best language" - if it was, we would have substantially less than current 8K+ programming languages. But I strongly believe there is couple of best languages to start with. They are all dynamically typed scripting languages, like Python and Ruby, and Python is my preferred because of readability and simplicity. Regardless of being used in universities, IMNSHO Java is less suitable as first language because of static types, static exceptions and forcing objects before student is ready. Learn basic of programming in python, and then you can upgrade to java if you feel so - or not, because Python will scale up :-)

This horse was beaten to death in at least dozen threads on this forum only in last month. I don't think many people are willing to repeat that they said, we read each other opinions and responded to them - check  previous posts, ask questions in context, but there is not much more to be said.

If you want to learn python, you may want to take a look at [learn Python wiki]("http://learnpydia.pbwiki.com") - with links to tutorials, data structures, and tasks  with special preference for needs of  beginners.

I also agree there is no single "best" programming language. All depends on what you want to achieve.

However I wouldn't recommend Python as a beginner's language, because it is dynamically typed. While this may seem easier to start with, it quickly gives headaches when working out bugs.

The big advantage of a statically typed language, like Java, is that it forces you from the beginning to have good programming practices. It won't let you write quick and ugly hacks that easily and that's a major advantage to get things done right. Sure, it's a little bit more difficult to learn, but imho you'll learn much more.

BTW, Java has a wonderful IDE called Eclipse. It may be useful ;)

---

### Post by meng on 2006-12-28
> **zorglab said:**
> However I wouldn't recommend Python as a beginner's language, because it is dynamically typed. While this may seem easier to start with, it quickly gives headaches when working out bugs.
You raise an excellent point. My non-expert perspective is that rigor can be good and bad. Good, insofar as it promotes good programming practices. Bad, insofar as it raises the barrier to entry.

---

### Post by gummibaerchen on 2006-12-28
You need this one link for a start:

[http://diveintopython.org/toc/index.html](http://diveintopython.org/toc/index.html)

Have Fun!

Yeah, and maybe add this to your Feedreader:
[http://www.learningpython.com/](http://www.learningpython.com/)
(if you have basic experiences)

---

### Post by Wybiral on 2006-12-28
Read here: [http://www.ubuntuforums.org/showthread.php?t=327239](http://www.ubuntuforums.org/showthread.php?t=327239)

---

### Post by maxamillion on 2006-12-28
Don't get me wrong, I love python but I don't think it should be a first language because of a few things.

[LIST=1]
[*] No type checking.
[*] Unique data types. (Unique as in "not found in other languages" which can make life harder when learning other languages)
[*] No "real" variable declaration
[*] Not learning the difference between a float and a double.
[/LIST]

There are more I'm sure I could come up with but those are just off the top of my head, but then again ... this is just my opinion and I must reiterate that Python is by far my favorite high level language but it has become so due to my appreciation for how much it does for me and I just don't think programmers should be shown how to do something with such syntactic sugar and then later force them to learn backwards because majority of people who I have seen do this (myself being guilty during my transition from Java to C) will get to a situation where they say "why can't you just do <this>? <What_ever_language> can" .... 

Yes there are a group of languages that are better than others to teach basic concepts, but I think assembly language was the most eye opening I have come across to date because you really learn what's going on behind the high level syntax to perform functions ... because you have to write it, but I would never wish it on a newbie.

In the end, its all about preference and choice ... you will always hear opinions, you might want to look into just picking one and sticking it out, learn it and then start learning another ... compare and contrast for yourself what you like and don't like.

---

### Post by pmasiar on 2006-12-28
> **zorglab said:**
> However I wouldn't recommend Python as a beginner's language, because it is dynamically typed. While this may seem easier to start with, it quickly gives headaches when working out bugs.

The big advantage of a statically typed language, like Java, is that it forces you from the beginning to have good programming practices. It won't let you write quick and ugly hacks that easily and that's a major advantage to get things done right. Sure, it's a little bit more difficult to learn, but imho you'll learn much more.

This is such a BS which I am tired to respond to in every thread. Most often from people who never used dynamically typed language. Dynamic typing is  simpler for learners, because if type (class) has right methods, it just works. You need to check methods on compile time, or in runtime, no way around it. With static typing, newbies have problems to create collections and get objects out (because **type nazi** compilers frustrate newbies without letting them  even to compile even simple programs). 

For simple programs (which are 100% of what newbies do), dynamic typing works just fine. When newbie learn programming and want to get hired in Fortune 500 company and be able to maintain 40MB of source code, *then* they can learn java/C++/C# or whatever. Or write small little scripts for rest of their life, amusedly looking at "real programmers" using 300 java classes to do task which takes 200 lines of python code.

Yes, there is dynamically typed language open to ugly hacks - it is perl, not python.

self-invoking [Godwin's Law]("http://en.wikipedia.org/wiki/Goodwins_law")

---

### Post by gh0st on 2006-12-29
If you wanna learn Python this is a good place to start - [http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

---

### Post by Herodes on 2006-12-29
Take Lua to start off.. and keep going..

[http://www.ubuntuforums.org/showthread.php?t=317426&highlight=lua](http://www.ubuntuforums.org/showthread.php?t=317426&highlight=lua)

[http://www.lua.org/](http://www.lua.org/)

---

