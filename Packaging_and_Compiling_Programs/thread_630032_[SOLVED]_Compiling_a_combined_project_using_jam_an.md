---
title: "[SOLVED] Compiling a combined project using jam and make"
date: 2007-12-02
forum: Packaging and Compiling Programs
---

### Post by derrick81787 on 2007-12-02
Hello, everyone.  I've been working on creating a GTK gui for the HandBrake dvd ripping utility.  It's pretty much done, and it works, but I would like to make the install process a little easier.  As of now, to install you need to compile my slightly modified version of HandBrakeCLI (renamed to ghandbrake-backend), which uses jam, copy the resulting binary to somewhere in the system path (such as /usr/bin) and then compile my program using make and make install.

My Makefile was handled by the Glade Interface Designer, but I would like to somehow modify it so that I can have HandBrake's source as a subdirectory and that running make and make install on my source would also compile HandBrake.  The problem is that HandBrake uses jam, and my project uses make.  Does anyone know how I can make this work?  The next step I would like to take is to make a .deb package, but I figure I should get the compiling process to work well first.

Thank you all for your help,
- Derrick

---

### Post by dholbach on 2007-12-03
This is hard to work out if there's no source to look at.

[http://wiki.ubuntu.com/UbuntuDevelopment](http://wiki.ubuntu.com/UbuntuDevelopment) for how to get your software included in Ubuntu once you want to get it included.

---

### Post by derrick81787 on 2007-12-03
Sorry.  I've been trying to get my source online, but I've been having problems.  You can temporarily get the source [here]("http://ews.uiuc.edu/~dwright3/ghandbrake.tar.bz2").  I'll be moving it sometime soon, but when I do, I'll post the new link here.

By the way, when you look at the source for ghandbrake-backend, you'll see that it uses jam and make.  The make process uses precompiled binaries, though, and I don't know if it works for i386, but I'm on amd64 and it throws an error.  So basically, make is pretty much useless for it (as it is now), and you have to compile using jam, hence my problem.

Thanks again for all your help.

- Derrick

*****Edit:**  I forgot to mention that if you wait to install and try out my program, it depends on lsdvd.  You can just install it from the repositories.  For compiling, it also depends on libxml and having a the gnome headers (or at least gtk headers).

---

### Post by derrick81787 on 2007-12-04
Well, I worked on it a little more, and I think I got it.  The whole compiling and installation process works, but it could probably still use some work.  Anyway, I'm going to start working on packaging it, so we'll see how that goes.  Thanks for the help.

- Derrick

*****Edit:**  Here's my Makefile that just runs jam when it's called.  Someone who knows what they're doing could probably make it a little more robust and professional, but if someone else is having this same problem, this does do the job.  Note that this isn't my main Makefile.  It's just a Makefile that I use in my subdirectory containing HandBrake's source code.  Anyway, here it is:

Makefile:
```
#####################################################
#                                                   
#   Makefile                                     	 
#																# 
#	 	a wrapper around jam which calls jam in 		 
#	 	order to compile ghandbrake-backend.			 
#																# 
#   Written December 2007 by Derrick Wright.			 
#																#	 
#	 This file is part of the ghandbrake source		 
#	 code.														 #
#	 														
#
#####################################################

# HandBrakeCLI is compiled using jam, and so this allows
# ghandbrake and ghandbrake-backend to both be compiled
# all in one step using make.

# If anyone knows of a more professional way to achieve
# this, please either let me know or just change it
# yourself.

# the main compile step should call jam
all :
	jam

# the install step
install :
	./install-sh

# the uninstall step
uninstall :
	./uninstall-sh

# make clean should call jam clean
clean :
	jam clean

# make distclean should also call jam clean
distclean :
	jam clean
```

---

