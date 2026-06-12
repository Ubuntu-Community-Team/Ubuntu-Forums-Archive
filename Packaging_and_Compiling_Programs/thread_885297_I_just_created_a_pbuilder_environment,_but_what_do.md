---
title: "I just created a pbuilder environment, but what do I do with it now?"
date: 2008-08-09
forum: Packaging and Compiling Programs
---

### Post by JasonSpradlin82 on 2008-08-09
Ok I am trying to go through the packaging guide so that I can start (eventually) helping out in the Ubuntu community... Ones I kind of figure out what I'm doing, I am going to see about getting a mentor...

My question is this... I'm trying to learn what I'm doing... And the packaging guide tells me HOW to do something, but does not tell me what exactly it is that I am doing...

Example:

to create a pbuilder environment, run

sudo pbuilder create --distribution <ubuntu_version> \
        --othermirror "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <ubuntu_version> main restricted universe multiverse"

Ok.... I did that.... what did I just do?  After searching around TRYING to figure it out, I see that /var/cache/pbuilder/base.tgz contains the filestructure of what I assume is a complete Ubuntu install... But my question now is, what do I do with this?  What is it for?  What can it accomplish?  

I don't care that by typing the above commands I can create a build environment if I don't know what to do with it.  I understand that the idea is for it to exist as an installation that thinks it is installing to a root directory of the computer, so that none of my installed files get messed up... but what does one do with the base.tgz now?

---

### Post by Stemp on 2008-08-10
As you figured out, you just created a nice clean minimal install of Ubuntu or Debian.
The main goal is to create package in a clean environnement (minimal).

---

### Post by JasonSpradlin82 on 2008-08-10
I understand the goal... but is this something that can now be worked on, or can a person work IN the .tgz file?

Is this just one step in the process?  For instance... is this base.tgz good for anything as it is, or does a next step have to be done to it.  

Does one get a program that accesses the base.tgz as if they were using it as its own filesystem and then test things out on it?  

This was a test build, of course, but if it weren't, what would be the purpose of what I just did... I understand i "created a nice clean minimal install of Ubuntu or Debian"... What does one do with it now?  what is its purpose in life?

---

### Post by Stemp on 2008-08-10
Forget the .tgz file. It's just a file containing your pbuilder environnement.

If you want to build a package, you have two choices :
1/ Build it on your installation, but it's not a clean install. You installed many packages so you can't be sure you're package will work on any Hardy system.
2/ Create it on your pbuilder environnement, so you will be sure it will work on any Hardy system.

There is also another reason to create a pbuilder environnement, you can create an Intrepid environnement and still running Hardy.

Anyway you just need it for building packages.
For more informations, look at chroot ;)

---

### Post by JasonSpradlin82 on 2008-08-10
Thanks for the help.

So I guess what i don't understand is what is the build for... In theory would anybody be downloading this .tgz to install something in their computer?  Is it like a .deb package that makes it so hardy users can install the software without needing to download other files?  would somebody uncompress this file directly to their root folder so that every files gets placed automatically?  

I understand the need to make software installations universal, but, what part of the process is this?  are there more steps to getting a software installation ready to be downloaded and installed on a similar system?

---

### Post by JasonSpradlin82 on 2008-08-10
Or look at my question this way... imagine i was to say to somebody who programs, but not in linux or unix, that "i built my software installation into a package on my computer, etc, etc... i've got the finished product as base.tgz..."

I expect they would say... "what's base.tgz?  Why did you package it... is it like an .msi file in windows? "

---

### Post by JasonSpradlin82 on 2008-08-10
Sorry, i would just got on the IRC MOTU channel, but I'm behind a firewall and don't have access to open or close ports.

jason

---

### Post by JasonSpradlin82 on 2008-08-10
> **Stemp said:**
> Forget the .tgz file. It's just a file containing your pbuilder environnement.


Just re-read your response and saw this again..... (i'm tired... and that makes me say whatever thoughts pass through my head, without any filter)...

Ok, so it is just a step in the process, and therefore, by itself, is not much use to anybody?  Would I want to take this base.tgz and turn it into something else... or do something else with it, now that it is built?

I've got that it is a file containing my pbuilder environment, which is a clean environment that building can be done in without all kinds of other problems that could be caused by building live on my fs.

But I'm not sure what I have accomplished, within the bounds of the complete package process, if there is more to the process, that is.

---

### Post by Stemp on 2008-08-10
You're over focused on this base.tgz file :D
Forget it, lets pretend it doesn't exist and anyway you will never use it.

The goal of a pbuilder environnement (or a chroot) is just to have a virtual clean installation of another debian/ubuntu. And this virtual environnement is used to build packages. 
If you don't build packages (.deb files) you don't need a pbuilder environnement.

---

### Post by JasonSpradlin82 on 2008-08-10
I want to be building .deb packages, when I get that far... I just didn't understand why the packaging guide had me create the build environment...

I'm trying to get all my ducks in a row so that i can hopefully jump in and start contributing some, but I rarely like to do anything just because somebody (or some packaging guide) said to, without telling me what it was accomplishing and to what end.

I guess i can just continue my reading of the packaging guide and maybe it will make more sense down the road.

Thanks for putting up with my odd questions!

---

### Post by bobbocanfly on 2008-08-10
Pbuilder builds a minimal version of Ubuntu, which is used to test build package (Make sure you got Build-Depends(-Indep)) correct. It also makes sure that your package actually builds correctly, which saves the actual build servers wasting time attempting to build a broken package.

---

