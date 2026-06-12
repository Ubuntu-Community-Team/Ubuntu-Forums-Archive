---
title: "My programming roommate..."
date: 2008-12-02
forum: Programming Talk
---

### Post by cartisdm on 2008-12-02
I hate programming so very much (sorry guys).  However, my roommate loves it and it's all he does.  I'm finally getting somewhere convincing him to try out Ubuntu (at least dual boot).  

How would he just find source code for stuff and mess around with it?  I've been using linux for over two years now but like I said, I don't program so I've never done it and frankly wouldn't care.

I know with web browsers you can just "View source code" etc and with firefox there's the user config file to play around with.

That's the point of open source right?  To just be able to see the code and experiment?  (Sorry if I sound like a linux noob, I'm really not I just don't know anything at all about programming)

---

### Post by bruce89 on 2008-12-02
Usually the projects' Web sites have details on how to get the source (usually from a VCS).

FreeDesktop.org (X for instance) - [http://cgit.freedesktop.org/](http://cgit.freedesktop.org/)
GNOME - [http://svn.gnome.org/](http://svn.gnome.org/)
Linux - [http://git.kernel.org/](http://git.kernel.org/)

---

### Post by cartisdm on 2008-12-02
Cool, well I'll point him in that direction when he's ready to start tweaking stuff.  Thanks!

---

### Post by shadylookin on 2008-12-02
well for programs on ubuntu I would use 

sudo apt-get source THE_PROGRAM_WHOSE_SOURCE_CODE_YOU_WANT

this way you won't have to go hunting all over hells half acre just to find source code.

---

### Post by cartisdm on 2008-12-02
> **shadylookin said:**
> well for programs on ubuntu I would use 

sudo apt-get source THE_PROGRAM_WHOSE_SOURCE_CODE_YOU_WANT

this way you won't have to go hunting all over hells half acre just to find source code.


```
dan@dan-laptop:~$ sudo apt-get source pidgin
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'pidgin' packaging is maintained in the 'Svn' version control system at:
svn://svn.debian.org/svn/collab-maint/deb-maint/pidgin/
Need to get 13.4MB of source archives.
Get:1 http://us.archive.ubuntu.com hardy-updates/main pidgin 1:2.4.1-1ubuntu2.2 (dsc) [1539B]
Get:2 http://us.archive.ubuntu.com hardy-updates/main pidgin 1:2.4.1-1ubuntu2.2 (tar) [13.3MB]
Get:3 http://us.archive.ubuntu.com hardy-updates/main pidgin 1:2.4.1-1ubuntu2.2 (diff) [66.7kB]    
Fetched 13.4MB in 32s (415kB/s)                                                                    
sh: dpkg-source: not found
Unpack command 'dpkg-source -x pidgin_2.4.1-1ubuntu2.2.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed

```


I tried it for "firefox" too but got basically the same result

---

### Post by bruce89 on 2008-12-02
> **shadylookin said:**
> well for programs on ubuntu I would use 

sudo apt-get source THE_PROGRAM_WHOSE_SOURCE_CODE_YOU_WANT

this way you won't have to go hunting all over hells half acre just to find source code.

The snag with this is you end up with an old version of the source, which is useless if you want to contribute to a project.

---

### Post by geirha on 2008-12-02
> **cartisdm said:**
> ```
sh: dpkg-source: not found
Unpack command 'dpkg-source -x pidgin_2.4.1-1ubuntu2.2.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed

```


The error message is fairly clear. It can't find the command dpkg-source which is installed by the package [apt://dpkg-dev](apt://dpkg-dev), so make sure you have that package installed first. 

Also, you don't need to run that command with sudo, in fact you shouldn't, because all the source files will be owned by root and unwritable to you. Run it without sudo. The source will be downloaded and extracted to the current working directory.
```
mkdir ~/src
cd ~/src
apt-get source pidgin
```

---

### Post by Sydius on 2008-12-02
> **cartisdm said:**
> That's the point of open source right?  To just be able to see the code and experiment?

It's about transparency (being able to verify what a program is doing), extensibility (being able to add to or modify it if needed), and longevity. If a programmer drops an open-source project because they get bored or hit by a bus, somebody else can pick it up and keep it going.

---

### Post by Sorivenul on 2008-12-03
There are some excellent projects (and some not so excellent projects) on [SourceForge]("http://sourceforge.net").  There are many different languages there in a fairly well-categorized system that one can search with the added ability to filter search results.  You roommate may want to have a look there as well.  A little less straightforward but worth mentioning, IMO, is [Google Code]("http://code.google.com/").

---

