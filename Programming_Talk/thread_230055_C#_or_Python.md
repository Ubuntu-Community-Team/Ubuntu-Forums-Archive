---
title: "C# or Python?"
date: 2006-08-05
forum: Programming Talk
---

### Post by Olav on 2006-08-05
Hello. After many years of **not** programming, I am now in a situation where I would like to start again. To be a little more specific: I have an idea for a commercial application that I would like to realize. Well, at least I would like to build a quasi-functional 0.1 version, and then see how it goes from there. Obviously, one of the things I must now do is to select a programming language to work with.

In my earlier life I have been using languages like Microsoft's QuickBASIC (waaayyy back), Clipper, Turbo/Borland Pascal. Did a few small but successful projects with them, too. I have done some tinkering with Delphi and Visual Basic, and never liked either. Probably because they were both still very immature then. I have looked at (and turned away from) C and C++. They never seemed worth the hassle. I had some training in SmallTalk, only programming classes I ever took, but most everything of that language has escaped me since - I'm still OK with general OO concepts though. I use PHP sometimes to do simple dynamic webpages, **very** light CMS-like stuff and databases. But I don't consider these to be serious applications, they are just hacks. I steal bits of code from others, from tutorials and such, and just adapt them to my needs.

My application must run at least on Linux/Gnome, but it would be (much!) better if it could also run as a as good as native program on Windows and, if at all possible, MacOSX. I said it was to be a commercial application, didn't I, so obviously I want to maximize my potential for sale...

I don't like Java (don't ask...).

This application will use a generic relational (SQL) database, like MySQL, PostgreSQL, Oracle, MSSQL etc. I want the language I choose to be fairly high-level, to do away with a lot of micro-management of GUI elements, database connections et cetera, letting me concentrate on application logic instead of arcane technical housekeeping. I also want quick results, but not too dirty...

There will be no heavy graphics or multimedia involved, except perhaps the import and storage of graphics and multimedia files inside databases.

So far, my investigations lead me to consider C# (and the Mono/.NET environment) or Python (and whatever tools are involved with that). I lack any experience with either and, like you could have guessed, I don't consider myself up-to-date with modern application programming anyway. So either way, I will have to invest some time in picking that up. A language and a set of tools that will actually HELP me get up to speed with this will of course be highly preferable.

I heard some good things about Ruby, too. I may have to look into that.

So, in short: **what language would you recommend for my project, and why?**

Meanwhile I will not be sitting still of course, and will try to learn a bit more about all the options. But I feel that your personal opinions could perhaps be very helpful in making a final choice. I may even have missed a few obvious language candidates, so I would love to hear about them too!

Thanks for your time and your answers!

---

### Post by sapo on 2006-08-05
I use bot and i think if you want to earn money you should just use C# and .NET in windows... 

I tried to use mono but i found a lot of limitations... and i think python is better to make multiplataform stuff.. but if i had to give you an advice i would say, learn both and then you will be able to tell wich one is better for your project.. 

python is my favorite language, but i code C# for food cause its C# that pays my salary.. python i just use to make some backup scripts and server side stuff. :p

---

### Post by neilp85 on 2006-08-05
I would recommend using Python with wxWidgets for the GUI elements. I say this because you said your application must run at least on Linux/GNOME but would be great to run on Windows and OSX. Python was built from the ground up to portable, while C# was not. I know there is Mono but I still consider C# a Windows only language. In my limited experience using Python I have found it to be exactly what I needed

---

### Post by mariux on 2006-08-05
Having only tried C# with .Net and VS (not with mono and GTK#) i have to say that i was blown away by how great the language was (my earlier experice has been with c++ and perl (gtk2-perl)).

Now how good c# is for programming for linux i dont know.

---

### Post by Olav on 2006-08-05
Hello Sapo, 

