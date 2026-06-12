---
title: "Python and commercial stuff, would it work? why not?"
date: 2006-02-22
forum: Programming Talk
---

### Post by sapo on 2006-02-22
yo lads, :mrgreen:

I m currently working in a very very small company in brazil and we develop commercial software, like those used in small stores to control stock, cash, and all that crap.

Currently we have 2 versions of our software: 
The best (and oldest) one was made with clipper 5.2 and runs on MSDOS and linux (using flagship under linux) it have a lot of features and work as it is supposed to.

The second (and worst) runs on windows and was made in delphi with a stupid database named ADS :-# 

We are starting a project to remake the windows version and try to make it have all the features that the clipper version has, we just started the brainstorming but soon we will start rewriting stuff.

So where the hell is python on this? I started here 5 months ago, and i m a linux addicted and hate everything about windows, i mainly code php and right now i m making a lot of server side scripting with python, backup and restore tools, database converters, etc :twisted: 

So i thought, a lot of people use the flagship (linux) version of our old software, and it works best, is faster and more stable, so i NEED to convince my boss to make a linux version for our new graphic version, some stuff is already decided:

1 - Database will be firebird (cause its free and most of our clients cant pay a proprietary database)

2 - The database server will be linux too and run samba + firebird

3 - The linux version will be written on delphi 7 (thats what we have right now, and thats what our programmer knows)

But i want (and i will) convince my boss that we need to have a linux version, cause a lot of clients run linux and they like it because they can trust on it, we almost dont have any problems on our linux version, but the windows version is always corrupting the dabatase and stuff like that.

And i was thinking if there is any way i can make a linux version of our system, it would be great if we could just write once and compile in both windows and linux, but that is a complicated task.

I ve started with pygtk and i m finding this stuff very easy, and i m using kinterbasdb to make python talk with firebird and its running perfect.

I know that pygtk doesnt have any rad, but i m a code freak and i dont mind coding everything by hand, i know that there is that lazarus that is a delphi like, but honestly, delphi sux.

So what you guys think? is it worth a try? i mean, making something like this in python?

I think that the problems will be mainly GUI and i was thinking that reports will give me some headaches too, but i also think that python can write pdfs cant it? i could just write ou a pdf as a report and call xpdf to read it.. would it work?

Anyway.. is it worth a try?

My boss doesnt even understand what is python, but i have credits with him, everything i made till now worked as it was supposed too, so when he asks me to made something i just say "ok, i can do it".. and he doesnt care how i do it if it works.

If you guys have any suggestions or ideas, please let me know.

thanx.

---

### Post by ebash on 2006-02-22
Using a scripting language is probably the way to go since you don't need to bother too much with porting the application. Also development time will be shorter.

I have no experience with python but I do with perl. I was quite surprised with the win32-gtk bindings for perl. I was able to 'port' a perl GTK application I made without any code modification. If python has also win32-gtk bindings then you will be set.

Pygtk may not have a RAD but I'm sure that there is a binding for the glade library. I strongly suggest that you create you GUI with glade.
The advantage with glade is that you can then change your programming language without any effort.

Since you are skilled with php you can also take a look at the php binding for GTK. There's even a brazilian community!

