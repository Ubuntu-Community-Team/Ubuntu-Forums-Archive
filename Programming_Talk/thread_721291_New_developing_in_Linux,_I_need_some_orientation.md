---
title: "New developing in Linux, I need some orientation"
date: 2008-03-11
forum: Programming Talk
---

### Post by dmendizabal on 2008-03-11
I need to have some clarification about where to start to make my software in Linux/Ubuntu. 

I've been researching Gnome.org and the tons of documentation they provide, but I'm still lost.

I understand the concept for the Gnome architecture and the many libraries that create the whole system: GTK++, GDK, GLib, GConf, etc.
Then I read about gtkmm that seems to be Gnome/GTK++ binded for C++.

But I need the following:
1) A good IDE with UI support to make my life easy. I was used to using Eclipse on Windows and I wonder if I can continue using it. I didn't have to worry to create makefiles or to memorize lot of command line parameters to compile. It was done automatically by Eclipse and the parameters were easy to assign using dialogs.
The IDE should include the editor, debugger, tool to create dialogs (probably using the assistance of Glade), etc.

2) I would like to get a C++ programming environment. It means that all the GTK++ for instance would be completely object orient.

3) Clear and complete help for the API.


Is there a package to download from the repositories that can give me exactly what I need?
Please give me some hints.

---

### Post by Can+~ on 2008-03-11
Tip: When you're on ubuntu, first you look on your repository for software.

Open synaptic, Ctrl+F, "Eclipse". Installing the eclipse pack will carry all the dependencies with it. The c++ plugin is already there. And for using GTK, indeed, use glade. 

For everything else, google is your friend, unless you could make specific questions, then we (as in, anyone on the forum) could help you out

---

### Post by jespdj on 2008-03-11
There's a package gnome-devel which installs GNOME development tools, including the Anjuta IDE and devhelp, which contains a lot of developer documentation. Also see gnome-devel-docs.

For many libraries there is a ...-dev version of the package that contains the C/C++ header files etc. that you need if you want to use the library in your own programs. Look around in Synaptic.

---

### Post by dmendizabal on 2008-03-17
If I understand, there are 2 alternatives for development: 
1) Eclipse and its plug ins
2) gnome-devel (tools to program with gnome)

Which one is the recommended to create software in Ubuntu using C++?

---

### Post by escapee on 2008-03-17
You have more than two choices for sure.

The IDE's they listed:
Eclipse
Anjuta

Some others:
Code::Blocks
Geany
KDevelop


Make sure you have the "build-essential" package installed (has the necessary compilers and libraries).

---

### Post by Sockerdrickan on 2008-03-17
I'd recommend Geany.

---

### Post by Sinkingships7 on 2008-03-17
i think you'd love geany
```
sudo apt-get install geany
```

copy and paste that into the terminal.

i've been looking for the exact same things you're looking for and just recently fell in love with geany.

---

### Post by dmendizabal on 2008-03-17
Thanks for the posts.
I will review these alternatives. Only one more thing, I want to think in the future and in this sense the final IDE I decide to use should fulfill my expectation. I wouldn't like to get in love with one of them and then it wouldn't be helpful for me later.
Based on this, I'm being more specific below explaining what is the scope of development I'm planning to do:

1) Ubuntu 
2) Ubuntu mobile 
3) Maemo (Nokia tablet)

As you see, I would like one IDE that could manage all these platforms (if it were possible).
All of them use gnome, GTK++ so I assume it would be possible to find on tool for all??

---

### Post by LaRoza on 2008-03-17
> **dmendizabal said:**
> Thanks for the posts.
I will review these alternatives. Only one more thing, I want to think in the future and in this sense the final IDE I decide to use should fulfill my expectation. I wouldn't like to get in love with one of them and then it wouldn't be helpful for me later.
Based on this, I'm being more specific below explaining what is the scope of development I'm planning to do:

1) Ubuntu 
2) Ubuntu mobile 
3) Maemo (Nokia tablet)

As you see, I would like one IDE that could manage all these platforms (if it were possible).
All of them use gnome, GTK++ so I assume it would be possible to find on tool for all??

Gedit?

---

### Post by kknd on 2008-03-17
> **Tux0r said:**
> I'd recommend Geany.

+1.

I did a lot of GObject / gtk / cairo codding last months, and geany fit like a glove for the job.

---

### Post by jespdj on 2008-03-18
> **dmendizabal said:**
> If I understand, there are 2 alternatives for development: 
1) Eclipse and its plug ins
2) gnome-devel (tools to program with gnome)

Which one is the recommended to create software in Ubuntu using C++?
No, these two are not really alternatives. Eclipse is an IDE, gnome-devel is an Ubuntu package that contains a set of tools, programs and libraries to help you with programming GNOME applications. You'll probably need many of the things in gnome-devel, no matter what IDE or code editor you're going to use.

The C++ interface to GTK+ is [gtkmm](http://www.gtkmm.org/).

---

