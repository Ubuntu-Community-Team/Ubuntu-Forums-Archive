---
title: "Does anybody use Qt from trolltech?"
date: 2006-12-15
forum: Programming Talk
---

### Post by dave_567 on 2006-12-15
I was just reading about it and it sounds really good.  Not much talk on it here.  

Cross compiling with the same code sounds great if it is as smooth as they claim.  Any drawbacks that are not in the reading?

.

---

### Post by loell on 2006-12-15
its dual licensing could be the main drawback.

---

### Post by po0f on 2006-12-15
dave_567,

If you use/have used Kubuntu, or any KDE app, you have used Qt.  Qt is to KDE as GTK is to GNOME.

As far as development goes, it is a bear.  I found it very confusing, as Qt comes from pre-Standard C++ dark days!  Actually, I find *all* GUI development confusing.  My current project uses NCurses.  :)

---

### Post by lnostdal on 2006-12-16
> **dave_567 said:**
> I was just reading about it and it sounds really good.  Not much talk on it here.  

Cross compiling with the same code sounds great if it is as smooth as they claim.  Any drawbacks that are not in the reading?

.

The biggest drawback is that it is implemented in C++ (part of it isn't even standard C++) which has a lot of problems.

I'd head for GTK+ instead. If you're into Python; PyGTK is great.

---

### Post by g8m on 2006-12-16
I am stil confused. I tried gtk+, gtkmm, wxwidgets, ncurses and.. Qt (3 and 4). I know there are licence issues, but Qt feels solid. With only a few lines of codes you make applications that work. No hundreds of lines to implement a mysql connection, just a few lines connect, query, next, it works. So after some sidesteps trying to understand gtk+ and gtkmm I am back at Qt and loving it. I like the way signals and slots works. I don't like the fact that i have to precompile it with moc. I change a field on a screen, emit field changed and on another screen the field gets changed too. I like the model/view approach, although it's still is very new. I like the way html is integrated, just make up some html text, hang it in a label and your text is displayed like a web-page. 

It probably works under gtk+/gtkmm/wxwidgets and even ncurses, but it only takes a few lines under Qt and a lot more under the other libraries.

Under Gnome i would choose for Gtk+, because it will integrate better, under KDE i will choose Qt.

But I would definitely choose for C++. The class definitions rock.

---

### Post by dwblas on 2006-12-17
Flame me if you want, but I think it is all personal preference.  With each you have to define which widgets to use, put them in a container, define call-backs, etc.  Pick one and use it.
Edit: If you are just starting out, pick one that has a lot of examples and use it.

---

### Post by protocoder on 2008-11-11
I have downloaded QT and installed, i have windows XP here and all i get after installation to a place where g++ exe is there is documentation and files. Please can you tell me what should i do to use QT as IDE .. compile and build and try some GUI applications.. 
1. Give some references and help to create the applications .

Regards
--P

---

### Post by Bichromat on 2008-11-11
> **protocoder said:**
> I have downloaded QT and installed, i have windows XP here and all i get after installation to a place where g++ exe is there is documentation and files. Please can you tell me what should i do to use QT as IDE .. compile and build and try some GUI applications.. 
1. Give some references and help to create the applications .

Regards
--P

First off, you should create new threads instead of posting in dead ones.
I assume that when you say "Qt as an IDE" you're talking about Qt Creator? If so, I'm pretty sure you need to install it separately. Bear in mind that it is still in development.

---

### Post by samjh on 2008-11-11
Ugh, thread necro. :(

---

