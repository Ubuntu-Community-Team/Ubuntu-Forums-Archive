---
title: "n00b that needs to compile some python into a .deb"
date: 2010-02-17
forum: Packaging and Compiling Programs
---

### Post by steve19137 on 2010-02-17
hi. i have very, VERY little experience with coding. all i can do is recognize xml. pretty lame for a linux user, eh? anyway, i play a game called world of goo, and there is a modding tool for world of goo called gootool. there is yet another tool for gootool called WoGEditor. it specifically makes levels for world of goo. the download page is here.

[http://goofans.com/download/utility/wog-editor](http://goofans.com/download/utility/wog-editor)

there are two downloads. a launcher for the windows version, and the python source. im felling a bit adventurous today, so i want to figure out how to compile this piece of python. maybe ill even get around to actually learning it... so what i want to do is compile it into one of two things (this might be kind of choppy, im still not very good at using linux). i either want to make a debian out of it, or i want to make it into an application that just runs in a double click. let me explain the application part more, even though i dont think i need to, since im in the developing section.

a while ago, i was using puppy linux on a usb, and i got the thing on a usb by using a windows/linux app called unetbootin. if you google that and download it, it comes in one file that you launch and do crap with. so thats what i mean by an application.

so what do i need to get? i dont want to launch the .py script, i want to make a .deb or application out of it, just to clarify. also, i dont want anyone to do it for me, i want to figure out how to do it myself, by following instructions and such. so can anyone redirect me to a tutorial or post one of their own?

---

### Post by SevenMachines on 2010-02-18
hi, just to make clear that python is an 'interpreted' language, it isnt compiled, the .py source files 'are' the same files you would run with python (technically python may byte compile things for efficiency).

py2exe, used to make a python windows executable isnt needed on linux where python is already installed. a python 'executable' is just the same as running
$python someprogram.py

you can actually associate the program 'python' with opening .py files and this will make it clickable to execute should you want to do that

what 'debianizing' the program would typically do is to
* install everything to the standard system locations 
* make sure all dependencies are met, such as python, python-qt4, etc
* package copyright with the program
* do any setup things that the packager would like done

that sort of thing and pretty much anything else you'd want to do to install on a debian based system and meet debian policy on installing programs.

the [full python packaging tutorial is here]("https://wiki.ubuntu.com/PackagingGuide/Python"). you will need to be used to working on the linux command line and get familiar with the general packaging tools used to do this but it is a good tutorial and step-by-step guide on a python packaging example which sounds like what you were looking for.

there is also the program 'checkinstall'. this will create a handy deb package out of source code that have a standard approach to building themselves, a makefile, i think it might handle setup.py building as well but i really cant remember. if you follow the build instructions that come with the source code and find it works then you might find checkinstall useful to wrap this process up into a debian package automatically

---

### Post by steve19137 on 2010-02-18
> **SevenMachines said:**
> hi, just to make clear that python is an 'interpreted' language, it isnt compiled, the .py source files 'are' the same files you would run with python (technically python may byte compile things for efficiency).

py2exe, used to make a python windows executable isnt needed on linux where python is already installed. a python 'executable' is just the same as running
$python someprogram.py

you can actually associate the program 'python' with opening .py files and this will make it clickable to execute should you want to do that

what 'debianizing' the program would typically do is to
* install everything to the standard system locations 
* make sure all dependencies are met, such as python, python-qt4, etc
* package copyright with the program
* do any setup things that the packager would like done

that sort of thing and pretty much anything else you'd want to do to install on a debian based system and meet debian policy on installing programs.

the [full python packaging tutorial is here]("https://wiki.ubuntu.com/PackagingGuide/Python"). you will need to be used to working on the linux command line and get familiar with the general packaging tools used to do this but it is a good tutorial and step-by-step guide on a python packaging example which sounds like what you were looking for.

there is also the program 'checkinstall'. this will create a handy deb package out of source code that have a standard approach to building themselves, a makefile, i think it might handle setup.py building as well but i really cant remember. if you follow the build instructions that come with the source code and find it works then you might find checkinstall useful to wrap this process up into a debian package automatically

thanks. ill try that tutorial later.

---

### Post by Jacks0n on 2010-02-26
Hi Steve,

I'm the creator - so sorry about the spam, but I thought it'd help.

Checkout [Python Packager]("http://python-packager.com") ([http://python-packager.com](http://python-packager.com)). It'll make a debian file automatically, and a Windows Installer.


Jackson

---

### Post by steve19137 on 2010-02-26
> **Jacks0n said:**
> Hi Steve,

I'm the creator - so sorry about the spam, but I thought it'd help.

Checkout [Python Packager]("http://python-packager.com") ([http://python-packager.com](http://python-packager.com)). It'll make a debian file automatically, and a Windows Installer.


Jackson

what are you the creator of? the app or the packager? and what spam?

---

