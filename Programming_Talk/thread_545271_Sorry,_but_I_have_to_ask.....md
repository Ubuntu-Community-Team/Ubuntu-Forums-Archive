---
title: "Sorry, but I have to ask...."
date: 2007-09-07
forum: Programming Talk
---

### Post by Midahed on 2007-09-07
...another of those 'which language' / 'what tools' questions #-o

Well, not quite...

I moved across to Linux just a few months ago and, although I have a Windows guest running under VMware, I'm trying to avoid using Windows any more than the absolute minimum.

As I'm recently retired I want to do a bit of application design and development for my own entertainment and to help keep the brain cells working.  I used to work in IT, latterly in database administration (Oracle and SQL Server) and some small back-office application development, mainly using VB :oops:

I'd like to learn something new, but at the same time I'm hooked on the super-RAD environment that is part of the world of VB and Microsoft.  I also like having a set of tools that are designed to work well together.

Although I've written a lot of code for applications that have subsequently gone on to be used for many years, I don't really consider myself a programmer.  I like to be able to quickly test that what I've written does what I think it will, so for that reason I'm drawn to an interpreted language as opposed to having to go through the compile and link cycle every time I want to try something.

I don't see myself writing drivers or having to call low-level functions in the OS.  I'm not interested in web development - I'm looking for something that will play well with a local MySQL back-end database and where it's easy to build forms and populate them with controls - preferably in a VB-like GUI environment.

Is Python the right tool for this?  I also considered Java and NetBeans, but I'm more drawn to Python at the moment.

What other tools would I need in order to have a VB-like development environment in the world of Python?  I'm reluctant to invest time learning Python and ToolA and ToolB and ToolC, only to find that they don't always work together as well as they should.  Oh for that 'integrated' feeling that Microsoft provides (at a price!) ;)

I've seen some Python code examples that seem to show the sort of text highlighting (and syntax checking?) that's available with VB?  What are the best Python editors to use?  At the moment I'm just using terminal to try a few commands, but of course there's no syntax checking until I try to run it....

So, given my requirements, is Python the best decision, or should I look elsewhere?  If Python is the right choice again, given my requirements, what would be the best tools/editor, etc, to use with it?

Thanks,

Mike

---

### Post by LaRoza on 2007-09-07
> **Midahed said:**
> 

I'd like to learn something new, but at the same time I'm hooked on the super-RAD environment that is part of the world of VB and Microsoft.  I also like having a set of tools that are designed to work well together.

Is Python the right tool for this?  I also considered Java and NetBeans, but I'm more drawn to Python at the moment.

What other tools would I need in order to have a VB-like development environment in the world of Python?

So, given my requirements, is Python the best decision, or should I look elsewhere?  If Python is the right choice again, given my requirements, what would be the best tools/editor, etc, to use with it?


Python may be what you are looking for, see my wiki in my sig.

PHP and MySQL might also be what you want, if you are in a web based environment, Linux, Apache, PHP, Perl (and now Python) work very well together.

Gedit has syntax highlighting, as does almost every other editor. Some would recommend IDLE, but I never really used it, but it is an IDE for Python.

Other editors:

* Vim
* IDLE
* KWrite
* Kate
* Crimson Editor (for Windows, what I use for all of my coding when not using Linux)

---

### Post by loell on 2007-09-07
i don't think python fits your requirements, Java and Netbeans would be the closest RAD Language and IDE for you though.

you can also consider mono and monodevelop , if your into vb.net :)

---

### Post by LaRoza on 2007-09-07
> **Midahed said:**
> 
Although I've written a lot of code for applications that have subsequently gone on to be used for many years, I don't really consider myself a programmer.  I like to be able to quickly test that what I've written does what I think it will, so for that reason I'm drawn to an interpreted language as opposed to having to go through the compile and link cycle every time I want to try something.

I don't see myself writing drivers or having to call low-level functions in the OS.  I'm not interested in web development - I'm looking for something that will play well with a local MySQL back-end database and where it's easy to build forms and populate them with controls - preferably in a VB-like GUI environment.


