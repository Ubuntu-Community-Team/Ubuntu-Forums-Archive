---
title: "C - Why a lot of people today still point and use C a lot?"
date: 2015-03-18
forum: Programming Talk
---

### Post by flaymond on 2015-03-18
Hello, I cannot hold my curiosity anymore about this amazing twin, C & C++. Whenever I'm doing some poll on/in any open chat,forum and polls, about which one you use more and love more, a lot of people still point to C ? It's surprising me of how this nice and small programming language is attractive to others. I used both C and C++ in my task, and indeed C is much clean and small, but I thought C++ is better and people say it's a superset of C. So why do people use C more often than C++? I just wanna get some opinions from you guys.

Thanks in advance. :D

---

### Post by Skaperen on 2015-03-18
i use [C]("http://en.wikipedia.org/wiki/C_%28programming_language%29") for a lot things but for higher level stuff i skipped over [C++]("http://en.wikipedia.org/wiki/C%2B%2B") and use [Pike]("http://en.wikipedia.org/wiki/Pike_%28programming_language%29") and [Python]("http://en.wikipedia.org/wiki/Python_%28programming_language%29").  now days if i only use [C]("http://en.wikipedia.org/wiki/C_%28programming_language%29") for low level stuff and i don't need [C++]("http://en.wikipedia.org/wiki/C%2B%2B") for these.  i started my programming experience in [assembly language]("http://en.wikipedia.org/wiki/IBM_Basic_assembly_language_and_successors") on [mainframes]("http://en.wikipedia.org/wiki/IBM_System/360").

IMHO OO programming should focus more on the programmin effort.  i see languages like [C++]("http://en.wikipedia.org/wiki/C%2B%2B") as hacks.

---

