---
title: "What language/s to use to build Property Managment application"
date: 2012-10-22
forum: Programming Talk
---

### Post by chipppy on 2012-10-22
Good Morning

Noob here.  I have dabled a tiny bit into programming over the years but never really got deep in to it.

My wife runs a Residential Property Managment Business (rents out houses.  She is only a small business 3 people in total, like many similar property managent businesses.  She doesnt have the resources (moeny) for a commerical property mamangent software app like [**[B]*REST***[/B]]("http://www.rockend.com.au/pageREST.aspx?category=1&element=109") or [***Console***]("http://www.console.com.au/").
I made up a heaps of spreadsheet for my wife to use to run her business from and it has all work great but she has been on my case for a few years to go the next step.  This is a little beyond my skills but hey I have decided to take on the challange and actually really learn a new skill (programming) while building a better more intergrated app for her.

Now my question is what language/s to use to write this all in.
Here is the basic outline of what she would love to have at the end of the day.  Please feel free to correct my mis assumptions or outright mistakes here

**Holder of the data**
Database of some sort to hold all the important info i would assume.  She has approx 230 houses on the books.  In spreadsheet terms 230 rows but about 1000 coloumns.  Here data security is the most important thing as it needs to be 'auditable' and be able to show that noone has fiddled with the data.  
Which would be the right database system to use.
Needs to have things like
[LIST]
user accounts
record info on who, what, when changes were made, etc
keep picture, photos, video, scans, etc aswell as data entry
have muttliple user logged on at same time
like to have remote access (work from home/across web)
be able to lock a 'row' so that it cannot be modifed.  The idea here is to log out an inspection, complete the inspection, log in the results a day later type thing
probably a lot of things I havent thought of[/LIST]
Lets allow for say 500 propertys and 6 different users.  This allows her business to double in size.  i would assume that as well as user accounts there would need to be user privilage levels(eg like ubuntu guest, user, and sueruser)

**Interface to the database.**
I was thinkking some sort of webbased interface.  This way she could use it across a few different devices (desktop, table, smartphone, etc).  We are a big believer in the KISS pricipal (Keep It Simple Stupid).  Therefore nothing to fancy but still has the flexiblity and power to do everything she wants to.
[LIST]
Property entry, routine, exit inspections
Owner lists
Tennant Lists
Payment details both tennat (in) and owner (out)
Normal business reports (profit/loss, banking, etc)
and much more
[/LIST]
She would love to be able to do her inspection on her tablet and or smart phone (love that thing more then me I think), and then have it just update the database when she gets back to the office (thats a long way off, if ever, but worth thinking about at the start of the project)

Or would using something like LibreOffice Base do the job just as well.  I am up for any suggestions

I have done some research and only found a few open source Sales property managment apps.  Mostly in Drupal.  If you happen to know of a good open source rental property managment app, please link the site so I can take a look.

What do you people thing is the best way for me to go, interms if language/s to use.  I enjoy a challange so dont be scared to suggest something a little harder initially but worth the effort in the end.

Cheers
chipppy

---

### Post by Tony Flury on 2012-10-22
I would say for something like this - what languages are you comfortable with ? In theory any Turing complete language can do this job, so crucially the decision is down to development speed and ease of maintenance, and maybe performance (but only worry about that later - when you know which bits of your application are slow).

If you want to go web based then PHP/HTML/CSS is a good combination with an SQL databse to hold your information - assuming you have a server to host this on. Alternatively you could do a python implementation instead of PHP. 

If you don't know those languages, there is nothing to stop you doing a web based application in C (I speak from experience), but it is not the easiest of things to do.

Have a look at your database design - and don't just ape the current spreadsheets - 1000 columns might be ok for a spreadsheet (in that the spreadsheet can handle it), but it doesn't work too well as a database structure - you will almost certainly find you need to split the rows up into multiple tables.

From what you say security is critical - so whatever language you use, build that in from the beginning - trying to build security in once the application is complete leads to disaster (one example : MS Windows). Also security will be at least part based on your server - does it support https for instance - or have a decent user authentication/admin system ?

To be honest - a simple single user system sounds fairly easy - it is the multi-user stuff you will have fun with i think.

---

### Post by chipppy on 2012-10-22
Good Morning

Thanks for the reply

My experience with any specific language (in this project terms) is none.  I have played a little with Java and C++ but still a complete noob really.
First point is I perfer open source so I would prefer to stay completely open source (language, IDE, Server, etc)
Therefore all language are new to me and therefore all the same terms of development speed.  This leave ease of maintenace as the major point there.

The app dosnet have to be web based.  It just has to be able to server to and from the web.  Example is rent payment.  Currently all electronic transfers.  Each day wife downloads her bank statment and imports into a spreadsheet.  A Macro then moves the tennants payments from this spreadsheet to various other spreadsheets, which inturn does other stuff.
The remote work via the web is a bit of a dream thing really but if I allow for it at the start then less issues later if she wants it to become reality (think that more for a pro programmer then me)

DB is an interesting one.  I have been doing a little research into different DB languages.  Theres lots.  Which of the open source DB language is best to use?
Big thanks for the hint of keeping the table sizes smaller.  I would have fallen for that mistake without the hint.

Sever.  Dont have one at the moment, but I will make one once I start.  This does lead to the question of which server should I use, taking into account the security and connection requirment.

I suppose one of the questions that need to be answered is design.  So my thinking is a modular design.  Build a base module that other bits can be added to later, without having to rewrite the base.  Is this possible and is this a good design or is building the one intergrated app a better design.  
Also there is platform while I personally choose to use Linux, in the interest of open source (including OS) does any specific language cause issue whenusing the app on a different OS?

Can this affect which lanuage is best to use?

Wow i never thought so much to think about just to choose a language to use.


Cheers
Chipppy

---

### Post by Tony Flury on 2012-10-23
if it were me i would use python and SQLlite - but only because that is what i am used to.

I would also use GTK to build the GUI - becuase again - I am used to that - but that would not be web based.

Python and GTK are cross platform - as is sqllite (i think) - although i have only used any of them on linux.

A modular or OOP design is the best i think - but if you have never done any s/w design before it might take you a while to get the OOP level of design.

private message me if you want.

---

### Post by r-senior on 2012-10-23
Java EE is made for that sort of application. It has all the architectural support and security frameworks necessary for large-scale applications with vast numbers of users. It just has a major learning curve.

If I was developing it:

MySQL database with Glassfish application server
EJB3/JPA for the database integration
EJB3 (or Spring) for the business model and transactions
AOP (using EJB interceptors or Spring AOP) for auditing
JSF or Spring MVC for the web tier
JAX-RS/JSON web service into the business model to expose as web services
iOS or Anroid apps for tablet/smartphone access via web services

All of the Java EE code is completely cross platform. The key to making it manageable is getting the tiered architecture right.

It's a lot of work and a lot to learn. The Java EE 6 tutorial gives a flavour:

[http://docs.oracle.com/javaee/6/tutorial/doc/](http://docs.oracle.com/javaee/6/tutorial/doc/)

---

### Post by CptPicard on 2012-10-23
I would probably go for something like Rails, as this sounds like a fairly small application. The Enterprise Java stack is huge and completely unmanageable for a beginner.

---

### Post by llanitedave on 2012-10-23
You might look into [Django]("https://www.djangoproject.com/").  It's well documented and doesn't demand a lot of up-front expertise -- although if you have the expertise you can build some terrific apps with it.

---

### Post by oldfred on 2012-10-24
I do not know Django but think it may be worth investigating.

My goal was to learn python, I knew some sql and before retiring 6 years ago used MS Access a lot.  

So I wanted to build some apps in Linux. But MS Access does combine databases, queries, reports and the tools to create all those in one application. In Linux they all are different and each has many choices.

sql db - sqlite is good to start and learn, but you may want postgres or mysql

[http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL](http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL)

You may want tools to access sql tables directly. With swlite I use SqLite database browser & sqliteman to test sql statements.

I use python but needed an editor. I use geany or spyder, but everyone has a different opinion.
Too many choices but many are free so you can try them
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

I am still experimenting with gui. Some of the best advice was to separte gui from database stuff in python and I have used almost exactly the same python database app, sql tables, but experimented with gtk, qt and now starting HTML.

Gui & editors:
[http://wiki.python.org/moin/GuiProgramming](http://wiki.python.org/moin/GuiProgramming)
The Python GTK+ 3 Tutorial
[http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html)

There are tons of python examples for just about anything, but in bits and pieces.

Someone posted this on an accounting app.


> 
 The accounting needs of SQLite.org are likely much simpler than those of LWN.net. Nevertheless, it seems worth mentioning that we've gotten along fine here since 1995 using a database with a very simple schema and a handful of CGI scripts written in TCL. This system keeps track of client contact information, invoicing, various bank accounts, payroll and expenses, and then it generates a general ledger, income statement, and balance sheet which we print out and take to our accountant once a year at tax time. The key descriptor of the system is "simple". There are no graphics. Just some <form> and <table> elements mixed with a few SQL statements. The whole thing took about one day to hack together nearly two decades ago, and apart from minor adjustments now and then (ex: conversion from PostgreSQL to SQLite sometime around 2002) it has served us well with a minimum of fuss.


And this on database, I am used to just going in and fixing something, but if you need audit-ability you have to have more id, dates & info on who is making changes built into your tables.

> If I were to build a small business accounting system, I'd start with his and re-implement it using modern languages and a modern UI. And the first premise of the database system would be as already mentioned: every record inserted must include a record insertion date/time, the record this one retired (or null if it's new), a record retirement date/time, the record that retired this one (or null if it's current) and who did each deed. Nothing is ever deleted from the database or updated in it: 'DELETE' and 'UPDATE' don't exist. Call it 40 bytes per record; in 100M records, that's all of 4GB: mice nuts compared to the bit trail you'd get. And accounting is all about traceability.


---

### Post by chipppy on 2012-10-24
Good Morning

Huge thanks for all the advise.

r-senior:  I looked into Java EE and wow it is a monster for a noob like me.  From what I read it is more suited to B I G apps like monster corperations, banks, goverments and the like.  My app will be for little sole traders, up to maybe 5-6 employees.  Big thanks for your input as the advice the tiers archutieture is going to be invaluable.  The main issue here is me.  Im a noob to porgramming and something like this is a huge project for me.  therefor eI would prefer to use the 'easier' languages for a noob over the best langugae for a pro developer.  Though I am up for a challange if it is just 'dumb' to go any other way

SQLite v SQL.  Personally I think SQL over SQLite.  To this point I think PortgresSQL over MySQL.  Reasoning is 2 part
[LIST]
[*]Portgres appear (my reading) to be more about compliance with the standards at some cost of ease of use (though ease of use appears to have been mostly sorted in later versions).  Standard compiance is important to me personally as it is a big part of my normal job.
[*]PortgresSQL appears to be more true open source both in source code and community input to the project then MySQL.  Openess to help from all is iomportant as that is a major thing that I will require on my journey though this project.[/LIST]

Anyone have any thought if chossing PortgresSQL is a really bad idea.  If not then I will lock in Portgress as my DBase.

The gui side of things.
I dont specifically have to make the gui web-based.  The web-base part is the so that the application can interact with the web.  EG to download banking statments (and then manuliplate that data), post rental property available ads on the net, recieve online application for the aformentioned ad, etc.
I would like to allow for some sort of working from home, or remote site, and be able to work over the internet to that effect (really I think that is a big wish more then reality but I want to allow for into in the language I choose)
This means that using something like GTK+ is fine.

Therefore people the GUI language has only to allow for net communications it doesnt need to be net based.  Ease of use for a noob is pretty important here.

Whats your thiought as to the GUI language allowing for PortgresSQL (unbless there is a big negitvie to PortgresSQL)

Cheers 
chipppy

---

### Post by memilanuk on 2012-10-24
I'm fairly green at this stuff myself... get started on a project and then get side-tracked ;)  But if you are interested in this being open source, able to use whatever database you want, and web enabled would be nice but not strictly necessary... perhaps web2py might be an option.  It uses its own database abstraction language/layer (DAL) for accessing whatever kind of database you want - sqlite, mysql, postgresql, etc.  (might be easier to build initially with sqlite for testing) and it comes fairly self-contained - you can run it from a USB thumb-drive on Windows and it will pop up a small but functional web server to run the app.  Worth checking out, at any rate.

---

### Post by r-senior on 2012-10-25
Java EE is a monster and I would never pretend otherwise. It's a lot better than it used to be though and can easily be considered for a less than enterprise scale project.

You did say this ;) > dont be scared to suggest something a little harder initially but worth the effort in the end

By the time you've written a database creation script, written a pile of data access classes, got bogged down in maintaining one-to-many relationships, written lots of transaction management, rolled your own validation and tried to write a web service on top, you could have learned Java EE and ended up with something a lot more flexible and stable.

CptPicard's suggestion of something like Rails is a good one. Or Groovy/Grails. Any established framework is better than none. Coding this down to the bare metal is going to be harder in the long run than getting to grips with some sort of framework I think, whether that's Java EE or something else.

Things like database choice shouldn't matter if the architecture and toolset is good. You should be able to switch without any impact on the tiers above. Choosing a framework and language you are comfortable with is more important IMO.

---

### Post by trent.josephsen on 2012-10-25
In addition to the other good advice you've gotten so far, I'd just like to add that if I were working on a project like this, which I am, I'd use Python, which I do. Not because it's my strongest language, but because it allows rapid prototyping, comes with good documentation and a large standard library, and provides all the nice features that make it easy to go from a high-level design down to the implementation details without losing focus.

As regards the DB engine, I'd suggest you start with SQLite even if you eventually switch to a bigger system like MySQL or Postgres. The reason is that SQLite makes it really easy to get started without taking the trouble to set up a server with user accounts and passwords and other complications. It also makes it really simple to back up the data in the database or copy it to another machine -- just copy one file and you're done. Bigger DBMSes have other advantages, but if you don't already have DB admin experience it's just going to be a lot of stuff to learn and a huge up-front obstacle preventing you from getting started on the real project. If you're careful[1], you may be able to switch from SQLite to Postgres or whatever by changing only one or two lines of code, when you're ready to do so. Which brings me to my final point...

The important thing, and probably the most difficult for you as a new programmmer, will be designing it, not coding it. If you're *not* careful, you'll end up with a system that only partially works and is too much of a mess to fix. You don't need to have a software engineering degree or anything, but plan to spend a significant amount of time, like 50% or more of the total project, just *thinking* about how to organize it and not actually doing so. If you have a good design, coding should go quickly; if not, you'll find yourself staring at a screen wondering what the next step should be. That means you tend to implement the first thing that comes to mind, which is rarely a good idea.

Of course, feel free to ask here if you have questions about either design or implementation; there's a lot of skill represented on this forum. [This recent thread](http://ubuntuforums.org/showthread.php?t=2072082) might have some preemptive advice to keep in mind.

I'll leave you with a thought from Fred Brooks of *The Mythical Man-Month*:

> Plan to throw one away; you will, anyhow.

Meaning you aren't going to go straight from nothing to finished product without backtracking a few times. You'll probably restart from scratch at least once (because, believe me, your first idea is going to be crap). This is one of the reasons I recommended Python: when you realize your codebase is going all to heck, it will take you much less time to rebuild it than with many other languages (although I can't comment on Ruby; total lack of applicable experience there).

[1] Use an object-relational mapper like Perl's DBIx::Class to avoid writing straight SQL.

---

### Post by Tony Flury on 2012-10-26
A good first start at design is to write a simple set of sentences which state what your application will do - for instance :

The system will allows a user to add a new property to the list
The system will allows a user to view a list of properties ...
etc 

Once you have written all of these sentences - underline the nouns, these are good candidates for objects (or in procedural terms, the data structures) or possible attributes on objects (data items in structures).

Draw a box around each verb, and work out which object that verb applies to - these verbs are good candidates for methods (or for proedural coding - they are functions which operate on data structures).


It wont be perfect - but it should allow you to make a start on your design.

---

### Post by trent.josephsen on 2012-10-26
I'd like to clarify something I said here somewhat without thinking:

> **trent.josephsen said:**
> plan to spend a significant amount of time, like 50% or more of the total project, just *thinking* about how to organize it and not actually doing so.

This is primarily applicable to someone who already knows the language they're working in. Someone new to programming would likely spend a majority of their time just learning the language and tools, which is not accounted for in the above quoted 50%. Point is, when you're getting started, you don't have to feel like you're doing something wrong because code doesn't flow freely from your fingertips. How long it takes to get to the point where you're not continually checking references to do basic stuff varies depending on the language.

---

### Post by chipppy on 2012-10-26
Good Morning

Firstly I would like to redirect the thread back to the question of which languae/s verus some design post.  Desgin is my next question and I feel it would be better via a new thread (though I will like it to this one so others can follow my journey).  This said I feel there are some design issues that I dont understand at this point that affect the outcome of the language choice.

I have been researching r-seniors idea of Java EE (and being scared by the monster that appears to be Java EE).  This has raised a lot of question in my mind as I dont understand a lot of the architecture of the total application eg (stealing from r-senior first post)

[I]Application server
Database integration
Business model and transactions
Auditing
Web tier
Web service into the business model to expose as web services
Tablet/smartphone access via web services[/I]

I dont realy understand all that, being honest.  I am not sure if that is all the bnits I will need or if there is more.  This leave me with the question do I need to choose a language with a solid framework (for my application) over one that is ease for a noob.  As I dont know or understand frameworks I would also need your assistance in which framework/s to use.

eg a lot of recommendations for PHP/Python/Ruby and Java in there aswell.  I read a lot (here and other threads) about speed of getting the application up and running along with protoype testing.  To be honest spped is not really there.  Im a noob and this going to take so time.  I understand and accpet that.

So final question which of the 4 languages mentioned Ruby/Java/Pthyon/PHP would have the most solid framework/s that will allow a noob to focus more on the real stuff (User doing thing) and not just the getting things to talk to each other, along with which framework would I use for the differenet parts of the application?

Application server
Database integration
Business model and transactions
Auditing
Web tier
Web service into the business model to expose as web services

Cheers 
Chipppy

---

### Post by SuperCamel on 2012-10-26
Java, Python and PHP are all used in large scale applications by well known organizations. Honestly, they would all be well suited for this job.  They do have some minor differences but they will ultimately achieve the same goal. Learn one language inside out and you'll be good to go. 

Do you intend to use this application on mobile devices or tablets? If so, Java might be your best choice. Will it be a web based application? In that case Python and PHP are both great for server side scripting. If it's just going to be a plain old desktop application then your language of choice doesn't reeaaally matter at all, but I wouldn't recommend C or similar lower level languages. They are slower to develop with, they are more prone to having quiet bugs like memory leaks or whatever and it sounds like this project doesn't need to efficiency or lower level functionality that they provide.

---

### Post by chipppy on 2012-11-01
Good Morning

I have been do a fair bit of researching into the various languages suggested.  I came to Java using Java EE as per r-senior suggestion.  
The reason:  Even though I looks like a monster and a lot of learning (read as probably a lot of mistakes and start agains), it has a lot of structure (framework) prebuilt along with a lot of requirments to have things correct (verification to meet specifications) before they can be used in Java EE.  

This framework and verfiication processes hopefully will point me in the right direction to build a quality app and also learn good coding practices along with getting a better understanding of it all (as opposed to my current adhoc methods today).

I am not dropping other languages as this experiment in Java EE may still turn out to be a mess but I think I'll try it first and see where it leads me.  If all else fails I can [I]throw this one away[I] and try another language.  No learning is ever a waste.  Learning the what doesnt work leads can only lead to learning what does work
My next step is basic design of my Rental Property Managment App which is a new thread.  
I will do some design work prior to posting the new thread
I will post a link in here to the new thread incase anyone wants to follow me on my journey in the future.

Thanks heaps for all the suggestions and help.

Cheers
Chipppy

---

### Post by trent.josephsen on 2012-11-02
> **chipppy said:**
> No learning is ever a waste.

Very true. :)

Best of luck.

---

### Post by chipppy on 2012-11-02
Good Morning

For next thread in my journey [click here]("http://ubuntuforums.org/showthread.php?t=2079946") 

Cheers
chipppy

---