Python is easy to use with MySQL and SQLite.

GUI's are also easy to make, my wiki has several listed.

I don't know how Java will work in such an environment, but my experience with Java tells me Python would be better for you, at least to start with.

---

### Post by loell on 2007-09-07
i would have suggested python if you are interested with web app development,

since it would be easier for you to map to any database using popular python web frameworks but since you are not interested in web development.

and python with UI toolkits have no ORM , like easy gui data binding of VB,

so Java and Netbeans could be for you 

[with a gui data binding]("http://www.netbeans.org/kb/55/gui-database.html")

---

### Post by emperon on 2007-09-07
I'd say go for  Mono
This way you will feel yourself at home. Though I am not sure the status of VB.NET on mono but C# works well.

---

### Post by LaRoza on 2007-09-07
OP, look into both.

---

### Post by pmasiar on 2007-09-07
Python is nice because you can develop faster - in RAD style, instead of fighting with Java static typing.

IDE: depends on your style. IDLE is simple (colors, object help) but of course it is much harder to know propert type for a dynamically typed language - because it is dynamic, you know? :-) Other good free IDEs are SPE, Eric, Komodo. Komodo has paid Pro version, there are couple more commercial IDEs: WingIDE etc.

I often use SciTE for simple edits: it start so fast!

Many people prefer to learn good full-featured extendable programmer's editor, like vim or emacs, and then customize it exactly as you like, with features not available to standard IDEs. Vim is extemdable in Python, a big plus IMHO.

When learning Pyton, instead of command shell, get IDLE shell. You have interactive commandline with syntax highlighting, where you san build and test code, one line at a time. Perfect for following tutorials.

See wiki in my sig for links. For learning language and having fun doing it, try pythonChallenge.com website: 33 levels of puzzles, which you have to solve using Python. Includes forums with hints for each level :-)

---

### Post by loell on 2007-09-07
> **pmasiar said:**
> Python is nice because you can develop faster - in RAD style, instead of fighting with Java static typing.

i'm not going to argue, just one question, how can python be fitted when ones requirements are

> looking for something that will play well with a local MySQL back-end database and where it's **easy to build forms and populate them with controls - preferably in a VB-like GUI environment**.

> .  **not interested in web developmen**t 

> I'm reluctant to invest time learning Python and ToolA and ToolB and ToolC, only to find that they don't always work together as well as they should. Oh for that 'integrated' feeling

in light of these requirement please provide a link for UI toolkit in python that have some sort of ORM. for the OP, i'm also interested to see this in python.

---

### Post by Nekiruhs on 2007-09-07
> **loell said:**
> i'm not going to argue, just one question, how can python be fitted when ones requirements are







in light of these requirement please provide a link for UI toolkit in python that have some sort of ORM. for the OP, i'm also interested to see this in python.
Ok. PyGTK and Glade. I use PyGTK and Glade all the time. Glade builds the GUIs an exports a .glade XML file. PyGTK has tools to read this XML file and create the GUI.

1. Design a GUI in Glade.

2. Use a model like this in the program:
import gtk, gtk.glade

```
xml = gtk.glade.XML('somefile.glade') #Relative path to .glade file
somebutton = xml.get_widget('somebutton's name from glade')
somewindow = xml.get_widget('somewindow's name from glade')
somebutton.connect('clicked', somefunc())
```

---

### Post by loell on 2007-09-07
yeah, sure there are toolkits pygtk, wxpython, pyqt
 but where is the easy data binding for the database back-end ?

---

### Post by matthew on 2007-09-07
> **loell said:**
> yeah, sure there are toolkits pygtk, wxpython, pyqt
 but where is the easy data binding for the database back-end ?I'm looking into the same thing for a project. I found this forum user's page with some links to python libraries designed for interacting with mysql and sqlite, with tutorials.

[http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python)

I haven't tried them yet, but both options look promising to me, maybe you will find them useful as well.

