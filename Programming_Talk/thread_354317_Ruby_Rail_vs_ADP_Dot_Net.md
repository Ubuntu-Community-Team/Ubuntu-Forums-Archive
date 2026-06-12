---
title: "Ruby Rail vs ADP Dot Net"
date: 2007-02-05
forum: Programming Talk
---

### Post by tc101 on 2007-02-05
I am a retired programmer.  I spent years in the Windows world, most recently working in ASP Dot Net.  I quit working about 3 years ago, and for 2 years didn't write a line of code.  Recently I have gotten interested in programming again.  I am running Ubuntu exclusivly now, and plan to stay totally off windows for at least 6 months.  I am very curious about the newest developments in programming and am starting to learn Ruby.  

That is all background.  Now the questions:

What are the advantages and disadvantages of creating a web site that hits a database using Ruby Rails and mySQL rather than ASP Dot Net and SQL Server?

I know there is a cost saving, since the software is free, but other than that, what are the advantages?  I have spent the day playing with Ruby.  So far I see a few improvements in a few commands, but nothing that is ground breaking or super wonderful.  Of course I am only getting started, so I know there is lots more stuff to learn.

I miss the Microsoft IDE and intellisense.  That saves so much typing and so much memorization.  Maybe there are similar products for Ruby but I haven't found them yet.

Anyway, what are your thoughts.

---

### Post by lnostdal on 2007-02-05
in many cases autocompletion is implemented at the level above the language; in the editor/ide .. 