> **sapo said:**
> I use bot and i think if you want to earn money you should just use C# and .NET in windows... 
Perhaps I did not make this clear, but I do not intend to make money with my programming per se. Now, I **do** intend (or hope...) to make money with my application, once that becomes usable. You see, there is a slight difference.

> I tried to use mono but i found a lot of limitations... and i think python is better to make multiplataform stuff.. 
Interesting. Does it also work well with databases? What is your favourite tool to set up a GUI?

> but if i had to give you an advice i would say, learn both and then you will be able to tell wich one is better for your project.. 
That would be nice, wouldn't it. But my time and energy are not limitless, and to learn both well enough would seem like a waste. 

> python is my favorite language, but i code C# for food cause its C# that pays my salary.. python i just use to make some backup scripts and server side stuff. :p
OK, one vote for Python noted ;) 

Thank you.

---

### Post by Olav on 2006-08-05
Hello Neil,

> **neilp85 said:**
> I would recommend using Python with wxWidgets for the GUI elements. I say this because you said your application must run at least on Linux/GNOME but would be great to run on Windows and OSX.
Yes, this is almost a hard requirement for me.

> Python was built from the ground up to portable, while C# was not. I know there is Mono but I still consider C# a Windows only language.
Could you please explain why? I have seen a couple of nice Gnome applications lately that were written in C#/Mono, they were Beagle and F-Spot[*], and they didn't seem lacking. Of course I didn't check their source code, my experience with them is just as an end user.

> In my limited experience using Python I have found it to be exactly what I needed
Second vote for Python ;) 

Thank you.


[*] For Ubuntu, Beagle and F-Spot are installable in the Universe repository.

---

### Post by Olav on 2006-08-05
> **mariux said:**
> Having only tried C# with .Net and VS (not with mono and GTK#) i have to say that i was blown away by how great the language was (my earlier experice has been with c++ and perl (gtk2-perl)).

Now how good c# is for programming for linux i dont know.
That is one vote for C#.

So far it is 1-2 ;) 

Thank you.

---

### Post by Olav on 2006-08-05
Done some more reading now ;)

How about a combo of Python and PyGTK?

---

### Post by sapo on 2006-08-05
> **Olav said:**
> Interesting. Does it also work well with databases? What is your favourite tool to set up a GUI?


Mono works well with firebird and mysql, the limitations i found are all in the windows forms and GUI, first, you dont have a good gui builder under linux, so you need to build the gui on windows. but when you try to compile it on mono you have to sit down and pray, if you dont pray hard enough all you will get is "XYZ isnt supported".

Then you have .net 2.0 with all the new features as databindings, ado.net 2.0, etc but guess what, it isnt implemented in mono, so you need to do everything by hand.

If i was to make something to be multiplataform i would use Python + Pygtk + Glade, the you just install the GTK Libraries on windows and you have a multiplataform application.

Yes, i made some gui stuff even using database with python and pygtk (using a firebird database and the python kinterbasdb module) and it worked perfectly on both windows and linux.. and guess what.. it was so freaking easy to code.

---

### Post by Daverz on 2006-08-05
Now that Qt4 has a GPL version (note GPL; Gtk is a little less encumbered being LGPL, and wxWidgets still less being a BSD type license), PyQt4 looks like a viable option for crossplatform GPL work now.  I have it installed on windows, ubuntu of course, and on Mac OS X (from source; I've had some problems with menu demos on OS X and haven't had time to track down the source of the problem).  It's not as well documented as wxPython, which has an excellent book on it and a great wiki.

I'm using PyGtk and Kiwi for cross linux/win32 work currently and am fairly happy with it.  Gtk 2.x only has a nascent OS X port, which I haven't tried to get working.

One more comment: as IronPython improves, Python and C# should become more complementary rather than competitors to choose between.  Even as it is, the languages fill quite different niches.

---

### Post by Olav on 2006-08-05
Thank you, Sapo and Daverz, for your insights. I am beginning to lean more and more toward Python, either with wxWidgets or GTK (PyGTK) as a GUI toolkit. Now, I will just have to learn how to use them :D 

