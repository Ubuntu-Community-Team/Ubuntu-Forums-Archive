---
title: "Prog. Language to create Website/Apps"
date: 2009-08-25
forum: Programming Talk
---

### Post by ataide.carlos on 2009-08-25
Hi all,

Hope you can help with this. I'm creating a new project with various utilities, and will be using a website to make those available. (Stuff like job searching, edit CV, e-book storage)

I'm adding content as I go along, and right now I really have no strict guidelines. 

My problem is this: I will program all content, and it will take me a long time because of all the different programming languages involved. 
I am by no means an accomplished programmer, I have forgotten much of what I knew, but knowing the basics of programming its just a matter of learning a new language.

MySQL - Database
PHP - Server side and communicate with DB
JavaScript - small scriptlets to validate form entries

I will then need to run some scripts using a command line. (image manipulation using ImageMagick, or converting video files)

Because I will need to learn these languages, I'm asking for your advise on which programming language would be most versatile to accomplish all these tasks.

I've never used Java, but from what I've read, looks like one that would be easy to learn and has many uses.

PS. By the way, has anyone ever use JavaServer Pages? Is this anything like PHP and ASP?

---

### Post by Mirge on 2009-08-25
PHP is your best bet, imo, for server-side web applications. You can use JS to enhance the user interface, but please don't go overboard and end up ruining your UI.

EDIT: Don't rely on JS for your only method of form validation -- not everybody has it turned on, and it is easy to get around.

---

### Post by hessiess on 2009-08-25
Use PHP WITH a framework like cakephp or another web development environment like Ruby on Rails. Using PHP with no framework for your first application, will just result in an unmaintainable, imposable to secure mess, you have to stick with common design patterns like MVC and keep a single point of entry (which using a framework will do for you).

And as above, don't use JavaScript for anything impotent. Remember if it runs client side, its easy to hack.

---

### Post by fishy6969 on 2009-08-25
Just to throw another hat into the ring - Django with Python is another popular choice and well documented at [www.djangobook.com](www.djangobook.com)
Just finished Chapter 14 myself as it happens. I'm by no means a competent programmer but it's making sense and my initial 'doodlings' have been a success.

---

### Post by ataide.carlos on 2009-08-26
Hi, first of all thank you for your answers.

I will try to remember that Javascript is not secure, but how can I authenticate the users in the website?

How exactly does the framework do? What I am doing is basically creting several PHP files and use those for simple tasks. One for connecting to the DB, other to retrieve data, to create the HTML page, etc.

So I can have a clear understanding of all the code and don't repeat myself.

---

### Post by hessiess on 2009-08-26
> 
Hi, first of all thank you for your answers.

I will try to remember that Javascript is not secure, but how can I authenticate the users in the website?

Just do it server side;)

> 
How exactly does the framework do? What I am doing is basically creting several PHP files and use those for simple tasks. One for connecting to the DB, other to retrieve data, to create the HTML page, etc.

So I can have a clear understanding of all the code and don't repeat myself.


A framework just does a lot of the ``boilerplate code'' for you, and forces you to use good application design pasterns.

For example, when outputting data into HTML use a templating language, DO NOT use string concatenations and print statements as it gets ugly very fast, a framework does all this automatically.

---

### Post by WitchCraft on 2009-08-26
There are several other options to consider:

ColdFusion with a Free Server Engine
JSP (Java Server Pages) with Apache Tomcat
ASP.NET with MonoDevelop and Mono and mod-mono
PHP (mod-php, FastCGI, CGI)
Python Psycho FastCGI
Perl (mod-perl)
C++ (CGI)

C++ of course has the fastest performance (but the longest development time), followed by Python Psycho, which in turn is closely followed by ASP.NET.

Perl has the fastest development time (time to market), but it's badly maintainable.

ColdFusion is the way to go if you want it to be easy and fast to do stuff with PDFs and Flash, or generally speaking multimedia.

Java Server Pages are in Java, which is particlarly nice to integrate JavaScript and JavaApplets. Since it's Java, and there are JSP servers in Java, so you write the source once and can run it on every platform that can run Java.

PHP has the largest community, and it's the cheapest.
This means you'll find many ressources and examples online.


Particulary, you should ask yourself which database you want to use. Because the database always is the bottleneck of performance, plus once you started on a more complex project using a certain database, there is no way back, except if you can afford to shredder your sourcecode.

I would recommend PostgreSQL, because it offers most functionality. MySQL is only good if you use InnoDB.

So your choice depends on what you want.

- Want to stay Microsoft compatible and learn their technologies? 
Use ASP.net

- You like cheap and dirty spaghetti code?
Use PHP

- Want to create apps that are extremely fast
Use C++

- Want to have an easy life?
Use ColdFusion