when doing C, this provides it: [http://cedet.sourceforge.net/intellisense.shtml](http://cedet.sourceforge.net/intellisense.shtml) .. when i'm doing lisp - it is "built in" and provided via slime

now, for ruby i am not sure .. this page does mention autocompletion [http://wiki.rubyonrails.org/rails/pages/HowToUseEmacsWithRails](http://wiki.rubyonrails.org/rails/pages/HowToUseEmacsWithRails) .. and a google-search for "autocompletion ruby" mentions a couple of others, komodo for instance

---

### Post by tc101 on 2007-02-05
I just noticed my typo in the Title.  Is there any way I can now change ADP to ASP?

---

### Post by Mirrorball on 2007-02-05
For autocompletion, get the RadRails: [http://www.radrails.org/](http://www.radrails.org/)
It's an Eclipse plugin.

---

### Post by skeeterbug on 2007-02-06
> **Mirrorball said:**
> For autocompletion, get the RadRails: [http://www.radrails.org/](http://www.radrails.org/)
It's an Eclipse plugin.

It doesn't even compare to Visual Studio. What version of ASP.NET did you develop in? 1.1? 2.0? VS 2005 is just amazing. The built in webserver is really handy as well, and debug visualizers are a nice addition too. We are a Microsoft parter here, but I have been doing Ruby on Rails on the side since December of 05. Our website was built using rails and MySql.

When building a new application, Rails can be really nice. It is extremely picky about naming conventions, and even though you can use your own, it makes it really hard to work with. If you don't use MySql with it, you can run into some problems as well. Honestly the time you save in lines of code in Ruby are made up in .NET because of Visual Studio 2005, with breakpoints, debug visualizers, etc. We use a third party ORM mapper called LLBLGen Pro. It blows Active Record out of the water, plus you get intellisense to build your predicate expressions (WHERE clauses). Getting Rails on a production server isn't a fun task either.

I will be keeping our website in Rails for the time being, as we are too busy writing our core applications to really re-write it. However, I won't be doing a single site using Rails again.

About the money, SQL Server 2005 express edition is free (even has full-text, etc), at a 4GB data cap. It also has a really nice management studio (also free). You can do stored procs in C# now if you want to go that route (we use only LLBLGen though). Visual Studio can be pricey depending on the version, but in all honesty you get what you pay for. Just my 2 cents. Hope that helps.

---

### Post by gh0st on 2007-02-06
> **tc101 said:**
> I just noticed my typo in the Title.  Is there any way I can now change ADP to ASP?

I did wonder what ADP was I have to admit :) 

This is a bit off topic so I appologise in advance. 

I haven't used Rails but I did a lot of development work with ASP.NET for a few years and I liked it. I used to work for a Hospital that was a Microsoft Partner but since leaving there and playing with Python in Linux I decided to try Django and I think it's amazing. I can't compare it to ROR cos I've never tried ROR but in comparison to .NET it saves me tons of time. I didn't like the idea of things being automated at first, I'm a bit of a control freak at times, I got used to it though and I know exactly how my Django server works every bit as much as I understand the .NET Framework JIT Compiler and the ASP.NET worker process. So I'm cool with it now, as long as I know what it's doing I'm happy for it to go about it's business while I get on with something else. Creating database API's for your apps is great with Django. really quick, it generates the SQL you need and you can check it before running it. I have to be honest I don't know how it would cope with another database back end, I've tried it with MySQL, PostgreSQL and SQLite and all of them were easy. I suspect it wouldn't like MSSQL or Oracle.

I'm not saying Django is better than Rails or ASP.NET by any means, I just like it and I think you might wanna take a look. Writing code in Python is very easy to get used to especially if you've spent years writing VBScript for ASP like I did before .NET arrived :)

[http://www.djangoproject.com/](http://www.djangoproject.com/)

I don't know how Django would handle a production environment as yet cos I haven't tried it but I intend to ASAP. There are loads of big sites using it now, it was developed by some guys working for a newspaper and it seems to be very popular in that field. The Washington Post use it for their site so it must be pretty reliable. I reckon it's one to watch for the future.

Anyway, I'll let you get back discussing Rails now and stop changing the subject.

---

### Post by skeeterbug on 2007-02-06
> **gh0st said:**
> I did wonder what ADP was I have to admit :) 

This is a bit off topic so I appologise in advance. 

I haven't used Rails but I did a lot of development work with ASP.NET for a few years and I liked it. I used to work for a Hospital that was a Microsoft Partner but since leaving there and playing with Python in Linux I decided to try Django and I think it's amazing. I can't compare it to ROR cos I've never tried ROR but in comparison to .NET it saves me tons of time. I didn't like the idea of things being automated at first, I'm a bit of a control freak at times, I got used to it though and I know exactly how my Django server works every bit as much as I understand the .NET Framework JIT Compiler and the ASP.NET worker process. So I'm cool with it now, as long as I know what it's doing I'm happy for it to go about it's business while I get on with something else. Creating database API's for your apps is great with Django. really quick, it generates the SQL you need and you can check it before running it. I have to be honest I don't know how it would cope with another database back end, I've tried it with MySQL, PostgreSQL and SQLite and all of them were easy. I suspect it wouldn't like MSSQL or Oracle.

I'm not saying Django is better than Rails or ASP.NET by any means, I just like it and I think you might wanna take a look. Writing code in Python is very easy to get used to especially if you've spent years writing VBScript for ASP like I did before .NET arrived :)

[http://www.djangoproject.com/](http://www.djangoproject.com/)

I don't know how Django would handle a production environment as yet cos I haven't tried it but I intend to ASAP. There are loads of big sites using it now, it was developed by some guys working for a newspaper and it seems to be very popular in that field. The Washington Post use it for their site so it must be pretty reliable. I reckon it's one to watch for the future.

Anyway, I'll let you get back discussing Rails now and stop changing the subject.


This was some what on subject actually. We are programmers not XX developers. We use the right tool for the job. DJango had me until the last part of the tutorial, part 4 on generic views. The tutorial itself was awsome up until that point, at which I grew angry and closed Eclipse. DJango has a great ORM layer from what I have seen and read (we spend most of our time talking to the database, ORM is very important). It doesn't have MSSQL support, but that is ok, they have chosen 3 database platforms and hopefully they can support them, rather than trying to work on everything like Rails.

Google is going to be releasing a source code review system done in DJango. That might be a bit scewed though, because they hired the guy who wrote Python. Then again, what does that tell you about this web framework if the guy that wrote Python wants to use it? ;)

---

### Post by Mirrorball on 2007-02-06
> **skeeterbug said:**
> It doesn't even compare to Visual Studio. What version of ASP.NET did you develop in? 1.1? 2.0? VS 2005 is just amazing.
Was I comparing it to Visual Studio or suggesting it as a replacement to Visual Studio? I never wrote a line in ASP.NET, I don't even know what VS 2005 looks like. I just suggested a tool for autocompletion in RoR.

Moving on... I'm using Django for my latest project too and I'm enjoying it a lot. Writing Python code is so pleasant.

---

### Post by LordHunter317 on 2007-02-06
My biggest single issue with RoR is that it's support for !MySQL is poor, which is pretty offputting.  Most of my tasks are unsolvable with MySQL < 5.0, and at this point I'd just prefer not to use it.

---

### Post by skeeterbug on 2007-02-06
> **Mirrorball said:**
> Was I comparing it to Visual Studio or suggesting it as a replacement to Visual Studio? I never wrote a line in ASP.NET, I don't even know what VS 2005 looks like. I just suggested a tool for autocompletion in RoR.

Moving on... I'm using Django for my latest project too and I'm enjoying it a lot. Writing Python code is so pleasant.

Sorry I was asking the OP after that first sentence, there should have been a new paragraph.

---

### Post by gh0st on 2007-02-07
> **skeeterbug said:**
> Google is going to be releasing a source code review system done in DJango. That might be a bit scewed though, because they hired the guy who wrote Python. Then again, what does that tell you about this web framework if the guy that wrote Python wants to use it? ;)

Cool, I didn't know Google were using Django. I know they like a bit of Python at Google. It will be interesting to see if they extend the framework, that would be nice :)

---