> **sapo said:**
> Yes, i made some gui stuff even using database with python and pygtk (using a firebird database and the python kinterbasdb module) and it worked perfectly on both windows and linux.. and guess what.. it was so freaking easy to code.
Cool! Do you have an example of this, or do you know a website where this method of work is demonstrated?

> **Daverz said:**
> Now that Qt4 has a GPL version (note GPL; Gtk is a little less encumbered being LGPL, and wxWidgets still less being a BSD type license),
I am not sure I understand you here. You seem to imply that the GPL being applied to a programming language (and probably, its libraries etc.) imposes some kind of restriction on the application that I would want to build with that language? I don't think this is how the GPL works, but I may be wrong. Care to explain?

> PyQt4 looks like a viable option for crossplatform GPL work now.
Too much options makes choosing even harder... ;) 

I am sure PyQt4 is wonderful too, but I will stick with two toolkits to consider for the moment, until I hear more compelling reasons to add another to my list.

> One more comment: as IronPython improves, Python and C# should become more complementary rather than competitors to choose between.  Even as it is, the languages fill quite different niches.
Do you care to elaborate on that? Which niches are you talking about? Do you mean that another kind of application gets built in Python than in C#? What would be the reason?

---

### Post by sapo on 2006-08-06
> **Olav said:**
> Thank you, Sapo and Daverz, for your insights. I am beginning to lean more and more toward Python, either with wxWidgets or GTK (PyGTK) as a GUI toolkit. Now, I will just have to learn how to use them :D 


Cool! Do you have an example of this, or do you know a website where this method of work is demonstrated?


This should be a good start:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

---

### Post by Van_Gogh on 2006-08-06
> **sapo said:**
> This should be a good start:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)
[This tutorial]("http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/") is probably even more basic, is somewhat more modern and is also very easy to follow.

It also has quite good [a follw-up tutorial]("http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/") to show some advanced tree view/list stuff. Highly recommended, IMO

---

### Post by Daverz on 2006-08-06
> **Olav said:**
> I am not sure I understand you here. You seem to imply that the GPL being applied to a programming language (and probably, its libraries etc.) imposes some kind of restriction on the application that I would want to build with that language? I don't think this is how the GPL works, but I may be wrong. Care to explain?


IANAL, but IIRC if you link to the GPL Qt4 libraries, you're code has to be GPL.  

> 
Too much options makes choosing even harder... ;) 


For me it comes down do knowing Gtk very well already, but a friend has shown some interest in Qt, so that's why I was investigating it.

BTW, if you're doing database work, check out sqlite.  I use it for my project, and I can copy my code + database file from linux to windows and have it work perfectly with absolutely no changes.  

It's also easy to use py2exe + inno setup to create windows .exe installers for pygtk projects.

---

### Post by Olav on 2006-08-06
> **sapo said:**
> This should be a good start:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

> **Van_Gogh said:**
> [This tutorial]("http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/") is probably even more basic, is somewhat more modern and is also very easy to follow.

It also has quite good [a follw-up tutorial]("http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/") to show some advanced tree view/list stuff. Highly recommended, IMO

Sapo, Van Gogh, thank you both. Those links you mentioned look very promising. I had done some searching on my own as well and found these:

