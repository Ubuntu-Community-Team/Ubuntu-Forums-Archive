---
title: "{Beginner} GTK+ Programming"
date: 2010-02-12
forum: Programming Talk
---

### Post by madmax.santana on 2010-02-12
I want to learn designing applications for GNOME and Ubuntu. Some inexperienced friend tipped me that GTK+ libraries are needed in order to programme GUI apps in GNOME. However, I am totally blank as to details.

I would really be grateful if people could help me in following aspects.

1- I need a beginners-guide to Programming with GTK+ in C++ (that's the only programming language I am familiar with).

2- I shall need guidelines on which compiler to use for purposes mentioned above. G++ is good but a GUI suite would be better (not necessary though, I don't hate command line either :))

3- I shall need an explanation on what exactly is GTK+, in simple words. 

I tried approaching the websites on GTK+ but they are all technical words. In my current opinion GTK++ is a bunch of libraries (*.h files) residing in my system that I can access through #include<> or #include" ", just like when I started learning programming in win32 envoirnment, I would use #include<windows.h> to call certain functions and name different data structures.

Also I don't know if GTK+ comes with Ubuntu or I have to install packages to start compiling applications. And if they are already in my system, how to I use these libraries, I mean where are they located?

Just for fun, I tried #include <gtk>. It appears invalid though.... ;)

Hope I don't look dumb asking these questions... ;) Because I think it is not something that a normal person should know. And programmers are special persons ;)

---

### Post by Sinkingships7 on 2010-02-12
I don't know much about it myself, but I can help you get started with some Google keywords.

First, if you're set on using C++, then you want to install and learn how to use the gtkmm wrapper for GTK+. GTK+ was designed with C in mind, so it needs gtkmm in order to interface with the language.

Second, you can use the [Glade Interface Designer]("http://glade.gnome.org/") to help you design quick and easy GUIs for your programs.

That's really about all I know. Learning a library like GTK+ takes time, but stick to it and you'll be up and running soon. Good luck!

---

### Post by diesch on 2010-02-12
> **madmax.santana said:**
> I want to learn designing applications for GNOME and Ubuntu. Some inexperienced friend tipped me that GTK+ libraries are needed in order to programme GUI apps in GNOME. However, I am totally blank as to details.

I would really be grateful if people could help me in following aspects.

1- I need a beginners-guide to Programming with GTK+ in C++ (that's the only programming language I am familiar with).


[http://www.gtkmm.org/](http://www.gtkmm.org/) is the homepage of the GTK C++ bindings, I guess you'll find some docs there.

If you can read German: I'm writing a [ beginner's guide  to GTK for Python](http://www.florian-diesch.de/doc/python-und-glade/). I guess most GTK-related things are quite similar in C++


> **madmax.santana said:**
> 
3- I shall need an explanation on what exactly is GTK+, in simple words. 


A library for creating GUI apps. It's written in C, but there are bindings for other languages, like C++

> **madmax.santana said:**
> 
Also I don't know if GTK+ comes with Ubuntu or I have to install packages to start compiling applications. And if they are already in my system, how to I use these libraries, I mean where are they located?


GTK and its C++ bindings (libgtkmm-2.4-1c2a in Karmic) are installed by default in Ubuntu.

---

### Post by nvteighen on 2010-02-13
Also, the documentation is available at the repositories... Install it and install the great DevHelper program, which is a nice offline documentation browser.

---

