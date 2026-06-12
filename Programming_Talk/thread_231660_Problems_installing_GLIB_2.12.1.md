---
title: "Problems installing GLIB 2.12.1"
date: 2006-08-07
forum: Programming Talk
---

### Post by theDentist on 2006-08-07
Hi all,
more problems, I'm trying to update GLIB to version 2.12.1 but I failed at the make stage with the following error

Making all in gobject
make[2]: Entering directory `/home/peter/glib-2.12.1/gobject'
Makefile:214: *** missing separator.  Stop.
make[2]: Leaving directory `/home/peter/glib-2.12.1/gobject'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/peter/glib-2.12.1'
make: *** [all] Error 2

Can someone tell me what has happened here. The configure stage went with no errors (a first for me!!) but now I'm met with this. I have yet to install any package successfully from the command line on this installation of Ubuntu.  I'm new to Linux, Is it always this problematic.  I'm updating GLIB because during another installation attempt of another package it told me my GLIB needed updating to a version above 2.0.0.  I have installed Glade successfully throught the GUI of Add/Remove Programs but of course I can't compile any of the programs I write.  Am I missing an important package in my Ubuntu installation.  I have programmed a lot in VC++ in windows and never had such hassle!

Hopefully,   Peter

---

### Post by jeff_ on 2006-08-07
I'm no expert, but with Ubuntu I think almost all packages should be handled/installed through the Synaptic Package Manager under System > Administration. Try installing libglib-2.0-dev. What is the error Glade gives you when trying to compile?

Windows is streamlined to be easier to use than linux (Microsoft makes the OS and IDE), but once you get the hang of linux it can be pretty smooth sailing. I think it's kind of like learning a new language, at first everything is confusing and doesn't make sense, but as you learn more and more it becomes easier to figure new things out and make progress on your own, especially if you're a programmer. So I'd say stick with it for a while and it should be easier.

---

### Post by theDentist on 2006-08-08
Thanks for the valuable advice!!.  I didn't realise Ubuntu has that facility for installing packages.  All my previous experience has been C/C++ and Visual Studio in windows so all this is confusing.  At least my knowledge of C is going to help as it seems very common in the linux world. (Well, I'm only an amateur, so I better qualify the word "Knowledge")  :D 


Peter

---

### Post by theDentist on 2006-08-08
I forgot in my post to tell you the error Glade gives me.  When I type "./configure" at the terminal it tells me that no such file exists, in other words, it doesn't recognise the command.  However, in other packages that I've used the "configure" command, it is recognised and been successful.  Yes, I am in the correct directory, the project directory.

Hope this helps

Peter

---

### Post by theDentist on 2006-08-08
I've just tried again to compile my Glade project (called project1, it is a simple window, no code written) and the following message printed in the terminal after typing ./configure 

./configure: line 1250: syntax error near unexpected token `project1,'
./configure: line 1250: `AM_INIT_AUTOMAKE(project1, 0.1)'

Any ideas

Peter     :(

---

