---
title: "Frontend/Backend Symbiosis"
date: 2008-01-18
forum: Programming Talk
---

### Post by Thund3rstruck on 2008-01-18
Ok, so I'm a bit confused. I have spent the last 5 years programming in the .NET framework (C#) for Microsoft enterprise systems. In that idiom the programmer selects a language of choice and leverages it in all areas of development (web, desktop, db, etc, etc) by way of the universal .NET framework (CLR). 

Using a dummy problem, suppose a cron task running on a linux server needs to downlad files periodically from the Internet, parse the files, and publish meta-data to a corporate database. 

On the UI frontend, there is a web management system for interfacing with the system as a whole. 

From what I'm reading it appears that I need to use 2 separate languages to accomplish this common task? One language to write the application running on the physical server and another to display the web UI?

So what is recommended? I began reading up on C for the physical server task but that language looks way too low level for what is needed. For the web I assume PHP is called for? 

Is there convergence amongst languages to bridge this divide between front-end and backend in the OSS community?

Thanks guys for taking the time to read this

---

### Post by CptPicard on 2008-01-18
First of all, the Microsoft marketese concept that you "pick one language and then leverage that across the whole domain" is bs -- it's Good that you have multiple languages to do the various bits and pieces of your system, because sometimes it is genuinely called for. Open standards come in when you need to communicate between the subsystems. You're presenting a sort of false dilemma that comes from drinking too much MS kool-aid. :)

That said, if you insist on using a single language, for this it would probably be either Python or Java. Both can accomplish everything in this system. Java is of course the more .NET-like of the two here, and is capable of building a really huge enterprise system if that is called for.

---

### Post by mathisdermaler on 2008-01-20
If you're trying to develop exactly the thing you described in a quick-and-dirty, I would say write the whole thing in PHP.  Besides web development PHP can also be used to do everything you are speaking of.  (As a short-cut you might appreciate, the fopen() command in PHP actually takes URLs beginning with [HTTP://)](HTTP://))  The main downside is that (when I last used it) there was no threading and no good debugger in common usage.

You could also use a complete Java solution (Java is quite similar to C# as you may know.)  This preferrable if you want a more maintainable solution.  The main downside of this is that java web/application servers are fairly complicated to set up compared to PHP or IIS/ASP.NET.  If you go down that route, open another thread asking how to set up a java servlet container and I'm sure you'll get lots of responses.

---

### Post by pmasiar on 2008-01-20
The whole universe of Unix/Linux is different. .NET lures you by providing one "universal" tool (if you only have a hammer, every problem looks like a nail, if you have chainsaw...)

In Linux instead, you have "set of smart sharp tools" which do one thing, and do it right, so you can use them without fighting with them (if knife is sharp, you can use it without thinking, only if it is dull you would notice it).

So I am not sure which "two" languages you need to use, because I use more than that: SQL to access data, Python to process them, HTML and CSS to display them, and templating system to generate HTML pages. And every language has its place and skipping over it (ie doing all in HTML, ignoring CSS) is just such a waste of time.

Python has one nice templating system, Kid, where internal template language is Python, so you don't have to learn some custom half-language fot templating expressions. It comes included in excellent Python web app framework, TurboGears (together with all other goodies, like object-relational mapper, and development web server which autoreloads modules after changes).

---