[LIST]
[*][http://www.pygtk.org/pygtk2tutorial/index.html]("http://www.pygtk.org/pygtk2tutorial/index.html") (installable in Ubuntu as package python-gtk2-tutorial).
[*][http://www.serpia.org/tutorials]("http://www.serpia.org/tutorials") - made me install the SPE editor right away, looks very nice and not too overwhelming ;)
[/LIST]

I guess I have found myself something to do this week...

---

### Post by Olav on 2006-08-06
> **Daverz said:**
> IANAL, but IIRC if you link to the GPL Qt4 libraries, you're code has to be GPL.  
Isn't that only true for "derived work"? I think we should be fairly safe: [http://en.wikipedia.org/wiki/Derivative_work#Derivative_work_of_software]("http://en.wikipedia.org/wiki/Derivative_work#Derivative_work_of_software")

Then again, there is the LGPL, which should be the safest option either way. PyGTK is licensed as LGPL.

> BTW, if you're doing database work, check out sqlite.  I use it for my project, and I can copy my code + database file from linux to windows and have it work perfectly with absolutely no changes.
SQLite is indeed very nice for a certain class of programs, but it is definitely not going to work for my project (this is going to be a multi-user office application).

> It's also easy to use py2exe + inno setup to create windows .exe installers for pygtk projects.
Thanks. Must remember that. But first I need to build something ;)

---

### Post by nrs on 2006-08-06
> **sapo said:**
> Mono works well with firebird and mysql, the limitations i found are all in the windows forms and GUI, first, you dont have a good gui builder under linux, so you need to build the gui on windows. but when you try to compile it on mono you have to sit down and pray, if you dont pray hard enough all you will get is "XYZ isnt supported".

Then you have .net 2.0 with all the new features as databindings, ado.net 2.0, etc but guess what, it isnt implemented in mono, so you need to do everything by hand.

If i was to make something to be multiplataform i would use Python + Pygtk + Glade, the you just install the GTK Libraries on windows and you have a multiplataform application.

Yes, i made some gui stuff even using database with python and pygtk (using a firebird database and the python kinterbasdb module) and it worked perfectly on both windows and linux.. and guess what.. it was so freaking easy to code.

I'm not sure I understand your reasoning. 

You brush off C#/Mono because of incomplete windows forms support (it's improving), but recommended Python which has no windows forms support. It's worth mentioning that _both_ have GTK support in the forms of GTK# and PyGTK. 

You brush of C#/Mono saying there are no good GUI designers available for it in Linux, but then you mention using Python/PyGTK with Glade. It's OK to use Glade w/ Python+PyGTK but not Mono+GTK# ? 

You mention lack of full .NET 2.0 support (improving rapidly), compared to Python's 0 support. Even without full support .NET 2.0 Mono is good in it's own standing.

As for the author, no one can tell you. Try Python, try Mono. Just don't try using incomplete Windows Forms and complain though. If you're using GTK  w/ Python compare it to GTK w/ Mono. If you're using Glade with Python compare it to Glade w/ Python, etc.

AFAIK the latest Mono release comes with a copy of Glade for Windows too.

---

### Post by Daverz on 2006-08-07
> **Olav said:**
> SQLite is indeed very nice for a certain class of programs, but it is definitely not going to work for my project (this is going to be a multi-user office application).


See [http://sqlite.org/faq.html#q7](http://sqlite.org/faq.html#q7)

Of course, if you know you'll have a dedicated server available, there's no reason to use an embedded database engine.

---

### Post by LordHunter317 on 2006-08-07
If you link to GPL Qt4, your code must be GPL, unless you feel willing to test it in court.

---

### Post by sapo on 2006-08-07
> **nrs said:**
> I'm not sure I understand your reasoning. 

You brush off C#/Mono because of incomplete windows forms support (it's improving), but recommended Python which has no windows forms support. It's worth mentioning that _both_ have GTK support in the forms of GTK# and PyGTK. 

You brush of C#/Mono saying there are no good GUI designers available for it in Linux, but then you mention using Python/PyGTK with Glade. It's OK to use Glade w/ Python+PyGTK but not Mono+GTK# ? 

You mention lack of full .NET 2.0 support (improving rapidly), compared to Python's 0 support. Even without full support .NET 2.0 Mono is good in it's own standing.

As for the author, no one can tell you. Try Python, try Mono. Just don't try using incomplete Windows Forms and complain though. If you're using GTK  w/ Python compare it to GTK w/ Mono. If you're using Glade with Python compare it to Glade w/ Python, etc.

AFAIK the latest Mono release comes with a copy of Glade for Windows too.
You have a point, the truth is that i never tried C# with GTK, i always coded C# with Windows Forms, i read something about GTK# but never gave much importance to it.

But i prefer python over C# :)

---

### Post by Olav on 2006-08-07
> **Daverz said:**
> See [http://sqlite.org/faq.html#q7](http://sqlite.org/faq.html#q7)

Of course, if you know you'll have a dedicated server available, there's no reason to use an embedded database engine.
Such a dedicated server will pretty much be a requirement for my application, the fact being that several users should be able to access the database at the same time and from separate workstations (where they are running the app).

The FAQ you are referring to concurs that SQLite cannot be used in that situation.

---

### Post by Olav on 2006-08-07
> **LordHunter317 said:**
> If you link to GPL Qt4, your code must be GPL, unless you feel willing to test it in court.

This page seems to agree: [http://www.trolltech.com/developer/downloads/qt/windows]("http://www.trolltech.com/developer/downloads/qt/windows")

Of course, the legal standing of the GPL in various jurisdictions (and whether or not it applies to dynamic linking to a GPLed library) is still a bit unclear. LGPL is undoubtedly safer in that respect. BTW, I think QT is not my preference anyway. So I guess I won't run into legal issues soon.

Thank you for sharing your thought, though. Yes, I must do further study on licensing before I definitely go ahead with this.

---

### Post by Olav on 2006-08-07
> **sapo said:**
> You have a point, the truth is that i never tried C# with GTK, i always coded C# with Windows Forms, i read something about GTK# but never gave much importance to it.
Could someone please explain **in brief** what "Windows Forms" are? And why would I care about them?

> But i prefer python over C# :)
That much was clear, and thank you for your remarks ;)

---

### Post by DJ_Max on 2006-08-07
> **Olav said:**
> Could someone please explain **in brief** what "Windows Forms" are? And why would I care about them?


That much was clear, and thank you for your remarks ;)

Windows Forms is a toolkit for Windows like GTK is for Linux or BSD. Mono has implementation  [WinForms](hhttp://www.mono-project.com/WinForms).

Have you looked at the other languages Mono supports like [Boo]("http://boo.codehaus.org/Language+Features"), a mix between C# and Python.

---

### Post by Daverz on 2006-08-07
> **Olav said:**
> Such a dedicated server will pretty much be a requirement for my application, the fact being that several users should be able to access the database at the same time and from separate workstations (where they are running the app).

The FAQ you are referring to concurs that SQLite cannot be used in that situation.

Sorry, I don't know why I had the idea there was an embedded requirement.  Probably just projection.

However, sqlite *can* be used in that situation.  One process may have to wait a few milliseconds for its turn, though.  It's even been used for websites.

---

### Post by Olav on 2006-08-07
> **DJ_Max said:**
> Windows Forms is a toolkit for Windows like GTK is for Linux or BSD. Mono has implementation  [WinForms](hhttp://www.mono-project.com/WinForms).

Have you looked at the other languages Mono supports like [Boo]("http://boo.codehaus.org/Language+Features"), a mix between C# and Python.
Thank you for updating me. Both options look nice enough but I don't think I'm interested.

I have more or less decided now on Python + PyGTK. I will spend most of the rest of the week trying to learn the basics of those.

Wish me luck ;)

---

### Post by Olav on 2006-08-07
> **Daverz said:**
> Sorry, I don't know why I had the idea there was an embedded requirement.  Probably just projection.
That' s okay, never mind ;)

> However, sqlite *can* be used in that situation.  One process may have to wait a few milliseconds for its turn, though.  It's even been used for websites.
I can see how it could be used on a web server, and it will probably be a very nice solution for that too.

But for my application I seriously think I will need a bit more control, such as only a proper DBMS can provide. There will be user privileges to take care of, transactions, referential integrity, et cetera.

---