EDIT: lol, LaRoza's posted in this thread already. I think I saw his page from his sig in this thread. :)

---

### Post by loell on 2007-09-07
:lolflag: i think i found what i was looking for, though not as solid java and netbeans integration

this one looks promising for wxpython  

[Dabo is a 3-tier, cross-platform application development framework, written in Python atop the wxPython GUI toolkit. And while Dabo is designed to create database-centric apps, that is not a requirement. Lots of people are using Dabo for the GUI tools to create apps that have no need to connect to a database at all]("http://dabodev.com/").


[screenshots]("http://dabodev.com/screenshots")

this has not landed in the repo though :(


anyone interested to package this? :)
packagers please look into this :KS

---

### Post by matthew on 2007-09-07
> **loell said:**
> [Dabo]("http://dabodev.com/")Very promising...[the license]("http://dabodev.com/licensing") is a good one for me...

> Dabo: 3-tier desktop application runtime framework
 		Copyright (c) 2004-2006 Ed Leafe, Paul McNett, et. al.
 		 		Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
 		 		The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.


---

### Post by loell on 2007-09-07
indeed the license is a good one

---

### Post by pmasiar on 2007-09-08
> **loell said:**
> i'm not going to argue, just one question, how can python be fitted when ones requirements are: [... VB-like...]
 provide a link for UI toolkit in python that have some sort of ORM. for the OP, i'm also interested to see this in python.

Well, Python cannot be as tightly integrated as VB, because it is not possible with dynamically typed language: when type is checked only at runtime, IDE does not know type either (meditate about it a little and you will get it :-) ) it is price you pay to have RAD. 

IMHO we are stuck like that until some genius will create program which can "read my mind and do what I mean" - although Perl was close to it :-)

You know, universal program, using rmmadwim module:

```

$result = rmmadwim();
print $result;

```

But wait, this is not secure, here is much improved secure version:

```

if rmmadwim() or die "you are not allowed to do this";
$result = rmmadwim();
print $result;

```

</joke>

And almost any Python IDE for Linux still much better that any IDE oriented to Basic, that I hope is obvious now?

very good ORM are the one in TurboGears: SQLObject and SQLAlchemy. You can break TG apart and use only the gears you need :-)

I don't do GUI myself, but people praise Glade and wxPython all the time ;-)

I remember Dabo presentation from some Pycon: I had impression that guy was down-to-earth pragmatic, building stuff like foxpro (which I loved back in times), but I never needed it: my bread and butter is web and TG :-) So if it works for you, good luck!

---

### Post by loell on 2007-09-08
i'm a believer of TG myself , and a fan of cherrypy :)
if i would like to develop desktops apps through web frameworks i might also consider using adobe integrated runtime as one of the front end, and perhaps TG on the back end.

just to widen the OPs options

demo for data and gui integration

