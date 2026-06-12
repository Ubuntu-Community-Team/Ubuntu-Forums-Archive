---
title: "GNOME Panel Reset GUI"
date: 2011-04-19
forum: Programming Talk
---

### Post by Sam White on 2011-04-19
Just threw this together, as resetting my GNOME panels through Terminal was becoming a slight PITA.

Hope at least someone finds it useful. :D

Sam

PS. Is this in an appropriate section? The development and programming section seemed to be all questions and answers, so I figured that this should be shared in the Community Cafe. Please move if necessary.

EDIT: I used MonoDevelop to compile C# code (gui made with Glade), which is the reason for the .EXE.

I have attached a tar.gz with all the source files necessary, for anyone still not convinced.

---

### Post by user1397 on 2011-04-19
> **Sam White said:**
> Just threw this together, as resetting my GNOME panels through Terminal was becoming a slight PITA.

Hope at least someone finds it useful. :D

Sam

PS. Is this in an appropriate section? The development and programming section seemed to be all questions and answers, so I figured that this should be shared in the Community Cafe. Please move if necessary.
I downloaded that and it only has one file and it's a windows executable (exe)...

???

---

### Post by NightwishFan on 2011-04-19
The file type is:
> Panel Reset.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit Mono/.Net assembly

Considering the user's stated intent could be done with a simple shell script, at the moment I do not trust this file. Care to explain what it does Sam?

---

### Post by Sam White on 2011-04-19
See edited first post

---

### Post by NightwishFan on 2011-04-19
> **Sam White said:**
> See edited first post

Thanks! :) Always can't be too sure. I will give it a try next time I boot into Gnome 2.

---

### Post by Sam White on 2011-04-19
For future reference, what would be the best way to upload (ie. File types, compiling etc)

Sam

---

### Post by NightwishFan on 2011-04-19
.tar.bz2 archives work fine. :)

---

### Post by Sam White on 2011-04-20
Ok, so what are most programs for Linux written in? And the are compiled as .EXE, right? Or am I missing something? Sorry, I'm new to this, and I did some .NET programming on windows and just assumed it would be fine.

I suppose what I'm trying to say is, if you were concerned because it was a windows .EXE, is there any way to compile in monoDevelop so it runs natively on Linux, without mono? Or would I have to use another language? And are windows exes fine, so long as I clarify what they do?

Sorry again :P

Sam

---

### Post by NightwishFan on 2011-04-20
Well, mono I am not much familiar with though I know programs can run in Linux. (Banshee Music player is written using Mono). So it should be fine to develop using it. Personally I use Python.

A lot of simple stuff can be done using a shell script. Which uses native bash shell commands. (This is probably the simplest way to do what you tried to accomplish here), for example:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Forgive me being suspicious. Not too long ago there was a thread where a user stated "This is an executable to change your computer name". It had plenty of extra code in it to download something from an unknown webpage though. Thus I tend to try to nip such an usual thread in the bud before users might make their systems vulnerable.

---

### Post by Sam White on 2011-04-20
I see. I have no problem with what you did, as I understand that Ubuntu has a reputation for being secure that the users would like to maintain ( even if it is just to argue with Windows users ;))

On a side note, I am currently looking into Python, and I will in future supply my source code with my posts, so curious users such as yourself can have a poke around :)

---

### Post by Learning Linux 2011 on 2011-04-20
> **Sam White said:**
> Ok, so what are most programs for Linux written in? And the are compiled as .EXE, right? Or am I missing something? Sorry, I'm new to this, and I did some .NET programming on windows and just assumed it would be fine.

I suppose what I'm trying to say is, if you were concerned because it was a windows .EXE, is there any way to compile in monoDevelop so it runs natively on Linux, without mono? Or would I have to use another language? And are windows exes fine, so long as I clarify what they do?

Sorry again :P

Sam

Most of Linux is written in C, although many programs are written in other languages like Python.

They aren't .EXE files, .EXE is just Windows

---

### Post by NightwishFan on 2011-04-20
Mono uses .exe files. (Banshee for instance).

Do look into python, I find it very easy to learn and useful! :)

---

### Post by user1397 on 2011-04-21
.exe is the default binary format for windows, .deb is the default one on ubuntu

---

