---
title: "Networking project, language suggestions?"
date: 2007-02-06
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-02-06
I'm working on a project for my networking class, and I've decided on a web-based calendar app to replace the college's current one.  I want to allow for professors to create classes and have them hosted on a central database.  Along with creating classes I want to allow them to check for interferences with other classes people in a given field of study might also be taking to prevent these class times from overlapping.  Here's what I'm thinking it should look like:


[FONT=Courier New]==============================
|~~~~~~~~~|~~<__February__>~~|
|~|days~|~|_~|~~|~~|~~|~~|~~|~_|
|~|=====|~|_~|~~|~~|~~|~~|~~|~_|
|~~~~~~~~~|_~|~~|~~|~~|~~|~~|~_|
|~|int.1|~|_~|~~|~~|~~|~~|~~|~_|
|~|====.|~|_~|~~|~~|~~|~~|~~|~_|
|~~~~~~~~~~~~~~~~~~~~~~~~~~~~|
|~|int.2|~~~~~~~~~~~~~~~~~~~~|
|~|====.|~~~~~~~~~~~~~~~~~~~~|
[U]|~~~~~~~~~~~~~~~~~~~~~~~~~~~~|
[/U][/FONT]
[FONT=Courier New][FONT=Verdana](hehe i like ascii art...)
(sorry about all the tildes, the extra spaces were deleted :-( )

I'd like for the days to be check boxes and the interferences to be pull down menus with every time one interfering class is selected another pull down box is created underneath it.  I'd possibly like for the calendar days themselves to be clickable and have a small popup window with the classes already scheduled in that day show up.  I'd also like the months to be scrollable (change from Jan. to Feb. & back again) and I'd like to be able to do this without reloading the entire window/page.

My question is which language should I write this in?  I'm fairly skilled in C, Java, & Python and was looking at [Jython]("http://www.jython.org/Project/index.html").  However, I was unsure if this required a runtime environment on everyone's computer like jsp or java applets, in which case I didn't want to do it.  I might be able to use server-side python scripts, but I doubt that would do what I need.  I could probably pick up CGI/PHP (my most likely choice) but I'm on a deadline.  Languages come fairly easy to me so I don't think it would be a problem, assuming it would do everything I wanted.  I also plan on using MySQL to store everything.

Anyone have any comments/suggestions?

[/FONT][/FONT]

---

### Post by amohanty on 2007-02-06
If you know python, take a look at [zope]("http://www.zope.org"). Its a web app server + dev framework rolled into one. It has 'products' which can be installed and configured for use. Has a templating language (metal) and embedded extensible tag library (dtml) and a very active community. You can put up and app very quickly with it (if you have wokred with python - you know how rapid stuff can be). 

The downside is that the app server (zserver) is not on par with servers like tomcat, jboss and the like. And some cofiguration is required to get it to perform decently. Zserver behind Apache + FastCGI and cgi are available but they are generally slower than just doing some sort of url rewrite or virtual host solution.

HTH
AM

---

### Post by pmasiar on 2007-02-06
> **mrpeenut24 said:**
> I'm working on a project for my networking class, and I've decided on a web-based calendar app to replace the college's current one. 

I am not sure if you need to write it al from the ground up, but sourceforge is littered by calendar applications - maybe adding new feature for some of them would count too and be more useful. Skolelinux and Edubuntu (and others) are oriented towards schools apps - they might know more).

> which language should I write this in?  I'm fairly skilled in C, Java, & Python and was looking at [Jython]("http://www.jython.org/Project/index.html").  However, I was unsure if this required a runtime environment on everyone's computer like jsp or java applets, in which case I didn't want to do it.  I might be able to use server-side python scripts, but I doubt that would do what I need. 

You have it mixed up: JSP runs on server, unlike java applet.

What you want looks to me like AJAX: web-based javascript app. Take a look at Google calendar to see what is possible :-)

Turbogears would be my second choice (first being adding a feature to an existing app).

---

### Post by mrpeenut24 on 2007-02-06
Yeah I'm pretty sure I need to build this from the ground up, and I was planning on hosting it on my own server.  I'll ask today and find out whether or not it should be.  This is also going to be my senior project, though, so it may need to be.

