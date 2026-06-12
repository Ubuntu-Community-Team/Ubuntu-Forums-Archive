---
title: "Some help with what I should take up next"
date: 2007-08-02
forum: Programming Talk
---

### Post by engti on 2007-08-02
A little bit of background which I hope will make things clearer to you.

When I was in the 7th grade I remember using GWBasic in school.

That was my only brush with computers until I left college.

My work requires me to use a lot of Excel. Since it used to mostly consist of a lot of repetitive stuff, I began using Macros to manage things.

Well, next thing I know is that I began to use VBA to build small applications used mainly for Data entry and manipulation.

I now find myself getting quite ambitious about this. I want to build a travel related website. And I had been building some modules using Visual Basic Express.

But the things is that I feel that if I used some Linux based tools my development and hosting costs would be much cheaper. (I am on a very thin budget :( )

Looking at my background, which language/development tool I could look at for someone at my skill level. 

Any advice?

Much appreciated

---

### Post by xtacocorex on 2007-08-02
It as first sounded as though you wanted a database application.  I'd use one of the SQL's (MySQL, PostgreSQL, etc...) and interface with Python and use GTK+ for a GUI.

I was incorrect, you want web stuff.  PHP will interface with SQL databases and is easily rendered with HTML.  There is also Ruby-on-Rails and Django - which is Python based.

As for tools, I wouldn't try to get accustomed to an IDE, I'd keep it simple with gEdit for coding.

---

### Post by bobbocanfly on 2007-08-02
For web based stuff that heavily uses Databases PHP is definately the way to go. Purists would probably argue that PHP isnt that good a language (i dont get why people say this, i love it) but it is highly documented and ties in extremely well with MySQL databases.

PHP is also dead easy to learn and object orientation can be achieved quite easily.

---

### Post by LaRoza on 2007-08-02
PHP + MySQL

---

### Post by engti on 2007-08-02
Heh.... sorry for the confusion. I *WAS* thinking more in terms of web apps.

Thanks for the responses. I am looking at Python right now.

Planning on checking out PHP next. 

Maybe I shouldn't put too much on my plate and see which one of these two I am best able to manipulate.

It's not so much what the language is capable of, but what I am capable of making it do kind of scenario.

---

### Post by starfry on 2007-08-02
I have used PHP for years and it is a good solid platform with a lot of support on the web.

However...

There is a lot of hype about "Ruby on Rails" and I am currently evaluating that. If you aren't tied in to thinking in the C++/PHP coding style it may be worth looking at as the Rails framework does a lot of the grunt work for you.

And there is a really decent IDE for it called Aptana RadRails.

---

### Post by pmasiar on 2007-08-02
Python is easiest language to learn, and scales well for more complicated tasks. Wiki in my sig has many links, among other very simple web apps (using plain CGI to avoid confusion). 

Excellent database for web apps is SQLite: instead of runing database server, it is just libraries run in single-user mode, but fast. database is just a file, easy to back up restore - excellent for testing. Is fully SQL, so when you outgrow it, you can swith painlessly to MySQL or Postgres. Of course all mentioned tools are free software.

PHP, is simple to start, but it's structure (or lack of it :-) ) has tendence to result in very messy code. Yes, it is possible to avoid it, but it is not simple and you need good guru and self-discipline. [Model-View-Controller](http://en.wikipedia.org/wiki/Model-view) is way to go for web apps, to separate different parts of program to different layers, naturally.

Ruby on Rails was first rapid web app framework, and 2-3 years ago it was the best tool on the market. Not anymore, Python community created two comparable frameworks. Django is recommended for beginners, is good enough for 70% of the tasks, auto-generates your database tables and most maintenance code from class definition, you can have simple app up and running in hours. When your need outgrow Django, or you will like modules which Django does not support, switch to TurboGears.

Ruby is loved by former Java programmers, who missed Perl and Ruby is their first experience with latent dyping (non-static like Java and VB has), and former Perl hackers who like quirky languages. 

But Python is first language designed with one fundamental insight: **programs are read more often than written** so it is optimized to be readable by humans.

---

