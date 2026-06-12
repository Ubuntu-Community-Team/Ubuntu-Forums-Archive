---
title: "Alternative to gtkmm + glade + c++ ?"
date: 2011-01-18
forum: Programming Talk
---

### Post by skippersd on 2011-01-18
Greetings!

I'm fairly new at programming, but as my command line programs were ok, I tried to make a c++ app with GUI.  And failed. 

My queston is, can someone either point me at an other language, with better (easier) GUI creation for Ubuntu? My studies involve quite bit of matemathics, and I don't have to update my apps, so my interests lie that way.

Or post some up to date working code made with c++/glade/gtkmm? I would figure out eventually, but most of the tutorials are outdated. A little more advanced than a 'Hello World' would be perfect, because i have nothing to start from.

Thanks!

---

### Post by worksofcraft on 2011-01-18
> **skippersd said:**
> Greetings!

I'm fairly new at programming, but as my command line programs were ok, I tried to make a c++ app with GUI.  And failed. 

My queston is, can someone either point me at an other language, with better (easier) GUI creation for Ubuntu? My studies involve quite bit of matemathics, and I don't have to update my apps, so my interests lie that way.

Or post some up to date working code made with c++/glade/gtkmm? I would figure out eventually, but most of the tutorials are outdated. A little more advanced than a 'Hello World' would be perfect, because i have nothing to start from.

Thanks!
I fully agree with your sentiments about gtkmm. I found it so ghastly to work with that I made my own wrapper class for the GTK widgets and it is much easier to use.

It is so simple that it is just a single module in my enhanced internationalization and localization library [cs_lib-0.0.1.tar]("http://code.google.com/p/speaknumber/downloads/list"). The archive contains several very simple example programs and there is documentation in html_doc.tar at the same site (if you just want to use a gui you can skip the one on internationalization.html)

I know it doesn't have all the capabilities of gtkmm currently, but if you look in the gui module and see how simple it is inheriting from a common widget template and using gtk builder and [glade]("http://glade.gnome.org/") to create the interfaces I think you would have few problems adding anything you might need and be in full control too :)

---

### Post by Nytram on 2011-01-18
> **skippersd said:**
> Greetings!

My queston is, can someone either point me at an other language, with better (easier) GUI creation for Ubuntu? 



Java + Netbeans

---

### Post by Simian Man on 2011-01-18
QT + QTCreator.

---

### Post by sum1nil on 2011-01-18
Monodevelop and GTK-sharp

---

### Post by nvteighen on 2011-01-19
What is the problem?

1. Is it that the gtkmm library doesn't provide the functionality you want?
2. Is it that the Glade GUI designer doesn't work for you or that you find it hard to use?
3. Is it that you don't fully understand or don't like C++?

All three are completely different problems with different solutions. Respectively:

1. Qt. Assuming you want to work with C++, Qt is the best option because it's a C++ native library. GTK+ is a C library and gtkmm is a C++ wrapper that leads to some problems... A lot of people just don't like how it feels, and yes it does feel weird. (This doesn't seem to happen with the original GTK+ C library).

2. Either you code the GUI by hand or you switch to Qt and use QtCreator. Again, I'm assuming here you want to use C++.

3. Well, IMO C++ is a mess that also has its part on why gtkmm is so hard. You say you had written command line programs and that you're new to programming. So I ask: did those programs use OOP concepts and all the usual "C++-ish" stuff (STL, templates, classes, etc.)? If this is your issue or part of it, I highly recommend you to continue learning the language. Otherwise, you'll have a hard time using any C++ library there is out there.

---

### Post by skippersd on 2011-01-19
Thanks for the quick replies!

nvteighen, i'm just getting into programming, and c++ is the only that i've learned so far. My problem is, i'm getting used to simple code line programs, and i can make a GUI in glade, but i just can't understand how to make it work. 

so far the QT seems to be the best solution, i'm looking into it right now

Update:I've looked into it, it seems more logical to me. So the new question is, can someone point me at a decent QT tutorial?

---

### Post by worksofcraft on 2011-01-19
> **skippersd said:**
> Thanks for the quick replies!

nvteighen, i'm just getting into programming, and c++ is the only that i've learned so far. My problem is, i'm getting used to simple code line programs, and i can make a GUI in glade, but i just can't understand how to make it work. 

so far the QT seems to be the best solution, i'm looking into it right now

Update:I've looked into it, it seems more logical to me. So the new question is, can someone point me at a decent QT tutorial?

There is one that builds a simple game with a cannon... but I think you have to start here [http://doc.trolltech.com/4.3/tutorial-t1.html](http://doc.trolltech.com/4.3/tutorial-t1.html)

---

