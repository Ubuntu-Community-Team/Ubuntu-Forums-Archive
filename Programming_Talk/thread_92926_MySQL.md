---
title: "MySQL"
date: 2005-11-20
forum: Programming Talk
---

### Post by Robgould on 2005-11-20
I am doing some programming in windows with visual basic and MySQL.  I use Ubuntu as my "fun" system, but do most of my serious stuff on windows because I familliar with it.  I was wondering if there was an IDE similar to visual basic.net available for Ubuntu?  I would like to stick with MySQL, uslees there is an IDE that works very well with some other database.  I would like to kind of gradually try to learn to do the same thing in Linux that I do in windows.  Thanks for the help.

---

### Post by Burke on 2005-11-21
AFAIK, the only thing on Linux similar to VB.NET is Glade ([http://glade.gnome.net)](http://glade.gnome.net)).  Glade is an interface builder that can use C, C++, Python, or Ada95.  You'll find it in synaptic. Google for 'glade tutorial' and try out the first result... I found it to be a good introduction.

You may need to install some 'linux-headers'.  Open up Synaptic, then search for 'linux-headers'.  You should see a few variations on the same version number.  Just install the one without an extension (eg. -386) and then pick the one that matches your architecture. (Probably the -386 one).  Install both, and as far as I remember, Glade should work.

You'll also need to install gcc/g++. There are other tutorials for that .... [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by cactus on 2005-11-21
If you are familiar with VB, you might give gambas a try. 
Never tried it myself, but I heard it isn't too terrible.

I would suggest python or ruby myself though. Just giving you options and things to think about...

---

