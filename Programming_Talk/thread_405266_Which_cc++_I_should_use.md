---
title: "Which c/c++ I should use?"
date: 2007-04-09
forum: Programming Talk
---

### Post by evagelos on 2007-04-09
Hi,
   I am new in Linux, whick c++ i should learn, and which gui and database addons i should use? I am using Visual Studio.  Thanks

---

### Post by rufius on 2007-04-09
There's really only 1 C++ so to speak but several diff compilers. Available that I see are gcc-3.3, gcc-3.4, and gcc-4.1. Really they're just updates to eachother, most code should work fine in each without any changes. 

As far as gui and database addons, I'm assuming you mean gui toolkits and database toolkits. In that case, if you're sticking to Ubuntu (using Gnome) and this software is mostly for you, then go with the GTK2 toolkit, and then use whatever database you like (ie: MySQL, Postgresql, SQLite). I personally don't work at all with gui's but I do use sqlite mostly for my programs when I need a database. 

If you need an IDE, I would look into Anjuta.

---

### Post by pmasiar on 2007-04-09
which kind of apps do you want to write? C/C++ make sense in deep infrastructure, but not as much at application development level.

---

### Post by evagelos on 2007-04-09
> **pmasiar said:**
> which kind of apps do you want to write? C/C++ make sense in deep infrastructure, but not as much at application development level.

MOsty database application development

Thenk you

---

### Post by pmasiar on 2007-04-09
Try higher level, dynamically typed languages like Python or Ruby - see forum sticky. 

Most people agree that using HLL with automatic memory management and flexible typing, your productivity will increase substantially without much effect on speed of the resulting program, because most time is spent anyway at SQL connection/query.

---

### Post by Wybiral on 2007-04-09
> **pmasiar said:**
> Try higher level, dynamically typed languages like Python or Ruby - see forum sticky. 

Most people agree that using HLL with automatic memory management and flexible typing, your productivity will increase substantially without much effect on speed of the resulting program, because most time is spent anyway at SQL connection/query.

Shhhh... If you listen closely, you can hear the call of the elusive "pmasiar"...

Python.......... Python....

:p

---

### Post by pmasiar on 2007-04-09
Sure. I know you would prefer we all write database app in Assembly :-) but sane person may consider right tool for the job. 

If job is front-end for a database app, C/C++ might not be the best tool.

---

### Post by Wybiral on 2007-04-09
I'm not disagreeing with that, I was just making fun of you :)

---

### Post by rufius on 2007-04-09
> **evagelos said:**
> MOsty database application development

Thenk you

In that case... I agree with both pmasiar and Wybiral.

---

### Post by russell.h on 2007-04-09
As far as I know Visual Studio isn't available for Linux.

---

### Post by pmasiar on 2007-04-09
> **Wybiral said:**
> I'm not disagreeing with that, I was just making fun of you :)

Sorry I was in a wrong mood. Yes, i agree with you now :-)

---

### Post by samjh on 2007-04-10
If someone wants to write a database app in C/C++, let them I say! :)  A burnt hand teaches the best, after that the lesson about fire goes to the heart, as Gandalf would say in Lord of the Rings. ;)

But I sniff a contradiction in the original post.  New to linux, want to use C/C++ for database and gui, but using Visual Studio?!

If you're using Visual Studio, then C++ should already be included, along with rich documentation and more libraries for database access (see ODBC and ADO.NET) than you could poke a long stick at.

If you're actually using Linux, and the Visual Studio bit was just a humongous typo, then perhaps look at something like [Simple C++ Database API](http://simpledb.sourceforge.net/), or consult the documentation of your database engine/vendor for any APIs that can be used to access it.
As for GUI, you have too many choices.  GTKmm for Gnome desktops, Qt for KDE, wxWidgets for a platform-neutral choice, etc. etc.

---

### Post by rufius on 2007-04-10
> **samjh said:**
> 
If you're using Visual Studio, then C++ should already be included, along with rich documentation and more libraries for database access (see ODBC and ADO.NET) than you could poke a long stick at.

If you're actually using Linux, and the Visual Studio bit was just a humongous typo, then perhaps look at something like [Simple C++ Database API](http://simpledb.sourceforge.net/), or consult the documentation of your database engine/vendor for any APIs that can be used to access it.


I think he meant in the past he'd been using Visual Studio in Windows and wants something similar; hence why I mentioned Anjuta ;).

---

### Post by monktbd on 2007-04-10
if you are used to program c++/mfc under windows then you might be interested in wxwidgets as the gui framework. its syntax is quite similar to mfc - whether that is a plus or not is another topic :D 
also it is quite platform independent.

as for IDEs i would recommend codeblocks.

but overall, unless you are highly experienced in c++ only, just to make a database application i probably would look into another programming language making your life a bit easier.

---

### Post by samjh on 2007-04-10
> **rufius said:**
> I think he meant in the past he'd been using Visual Studio in Windows and wants something similar; hence why I mentioned Anjuta ;).

Ah, I didn't think of it from that angle.

There is another option: Qt and Qt Designer.  Free under GPL.  It the closest to Visual C++ and MFC I can think of.

---