[http://www.netbeans.org/download/flash/netbeans_6_gui_builder/netbeans_6_gui_builder.html]("http://www.netbeans.org/download/flash/netbeans_6_gui_builder/netbeans_6_gui_builder.html")

---

### Post by samjh on 2007-09-08
It seems Mono and Monodevelop would be the best way to go.

It's pretty much .NET for Linux with a Visual Studio wannabe IDE. ;)

[www.mono-project.org](www.mono-project.org)

Or just install from repositories.

---

### Post by Midahed on 2007-09-09
Well, thanks to everyone for your responses - they've been very helpful.

To cut a long story short, I briefly played with Glade, but found that it didn't really compare with the ease with which forms can be designed in the M$ VB environment.  I know - I should be forgetting about M$ and VB, but it's so damn EASY to use that it's hard to give up ;)

I also had a play with NetBeans - it's a bit closer to what I'm looking for, and I get the impression that it's easier to get Java code talking to a MySQL back-end.  I think I even read that there's a native Java mini-SQL database (or did I dream that?).  I also liked the easy availability of extensive and detailed tutorials on the Sun and NetBeans sites.

To be honest, I like the static typing environment of Java but, from what I've seen so far, I far prefer the syntax of Python - especially the fact that indenting is an inherent part of the syntax of the language.  In my view, Python code is much more readable than that of Java with all those damn curly brackets....

I also looked at Mono.  Mono Develop looks pretty good, but as it was my intention to move away from VB, (unless I've misunderstood something), my only real choice of language would be C#....?

So I sort of arrived back at square one again looking at Python.  I'd already discovered MySQLdb, but it looked quite a bit more work than, say, the equivalent database access in the dreaded VB.  That tended to put me off Python a bit...

But, having done a lot more reading since then, would I be right in thinking that Python, Qt4, PyQt, wxPython and Eric might be a good combination for what I want?  Qt Designer, in particular, looks very slick - far better than Glade, from what I could see.  The Qt classes also include SQL database support and seem to make establishing a database connection and running a query look very easy:-

 ```
        QSqlDatabase db = QSqlDatabase::addDatabase("QMYSQL");
        db.setHostName("bigblue");
        db.setDatabaseName("flightdb");
        db.setUserName("acarlson");
        db.setPassword("1uTbSbAs");
        bool ok = db.open();
```

```
        QSqlQuery query;
        query.exec("SELECT name, salary FROM employee WHERE salary > 50000");
```

There's info about the Qt SQL module on the TrollTech site here:- [http://doc.trolltech.com/4.0/qtsql.html](http://doc.trolltech.com/4.0/qtsql.html)

I'm completely new to all these tools, so it's quite possible I've completely misunderstood what all this stuff does.  It's also possible that I'm trying to bolt things together that just won't work - or at least won't work in the way that I imagine in a Python environment.

Can anyone give me a bit more guidance on this.  Is anyone using the mix of tools with Python that I've suggested, or will it all end in tears?  :)

Thanks,  

Mike

---

### Post by pmasiar on 2007-09-09
You should look at object-relation mappers for SQL: simple SQLObject (you don't write any SQL at all), and more flexible SQLAlchemy (you **can** write SQL for some trickier statements). 

Another simple SQL database for desktop/embedded systems is SQLite )with pySQLite) - it is a single-user DB library, not a server. 

I know people who love to pay for WingIDE, they say it is worth it, but I never tried it - I am kinda free software zealot. :-)

---

### Post by Midahed on 2007-09-09
> **pmasiar said:**
> You should look at object-relation mappers for SQL: simple SQLObject (you don't write any SQL at all), and more flexible SQLAlchemy (you **can** write SQL for some trickier statements). 

Another simple SQL database for desktop/embedded systems is SQLite )with pySQLite) - it is a single-user DB library, not a server. 

I know people who love to pay for WingIDE, they say it is worth it, but I never tried it - I am kinda free software zealot. :-)
Thanks for the suggestions.  I hadn't come across WingIDE, but it costs too much for me!  All the tools I suggested are free - as long as if I chose to distribute my application, I do so without charge.

I actually prefer the idea of being able to run SQL directly against the back-end, especially for one-off queries or tweaks to the database.  Any regularly-used queries get built into the application, while the one-offs stay as SQL.  It's a steam hammer to crack a nut, but it suits how I work.  Hence my intended use of MySQL (at least at the moment!)

Mike

---

### Post by Midahed on 2007-09-10
Well, in the absence of howls of 'you must be daft', I've decided to try Python 2.5, Qt and PyQt - mainly because Qt Designer seems the nearest I can get to my ideal in terms of quick-and-easy forms design.