- Want to have the fastest time-to-market and don't give a damn on program maintainability?
Use Perl

- You are a masochist and want to fail?
Use Java.

- Want development to be extremeley fast and simple, and maintainable code?
Use Python Psycho.


- Want DataBase speed?
Use MySQL with InnoDB.


- Want an efficient DataBase that offers useful functionality?
Use PostgreSQL.

In other words, I recommend Python Psycho & PostgreSQL.

---

### Post by hessiess on 2009-08-26
> **WitchCraft said:**
> There are several other options to consider:

C++ (CGI)...

- Want to create apps that are extremely fast
Use C++


Using C++ via CGI would be slower than mod_/perl/php/python etc as CGI has to spawn a new process for every request, which is slow, For optimal performance with Apache you would want to write the application in C or C++ as an Apache module.

And PHP can be used to write perfectly clean and maintainable code, however the majority of PHP developers are new to programming and don't have a clue what they are doing/ don't understand common design patterns(MVC). Though the language would be a lot nicer if they stuck to a consistent naming scheme and ditched the functions which basically do exactly the same thing.

---

### Post by Mirge on 2009-08-26
> **WitchCraft said:**
> 
Particulary, you should ask yourself which database you want to use. Because the database always is the bottleneck of performance, plus once you started on a more complex project using a certain database, there is no way back, except if you can afford to shredder your sourcecode.

I would recommend PostgreSQL, because it offers most functionality. MySQL is only good if you use InnoDB.