> **pmasiar said:**
> You have it mixed up: JSP runs on server, unlike java applet.

What's the other java internet application?  I think it's the java web start (.jnlp).  Maybe that was what I was thinking of.

---

### Post by lloyd mcclendon on 2007-02-06
you should definately look at google web toolkit for this.  you write code similar to a swing app (you've done this before right), and send it though googles compiler which turns it into a bunch of crazy unreadable javascript.  what you're left with is a nice ajax application that runs in ie6 and firefox.  there's a fake browser that allows you to run it in hosted mode for debugging.

[http://code.google.com/webtoolkit/](http://code.google.com/webtoolkit/)

if you're working with databases in java, learn how to use hibernate & hibernate annotations.  it's not easy at first but after you figure it out, it is very powerful and will save you a ton of time that would otherwise be spent with tedious sql statements.

---

### Post by mrpeenut24 on 2007-02-06
Yeah I've done swing before.  I believe I'm going to do this in CGI/Python scripts or PHP/MySQL.
My professor is trying to discourage me from using PHP/MySQL, but I believe it's just because it would be something else to learn, and is difficult to maintain.  He thinks I should use CGI/Python instead.  However, he says I can try it.  I'd really like to learn it, and wonder if it would be better than just using Python scripts.  Would Python be able to do everything I need?

---

### Post by mrpeenut24 on 2007-02-07
Actually, I might use CGI/Python with MySQL for the databases.

---

### Post by pmasiar on 2007-02-07
> **mrpeenut24 said:**
> My professor is trying to discourage me from using PHP/MySQL, but I believe it's just because it would be something else to learn, and is difficult to maintain.  He thinks I should use CGI/Python instead.  However, he says I can try it.  I'd really like to learn it, and wonder if it would be better than just using Python scripts.  Would Python be able to do everything I need?

yes, Python lets you do everythin java does, in half the time and 1/3 of the lines :-)

For intro, look at thread  Hello Web - simplest web app in python: [http://ubuntuforums.org/showthread.php?t=332041](http://ubuntuforums.org/showthread.php?t=332041)

then you can decide to continue with either (1) htmltmpl templating for simple solutions or (2) Turbogears or Django if you need real web framework.

---

### Post by mrpeenut24 on 2007-02-07
Yeah, I've done some simple web-python scripts.  Should I just forget the whole PHP/MySQL idea and go with python?  Should I use MySQL with Python?  Am I going to need templates for the calendar (probably a stupid question)?

---

### Post by pmasiar on 2007-02-07
> **mrpeenut24 said:**
>  Should I use MySQL with Python?  Am I going to need templates for the calendar (probably a stupid question)?

1) you can use SQLite - it is database library (not a server). Simpler for web app which has only one user at a time (web). And it is SQL, so you can switch to mySQL later if you need.

2) yes, you do need templates - you want to place your HTML outside of your code. Read [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) why.

---

### Post by gh0st on 2007-02-14
You should really check out Django if you want to do something web based with Python, it is amazing IMO.

[http://www.djangoproject.com/](http://www.djangoproject.com/)

The Object-Relational Mapper for building automatic database API is pretty special. You can link to a MySQL database easily and quickly, you get a built in "Admin" area if you want it and it's open-source so there are loads of mods and extensions available from the community.

I read the tutorial, which only took 2-3 hours or so and by the end I had a pretty usable web app with full database integration and a pretty slick admin interface, it was only small but not bad for 2 hours work. I really would recommend it.

Google are starting to use it for some projects and they even employed Guido van Rossum (the creator of Python) to do some work with it.

There is a free book (not quite complete yet I admit) - [http://www.djangobook.com/](http://www.djangobook.com/)

As you can tell I am a bit excited about it, I should probably lie down for a bit I think I'm starting to foam at the mouth :) ;) 

I haven't used Turbo Gears so I can't compare them, Django could have a big future IMO. There are lots of other web technologies out there though ans this is just my personal view.

Have a look at the site, you might like it

Dan

---

