---
title: "Learing UNIX"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Nikhil Kenvetil on 2011-09-17
Hello all
 
i am interested in learning UNIX. could someone suggest me what book/eBook i need to refer, and most importantly, what compiler i could use. and where to get it from?
 
your help is greatly appreciated!
:)

---

### Post by haqking on 2011-09-17
> **Nikhil Kenvetil said:**
> Hello all

i am interested in learning UNIX. could someone suggest me what book/eBook i need to refer, and most importantly, what compiler i could use. and where to get it from?
 
your help is greatly appreciated!
:)


Hi and welcome,

learn the CLI in Linux and you are for all intents and purposes learning UNIX

remember the commands

```
man
``````
apropos
```and that will cover the commands when you are stuck

```
man command
``````
apropos <command or action>
```see here to learn CLI [http://linuxcommand.org/](http://linuxcommand.org/)

as for compiling i presume you mean C etc ? then

```
sudo apt-get build essentials

```that is the GNU compiler

---

### Post by Nikhil Kenvetil on 2011-09-17
thanks haqking for sharing hte information :)

---

### Post by anewguy on 2011-09-17
+1  Linux isn't what could be considered a clone of Unix per se, but every attempt was made to keep things very similar from the outside in.  Obviously the kernel, which is really what Linux is, is a written from scratch project, not a copy.  The result is indeed what haqking has said - learn the command line - including the bash shell or other shell and you should be fine from that side.  We're not just talking simple shell scripts, etc. - there are some very complex things that can be done with the linux shell.  Once you learn those you also will have learned that you can do a lot in the linux/unix shell such that it doesn't require writing as many programs as in other OS's.

From a programming side, I'm not sure - Linux will have it's own header files, etc., so I don't know if you could take the source for a Linux program to a Unix machine (I actually haven't used Unix since about 1992 or so) and have it compile without changes - I've never tried it.

There may be differences in library calls, etc., especially with lower things - the libusb calls for example - that might be different in Linux versus whatever Unix has for the same type of functionality.

You can, however, write programs in linux and they will compile and run in Windows with the correct tools.  As an example, you can build a GUI'd application in linux, including low-level libusb calls, take it to a Windows machine, and as long as Windows has the libusb library, the GTK development package for Windows and a unix-like environment like MingW so you can compile it, it will run natively in Windows.  I've done this.

Dave ;)

---

### Post by haqking on 2011-09-17
> **Nikhil Kenvetil said:**
> thanks haqking for sharing hte information :)

no worries, you are very welcome.

Enjoy

---

### Post by benigncuttlefish on 2011-09-17
Here is a direct link to download the whole free ebook.

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)

It's very helpful.

---

### Post by kaldor on 2011-09-17
Hands on is a good way to get a general taste:

[LIST=1]
[*]Become familiar with the most popular web server OS; Red Hat Enterprise Linux (RHEL). Since Red Hat costs money, take a look at CentOS or Scientific Linux which are free clones that remain 100% compatible with RHEL. 

[*]Learn about Solaris. It's a commercial UNIX system. There's a free, community-developed version of it called OpenIndiana.

[*]Learn how FreeBSD works; it's the most popular BSD OS.
[/LIST]

I recommend forcing yourself to use Linux as much as possible. Use the command line a lot (don't memorize mouse clicks) and learn the differences between distributions. As for compiling, use GCC. Ubuntu is a great Linux OS, but it is mainly aimed toward desktop users. A lot of things are already done for you, so you don't need to be skilled with Linux (or in many cases even computers) to do things. For this reason, I recommend using something other than Ubuntu if you want to learn quickly. Dig in, break stuff, learn along the way.

Also, +1 to everything haqking said before me.

---

### Post by Nikhil Kenvetil on 2011-12-06
> **kaldor said:**
> Hands on is a good way to get a general taste:

[LIST=1]
[*]Become familiar with the most popular web server OS; Red Hat Enterprise Linux (RHEL). Since Red Hat costs money, take a look at CentOS or Scientific Linux which are free clones that remain 100% compatible with RHEL. 

[*]Learn about Solaris. It's a commercial UNIX system. There's a free, community-developed version of it called OpenIndiana.

[*]Learn how FreeBSD works; it's the most popular BSD OS.
[/LIST]

I recommend forcing yourself to use Linux as much as possible. Use the command line a lot (don't memorize mouse clicks) and learn the differences between distributions. As for compiling, use GCC. Ubuntu is a great Linux OS, but it is mainly aimed toward desktop users. A lot of things are already done for you, so you don't need to be skilled with Linux (or in many cases even computers) to do things. For this reason, I recommend using something other than Ubuntu if you want to learn quickly. Dig in, break stuff, learn along the way.

Also, +1 to everything haqking said before me.
Thank you Kaldor. Really appreciate it!

---

### Post by Mark Phelps on 2011-12-07
You didn't say why you want/need to learn UNIX, but it's almost entirely used in a commercial setting, not home setting.

If that's the case for you, then you should focus on doing System Administration with UNIX, and that's a lot of command line and scripting work.

I was a UNIX System Admin for several years, and mostly what we did was user account administration, server management, network management, and applications management. And LOTS and LOTS of script work.

If you really want to learn more about the underpinnings of Linux (and a lot of that will help with UNIX), you should consider moving over to a distro that involves a lot more setup work on your part than Ubuntu.  That will give you an opportunity to learn a lot about the Linux filesystem (UNIX has some similarities) and script work.

---

### Post by corncob on 2011-12-07
I see you've marked the thread as solved but let me give one more recommendation if I may:
[www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf](www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf)

---