With no disrespect intended, I have to say that is just untrue. I use MySQL for clients (using MyISAM and InnoDB in different DB's). I've _rarely_ come across an instance where the database was the bottleneck, if the tables were designed properly. I can still remember a few years back when I had to work on another programmer's project for a company I was doing work for, once the MySQL table filled up to 650k rows, it BOGGED hardcore... found the page causing it, looked at the query.. a quick EXPLAIN SELECT statement let me know there was no index. Altered the table to add an index, query took less than 1/10th of a second to run.

> **WitchCraft said:**
> 
- You like cheap and dirty spaghetti code?
Use PHP


Again, I have to disagree. Maybe you've had some bad experiences with PHP in real-world projects, or you have no real-world experience with it. Saying that all PHP is is cheap & dirty spaghetti code is ignorant.

---

### Post by Reiger on 2009-08-26
I love spaghetti. But I prefer lasagna. Though, neither is as tasty as tagliatelle or fettuccine. 

Anyways without proper Goto's writing spaghetti code becomes rather more difficult. Yes, there is plenty of poor PHP code out there but that doesn't mean that _because_ you write in PHP you produce spaghetti. You might have more skill and produce tagliatelle instead. :P

Seriously though the quality of the code depends more on the programmer than on the language: plenty of sloppy coding & simply not knowing the risks has produced untold numbers of security vulnerabilities in Windows & assorted MS products... And yet, I do not see any PHP files in Windows or assorted MS products...?

EDIT: @ The OP: if you are not experienced in any way with the language, I suggest you do some toying with your language of choice (be it PHP or Perl or Python) first before actually "committing" to your project. Writing a web app from scratch when entirely new to "the game" is a tall order indeed.

---

### Post by CptPicard on 2009-08-26
The point in PostgreSQL vs. MySQL is that for a long time Postgres was the only database that actually had proper transaction support, inner queries, triggers... it just was more of a complete database. In recent years it seems like MySQL has been catching up, but I've never managed to switch and I never understood why Postgres isn't the de facto db...

---

### Post by Mirge on 2009-08-26
> **CptPicard said:**
> The point in PostgreSQL vs. MySQL is that for a long time Postgres was the only database that actually had proper transaction support, inner queries, triggers... it just was more of a complete database. In recent years it seems like MySQL has been catching up, but I've never managed to switch and I never understood why Postgres isn't the de facto db...

To be honest, I've not gotten to use PostgreSQL as often as I'd like over the years, mainly due to the fact that when clients come to me wanting work done--they already are set on using MySQL because they are familiar with it, have it already installed & set up, etc. Come to think of it, most of my clients probably haven't even heard of or used PostgreSQL. Maybe MySQL's availability is what keeps it going, not sure.

EDIT: Yay!! No more super creepy clown avatar! Lmao

---

### Post by ataide.carlos on 2009-08-26
Thanks for the new batch of replies! Very helpful, got me curious on a few languages.

Since I'm building on my own, leaning towards PHP, because its very easy to find tutorials/examples. By the way, I'm trying to make this very cheap, don't have money to spend on licenses. The learning curve is also an issue.

My first try with PHP was creating a Chat room, and it worked great. Pretty simple, but the ; at the end is a bit annoying.

Why is Perl "badly maintainable"?
Has anyone ever used Java/JSP for the creation of webpages?

At home I've always used MySQL, but use Oracle at work. I'm guessing Oracle will be heavier on the machine right?

---

### Post by CptPicard on 2009-08-26
I have used Java and JSP... there the issue is the learning curve and the relative cumbersomeness of the whole thing. It can really take a LONG time to become reasonably competent and to know all the frameworks and libraries you're supposed to be using. J2EE on the other hand can, if you need it, go all the way.

Mind you, I would also be in the Python/Django camp...

---

### Post by hessiess on 2009-08-26
> **ataide.carlos said:**
> Thanks for the new batch of replies! Very helpful, got me curious on a few languages.

Since I'm building on my own, leaning towards PHP, because its very easy to find tutorials/examples. By the way, I'm trying to make this very cheap, don't have money to spend on licenses. The learning curve is also an issue.

My first try with PHP was creating a Chat room, and it worked great. Pretty simple, but the ; at the end is a bit annoying.



Be very careful with PHP examples, there is a lot of bad PHP code on the net.

> 
Why is Perl "badly maintainable"?

Perl is not `badly maintainable' though, like PHP it dousen't discourage bad design patterns, so there is a lot of badly written code around.

> 
Has anyone ever used Java/JSP for the creation of webpages?


I have looked into using Clojure breafly(Lisp on the jvm), but quickly dumped the idea as running java requires a spatial `java' server (Jetty), which just dousent work in a shaired hosting environment. If you want to use java, look into the google app engine.

---

### Post by WitchCraft on 2009-08-26
> **hessiess said:**
> Be very careful with PHP examples, there is a lot of bad PHP code on the net.

Perl is not `badly maintainable' though, like PHP it dousen't discourage bad design patterns, so there is a lot of badly written code around.


Well, of course there is good code and bad code in every language, and there are good programmers and bad programmers for every language. That's a truism, and I guess self-evident to everyone.

If you have ever looked at an average Perl code that was longer than 100 lines that you didn't write yourself, it can become difficult to understand what it is doing because the syntax is quite cryptic. That's even true for your own code if you didn't look at it for a long time.


And sure, if you intend to sell web applications including database, you should use MySQL because that's what most people are running.

Non the less, I've ported some (larger) applications between MySQL and PostgreSQL, and it's a fact that PostgreSQL was almost always up to ten times faster.

---

### Post by Mirge on 2009-08-26
> **WitchCraft said:**
> Well, of course there is good code and bad code in every language, and there are good programmers and bad programmers for every language. That's a truism, and I guess self-evident to everyone.

If you have ever looked at an average Perl code that was longer than 100 lines that you didn't write yourself, it can become difficult to understand what it is doing because the syntax is quite cryptic. That's even true for your own code if you didn't look at it for a long time.


And sure, if you intend to sell web applications including database, you should use MySQL because that's what most people are running.

Non the less, I've ported some (larger) applications between MySQL and PostgreSQL, and it's a fact that PostgreSQL was almost always up to ten times faster.

Wow really? No sarcasm here, can you please show some examples of this performance increase? We aren't experiencing any MySQL performance issues, but if we can scale better with PostgreSQL maybe some proof would help me convince clients to potentially make a switch.

EDIT: I tend to agree, regarding Perl. The whole TIMTOWTDI (There is more than one way to do it) thing is a double-edged sword.

---

### Post by hessiess on 2009-08-26
> **WitchCraft said:**
> 
If you have ever looked at an average Perl code that was longer than 100 lines that you didn't write yourself, it can become difficult to understand what it is doing because the syntax is quite cryptic. That's even true for your own code if you didn't look at it for a long time.


That can happen in any language, esp if you leava the code for some time and dont comment it. To be honest I havent used perl for anything besides playing around, I generaly use PHP as my system scripting language, though perl and PHP do look quite simmaler. I dont perticualy like PHP, but it works perfectly well so I havent bothered to learn anything else,

---

### Post by Mirge on 2009-08-26
> **hessiess said:**
> That can happen in any language, esp if you leava the code for some time and dont comment it. To be honest I havent used perl for anything besides playing around, I generaly use PHP as my system scripting language, though perl and PHP do look quite simmaler. I dont perticualy like PHP, but it works perfectly well so I havent bothered to learn anything else,

heh honestly I do the same... I use PHP for system scripting as well when I need to. That is likely changing now that I'm playing around with Python though.

---

### Post by WitchCraft on 2009-08-27
> **Mirge said:**
> heh honestly I do the same... I use PHP for system scripting as well when I need to. That is likely changing now that I'm playing around with Python though.

Nah, for me Python and Perl have become too boring.
It's simply too simple do to anything with them ;-))

I'm now heading more towards kernel modules and patches and I'm also starting to learn how to program directly on top of Xlib.

---