### Post by flaymond on 2015-03-18
How about GUI building task? Python and Pike still do the job well for you? (I thought it's very slow)

* That was my first time I heard about Pike, I looked at the link...and wow! I never know that there is a dynamic and intrepreted language that almost same to C in syntax. It's seems very "familiar" & good to use.

---

### Post by The Cog on 2015-03-18
I don't know pike, but I guess the same argument holds true as with python: It's not horribly slow because very little of the actual work is done in python. Python is the stuff directing what goes on, but is making calls into C libraries, whcih is where all the nitty-gritty hard work happens. Like when my wife tells me to do the washing up - She says "do the washing up", and I do the washing up.

---

### Post by flaymond on 2015-03-18
[QUOTE=The Cog] 			 				[INDENT] 					I don't know pike, but I guess the same argument holds true as with  python: It's not horribly slow because very little of the actual work  is done in python. Python is the stuff directing what goes on, but is  making calls into C libraries, whcih is where all the nitty-gritty hard  work happens. Like when my wife tells me to do the washing up - She says  "do the washing up", and I do the washing up. 				[/INDENT] 			
  			   		
[/QUOTE]

That sounds like Python itself is the UI to access the C library, with clear and easier code to read and type? Am I right?

By now, I tried to focus at C++. C++ is too big & hard for me, planning to skip C++ (sometimes I can understand the Java code with 200 lines of code typed but not C++!). I'm not hardcore or die-hard in game programming, I just wanna start something useful to use by others as newbie programmer. One more question -

***Does C++ is the best language for GUI building?***

---

### Post by slickymaster on 2015-03-18
> **The Cog said:**
> I don't know pike, but I guess the same argument holds true as with python: It's not horribly slow because very little of the actual work is done in python. Python is the stuff directing what goes on, but is making calls into C libraries, whcih is where all the nitty-gritty hard work happens. Like when my wife tells me to do the washing up - She says "do the washing up", and I do the washing up.
:lolflag:
Sorry for stepping in with an off-topic post, but this got to be one of the funniest and better sketched metaphors I've heard, in what programming languages are concerned.

---

### Post by Skaperen on 2015-03-18
> **InterProg said:**
> How about GUI building task? Python and Pike still do the job well for you? (I thought it's very slow)
i've not done any GUI apps so my language preferences should be viewed in that context.

> **InterProg said:**
> * That was my first time I heard about Pike, I looked at the link...and wow! I never know that there is a dynamic and intrepreted language that almost same to C in syntax. It's seems very "familiar" & good to use.
i first encountered this as [LPC]("http://en.wikipedia.org/wiki/LPC_%28programming_language%29") and the similarity to C got me into [LPmud]("http://en.wikipedia.org/wiki/LPMud")  programming for a while.

for fun here is a Pike [one-liner]("http://en.wikipedia.org/wiki/One-liner_program") in the form of a Unix shell command:
```
pike -e 'for(array p=({1});;p=(p+({0}))
[*]+(({0})+p)
[*])write(p
[*]+"\n");'
```
it calcuates [Pascal's triangle]("http://en.wikipedia.org/wiki/Pascal%27s_triangle") to high precision (how much memory do you have).

---

### Post by Lars Noodén on 2015-03-18
> **InterProg said:**
> ***Does C++ is the best language for GUI building?***

I've seen people do useful stuff quickly with [QML](http://doc.qt.io/qt-5/qtqml-index.html).  If you would like to avoid C++ with that, you could use [Qt Jambi](http://qtjambi.org/) with Java.

---

### Post by flaymond on 2015-03-18
[QUOTE=Lars Nooden]I've seen people do useful stuff quickly with [QML]("http://doc.qt.io/qt-5/qtqml-index.html").  If you would like to avoid C++ with that, you could use [Qt Jambi]("http://qtjambi.org/") with Java.[/QUOTE]

I'm using the Qt tk too. However, using C++ with it is very hard to understand(for me) when it become more complex because C++ teach you 2 style of paradigm, OO's and procedural native C (I know I can skip it, but still...the C++ STL disturbing me).  Qt Jambi, that sound good :D. I will try that out.

* Maybe, I just wanna rush to learn everything at once. However and sadly, I use C++ more than other programming language..still can't pick it up...when using C++...I feel something incomplete.....

** Is PyQt also good? Will it effect the speed? :O

Thanks.

---

### Post by benrob0329 on 2015-03-18
Just so you know, Qt is only for open-source applications. GTK+ is for open-source and commercial applications. Although I do prefer open-source.

---

### Post by Lars Noodén on 2015-03-18
> **benrob0329 said:**
> Just so you know, Qt is...

Qt has both LGPL and proprietary versions.  If you are going to make proprietary software, you have to sign up at the beginning, if I recall correctly.  (It's been a few years since I looked).  But if you are going to make LGPL from the beginning, it's not an issue.

---

### Post by jmburbach on 2015-03-18
Qt is LGPL, as is GTK. They both can be used for open source or proprietary closed source applications. Commercial Qt licenses are for the cases where your application cannot meet requirements of LGPL...such as you modified Qt itself and don't want to provide your changes, or you link statically...or just want commercial support...

---

### Post by ofnuts on 2015-03-18
> **benrob0329 said:**
> Just so you know, Qt is only for open-source applications. 

You should read [this](http://www.qt.io/licensing/).

---

### Post by ofnuts on 2015-03-18
> **InterProg said:**
> ***Does C++ is the best language for GUI building?***

The general consensus is that GUI stuff is more efficiently done with OO techniques. This in turns usually means OO languages. With a fast CPU or a not too demanding UI (mostly standard widgets...) most languages are up to the task. But for high performance you need an OO language that can generate very efficient code and there is much less choice.

---

### Post by benrob0329 on 2015-03-18
> **ofnuts said:**
> You should read [this]("http://www.qt.io/licensing/").

True, I forgot to mention that point, oops.

---

### Post by flaymond on 2015-03-18
[QUOTE=benrob0329]Just so you know, Qt is only for open-source applications. GTK+ is for  open-source and commercial applications. Although I do prefer  open-source.[/QUOTE]

I thought Qt also provide other license too? The OSS one is the community version, right?

* This is the last 2 question for this thread, I promise.

***1. Is GTK is completely written in C ? I wanna avoid C++ as much as I can for now, I want to learn the fundamentals without disturbed by the damn big STL of C++. I only found only 2 frameworks that can be used with C in GUI building task, LibX11/XLib and GTK. I understand and I can see why OOP's give such amazing option in GUI programming***, ***but still it's too big for me...and for now.***

***2. How to install GTK package/dependencies/modules to start developing GUI especially from terminal.***

---

### Post by benrob0329 on 2015-03-18
> [COLOR=#000000]I thought Qt also provide other license too? The OSS one is the community version, right?[/COLOR]
Yes, I forgot to mention that point. :oops:

[https://developer.gnome.org/gtk3/stable/gtk-getting-started.html](https://developer.gnome.org/gtk3/stable/gtk-getting-started.html) is a tutorial on the basics of GTK+, and libgtk-3 is installed by default.

---

### Post by flaymond on 2015-03-19
Ahh found out of how to install the packages to dev with GTK+.

```
sudo apt-get install gnome-devel
```

That would do to install Glade, dependencies, iPython, documents and tutorials and also Anjuta IDE.


Thanks for all of your feedback and opinions! You guys amazing! :KS

---

### Post by ofnuts on 2015-03-19
> **InterProg said:**
> I thought Qt also provide other license too? The OSS one is the community version, right?

* This is the last 2 question for this thread, I promise.

***1. Is GTK is completely written in C ? I wanna avoid C++ as much as I can for now, I want to learn the fundamentals without disturbed by the damn big STL of C++. I only found only 2 frameworks that can be used with C in GUI building task, LibX11/XLib and GTK. I understand and I can see why OOP's give such amazing option in GUI programming***, ***but still it's too big for me...and for now.***

***2. How to install GTK package/dependencies/modules to start developing GUI especially from terminal.***

On the contrary, if you want to learn how to develop GUIs, with OO languages you can remain at the "fundamentals" levels without getting involved in gory technical details. And the compiler will spot many problems for you. If C++ is too "big" for you then use Java.

---

### Post by Skaperen on 2015-03-20
> **InterProg said:**
> ***Does C++ is the best language for GUI building?***
it was (maybe still is) a good choice for OO GUI development where speed of the app is still very important.  for "a few good apps" this is probably a winner.  for this day and age with languages like Python, Pike, Ruby, and Perl, and faster CPUs, would C++ even be created? speed of the development process is becoming a more important goal. what development language is in your *future*?

---

### Post by flaymond on 2015-03-20
> **Skaperen]it  was (maybe still is) a good choice for OO GUI development where speed  of the app is still very important.  for "a few good apps" this is  probably a winner.  for this day and age with languages like Python,  Pike, Ruby, and Perl, and faster CPUs, would C++ even be created? speed  of the development process is becoming a more important goal. what  development language is in your *future*?                                                                                              [INDENT]                                      Last edited by Skaperen said:**
> 


I gonna say that your words are very "powerful" and deep. When I read the last few words, suddenly my mind go to other "dimension" and thinking why new language created and most of them today..are intrepeted one. Your reply really make me "open my eye". This is sound ironic, but it's not. 

=d>=d>=d>

---