However, for the moment I've cheated somewhat by installing it all on my Windows guest running under VMware.  For what's really just an evaluation exercise, I couldn't be bothered to fight the inevitable difficulties with a Linux-based installation.  OK, it's all in the repos, but I'm just not experienced enough with Linux to easily determine which packages I need.  There must be hundreds of Python, Qt and PyQt-related packages available to choose from, and I'm bound to get it wrong and leave some essentials out (or fill my drive with stuff that's not needed!).  The Python 2.5 install for Windows is easy-peasy and the guys and gals at Riverbank have put together a Windows installation binary that includes everything else that's needed:-

    *  PyQt
    * Qt
    * Qt Designer
    * Qt Linguist
    * Qt Assistant
    * pyuic4
    * pylupdate4
    * lrelease
    * pyrcc4
    * QScintilla
    * PyQwt
    * Qwt
    * eric IDE

... all in one easy installation executable.  The only glitch I had was that initially I didn't accept the default installation path for Python (it wants to use c:\Python25 whereas I selected c:\Program Files\Python25).  The upshot was that Eric wouldn't run.  Rather than find out why, I just un-installed it all and re-installed using the default path.  It all worked fine after that.

If and when I decide to stick with this particular combination of tools, I'll try and get it working on Ubuntu.  Until then, I'm happy enough to try it out on Windows :oops: :)

Thanks for all your advice and suggestions.

Mike

---

### Post by samjh on 2007-09-11
It's not that hard to use PyQT on Ubuntu.

Open up your terminal, and type this:
```
sudo apt-get install pyqt4-dev-tools python-qt4-doc eric qt4-designer
```This will install all your PyQT 4 development libraries for core QT and QT's GUI, documentation for PyQT 4, QT4's designer, and the Eric Python IDE.

---

### Post by Midahed on 2007-09-11
> **samjh said:**
> It's not that hard to use PyQT on Ubuntu....

Ahh, but the important difference between us is that you knew which modules to download... :)  ... whereas I was just looking at all those modules in Synaptic in complete bewilderment. :confused:

OK, maybe it's fairly obvious that I would need to download pyqt4-dev-tools but the list on Synaptic also has things like python-qt4, python-qt4-dbg, python-qt4-dev, python-qt4-sql, etc, etc.  And that's without considering all the non-qt4 entries that begin with 'python'....

This is one aspect of Linux that I find difficult on occasions - the modular construction of the software means that it is often not at all clear to the beginner which of the packages should be installed in order to get a particular set of features working.

Let me give you an example...

A little while ago I downloaded a mainstream Linux app from the Ubuntu repos.  I omitted to include the -docs module in my selection.  Later, when running the app I clicked 'Help' and absolutely nothing happened.  No response whatever, and certainly no error message along the lines of 'the documentation module for this application is not installed'.  In that instance it did occur to me to check back in the repos to see if I had missed something, so the problem was easily solved.  However, this sort of thing will trip-up new users - especially those trying to move away from the cosseted world of Microsoft.  Obviously the more complicated the application and the larger the number of packages, the more chance there is of things not working (because the user has left something out) and, unless the error-trapping is top-notch, the bigger chance there is of the user having no idea as to why it's failing.

In my view this is one of the things that the Linux community will have to seriously address if Linux is ever to become more than a niche segment of the desktop OS market.

Thanks for the tip though.  If I get on with Python and Qt I'll use that to install it on Feisty.

Mike

---

### Post by samjh on 2007-09-11
Hmmm, you misunderstood me.

I meant that it is not hard to install PyQT on Ubuntu, if you know what to install.

Yes, the sheer number of available packages can be confusing.  The secret is to patiently read the descriptions for each package using Synaptic, and a bit of trial-and-error. ;)  Google also helps.

---

### Post by Midahed on 2007-09-11
> **samjh said:**
> The secret is to patiently read the descriptions for each package using Synaptic
Oh, I do, but it often doesn't help :grin:

I agree that installing using apt-get or going the GUI route with Synaptic is easy enough in itself...  I just wish it was a bit easier to get applications installed correctly the first time round without having to trawl forums to look for answers as to why an installation might not be working.

OK, I'll acknowledge that it's part of the fun of Linux - heaven knows, I've spent enough time on my system over the last few weeks :), but these sort of installation problems will put off loads of potential Linux converts who, through necessity maybe, have to be more focussed on the productivity of their PC rather than the 'fun' and challenges of getting things working.

Mike

---