[http://gtk.php.net/]("http://gtk.php.net/")
[http://www.php-gtk.org.br/]("http://www.php-gtk.org.br/")

---

### Post by LordHunter317 on 2006-02-22
[QUOTE=sapo]So where the hell is python on this? I started here 5 months ago, and i m a linux addicted and hate everything about windows,[/quote]Then it's likely you won't produce a good Windows version.  You should learn to at least cope with your operating system and understand it.  At the very least that point, you'll hate both equally.

> 1 - Database will be firebird (cause its free and most of our clients cant pay a proprietary database)

2 - The database server will be linux too and run samba + firebirdIf you're not going to embed firebird, there's no point in running it unless you were based on Interbase before (and you're not).  It has some pretty terrible limitations that are PITA to work around, generally speaking.

If you're going to run a DB server, postgresql is almost inarguably a better choice.

> But i want (and i will) convince my boss that we need to have a linux version, cause a lot of clients run linux and they like it because they can trust on it, we almost dont have any problems on our linux version, but the windows version is always corrupting the dabatase and stuff like that.That arguably has more to do with choice of database and program architecture, not the operating system.  Windows is perfectly fine for this sort of things, and you shouldn't be pushing the operating system.  Ask what operating system your clients what the solution to run on.  If they're happy with Linux, great.  If not, you're not providing them with a good solution if it doesn't run on what platform they want.

> So what you guys think? is it worth a try? i mean, making something like this in python?I probably wouldn't.  You can try.

My main concern is python would be the lack of static type safety on a project like this.  And while the code may not care and it may be a feature there, the database cares very, very much.  And seeing as I have enough problems getting the typing reliably consistent in a static language...

> I think that the problems will be mainly GUI and i was thinking that reports will give me some headaches too, but i also think that python can write pdfs cant it? i could just write ou a pdf as a report and call xpdf to read it.. would it work?Reporting is usually substantialy more complicated than this at every job I've ever worked for.

Depending on what they want, the best solution may be to have the database server run a web server and run a web-version of Crystal Reports.  As crappy as it is, Crystal is the de facto standard, and can do much more than what you'll likely to cook up.  Obviously, if that's not necessary, it's not a problem.  But I'd bet money it is.

---

### Post by LordHunter317 on 2006-02-22
[QUOTE=ebash]Using a scripting language is probably the way to go since you don't need to bother too much with porting the application. Also development time will be shorter.[/quote]Doubtful.  Design will likely dwarf this, since to do it correctly sounds like an all new design is required.  Clearly at least the Windows version is poor, and everything I've heard about clipper makes it sound like a good design is nigh-impossible in it.

---

### Post by mariuz on 2008-11-21
if you will go the python way 
Pavel Cisar has done amazing progress on the driver (works with firebird 2.1)
[http://www.firebirdnews.org/?p=2194]("http://www.firebirdnews.org/?p=2194")
als i loved his python presentation at the firebird conference 2008
in fact i want to learn python after i saw that 


also if the app is written in delphi i highly recomend it to port on lazarus ide 
it works with firebird very well 
[http://mapopa.blogspot.com/2008/10/upgrading-to-lazarus-0.html](http://mapopa.blogspot.com/2008/10/upgrading-to-lazarus-0.html)
[http://mapopa.blogspot.com/2008/05/using-lazarus-ide-with-firebird-in.html](http://mapopa.blogspot.com/2008/05/using-lazarus-ide-with-firebird-in.html)

you don't need to rewrite the app you just need to fix it to work on linux (compile bugs)

---

### Post by kknd on 2008-11-21
Hi, I'm starting a small company on Brazil too (SC). Now, we develop small stock management and stuff like this.
We are using C (20%), Lua (80%), GTK and Postgresql, plus some homemade libraries (mainly bindings and l10n and i18n).
We're happy with the results (easy to develop good quality applications).

I think that scripting languages like Python and Lua are good choices for application development, but make sure that you design the whole application before coding, because its much more hard to do code refactoring in dynamically typed languages, and if you don't document it well, its gonna be hard to understand it on the future (ex.: in Lua, you don't define a type or "struct" and then use it, you create fields at runtime).

---

### Post by Kazade on 2008-11-21
We use Python for most of our projects where I work. But when we needed a desktop application we didn't use Python+GTK because of the difficulties packaging it properly (remember, GTK doesn't come with Windows so you need to install all the libs and what not). Then trying to get it to work with Py2exe seemed like to much of a mission so instead we went with Java+Swing and everything works fine. PyGTK is cool, just make sure you can package it and the clients don't mind installing the GTK runtime etc. (some IT people are really strict on what gets installed on their machines).

---

### Post by pmasiar on 2008-11-21
> **kknd said:**
> its much more hard to do code refactoring in dynamically typed languages, and if you don't document it well, its gonna be hard to understand it on the future

It is not, all you need to do to write better unit tests. They will also "explain" API, and have side benefit to help design better API. Tests are good for you and your app! 8-)

---

### Post by kknd on 2008-11-21
> **pmasiar said:**
> It is not, all you need to do to write better unit tests. They will also "explain" API, and have side benefit to help design better API. Tests are good for you and your app! 8-)

I agree in parts. Testing are a lot easier with Lua / Python / abcdef, but the code can't be refactored by (simple) tools. You just can't refactor a code where there are abusive use of upvalues in a closure and environment  changes (they are usually bad practices, but the programmer will, some day, try to be "clever" and do it).

---

### Post by crazyfuturamanoob on 2008-11-21
How can anything written in python be commercial? That's impossible because python is interpreted, and it will be open-source.

---

### Post by pmasiar on 2008-11-21
> **kknd said:**
>  You just can't refactor a code where there are abusive use of upvalues in a closure and environment  changes (they are usually bad practices, but the programmer will, some day, try to be "clever" and do it).

there are no technical solutions for social problems. OTOH, code review can handle such cowboys - and has other positive side effects (exactly like TDD), ans is cheap too. 

I am mystified why people deliberatedly avoid simple cheap solutions for common problems...

---

### Post by stevescripts on 2008-11-21
> **crazyfuturamanoob said:**
> How can anything written in python be commercial? That's impossible because python is interpreted, and it will be open-source.

It's all about the license ...

See [http://www.python.org/psf/license/]("http://www.python.org/psf/license/")

Steve

---

### Post by Luggy on 2008-11-21
I've written commercial database applications with QT, C++ and SQLite.

QT made interacting with the database very easy. It was also a dream to port between Windows and Linux. The application was easily compiled into a static executable so there was no installing of SQL drivers or GUI libraries.

---

### Post by stevescripts on 2008-11-21
QT is not free for commercial applications however...

---

### Post by Luggy on 2008-11-21
> **stevescripts said:**
> QT is not free for commercial applications however...

QT is dual licensed. What that means is that you can have access to it for free as long as you keep all the code you create with it under the GPL and open it up (which is what we did). If you want to close your source then you have to pay the big bucks.

What I ment by 'commerical application' was that we were paid to work on this software and were giving it to customers who used it to make money. Kind of a sign of robustness of how QT performed.

---

### Post by kknd on 2008-11-21
> **pmasiar said:**
> there are no technical solutions for social problems. OTOH, code review can handle such cowboys - and has other positive side effects (exactly like TDD), ans is cheap too. 

I am mystified why people deliberatedly avoid simple cheap solutions for common problems...

I agree, again.

We don't have any problem like this. But, this may be a reason of why it isn't so popular on this applications (also, not popular isn't a problem at all).

50% of the code of the systems developed by enterprises of my region are made by trainees. If they make a mess with a constrained language, image with a dynamic :). You don't need to believe, but 50% of the local enterprises also doesn't uses version control.

P.S:

Sorry for forking the topic. Back to the main topic:

I believe that Lua / Python / other dynamic languages magnifies the developer skills: a good developer will gain productivity, and a bad one will do a real mess. That why I believe that small enterprises, but with skilled developers, can battle the bigger old ones.

---

### Post by pmasiar on 2008-11-21
> **kknd said:**
> 50% of the code of the systems developed by enterprises of my region are made by trainees. If they make a mess with a constrained language, image with a dynamic :). You don't need to believe, but 50% of the local enterprises also doesn't uses version control.
[...]
I believe that Lua / Python / other dynamic languages magnifies the developer skills: a good developer will gain productivity, and a bad one will do a real mess. That why I believe that small enterprises, but with skilled developers, can battle the bigger old ones.

Yes, that's exactly right! That's why YouTube used Python, to be interesting target for buyout by Google. 

But solution is not to have more monkeys banging on more typewriters: solution is to give monkeys training to be more productive and better programmers. There is no beef in solving wrong problem in a better way: just solve right problem instead 8-)

And if big companies insist on solving wrong problem: free market and startups will take care about that!  8-)

---

### Post by ABCC on 2008-11-21
> **crazyfuturamanoob said:**
> How can anything written in python be commercial? That's impossible because python is interpreted, and it will be open-source.

It won't be open source it will be bound by the license the company selling the software chooses to use. Python's interpreted nature may make it easier to reverse engineer it steps can still be taken to obfuscate the code. The best one I know is simply putting it into an .exe container.

The stated intention is to use it on cash register systems. I seriously doubt that rampant piracy is going to be on their greatest concerns. After all, how many cashiers know what a .pyc is?

ABCC

---

