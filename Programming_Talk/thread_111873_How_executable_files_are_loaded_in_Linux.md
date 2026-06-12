---
title: "How executable files are loaded in Linux ??"
date: 2006-01-03
forum: Programming Talk
---

### Post by Zonkle on 2006-01-03
Hi,

In Windows I know the structure of the EXE file (executable files) and how Windows read the PE header and stuff ...... Reverse Engineering world :)

So I wanted to know is there something like this in Linux ?!

The other day I downloaded the Folding@Home for Linux and I was amaized how very easy it was to execute and make it work. Why the other programs are not like that? Or why doesn't the other developers make it as easy as that???

Why not have simple one executable file for a program like in Windows? .... maybe there is ... but I'm still newbie in Linux...

I really would love to learn more about this.

Thanks.

---

### Post by coredump on 2006-01-03
Linux executables are in so-called ELF format.  That stands for Executable and Linking Format, and is a widely-used standard for executable files.  Here's a web page that describes it, although you should be able to find loads more:

[http://www.cs.ucdavis.edu/~haungs/paper/node10.html]("http://www.cs.ucdavis.edu/~haungs/paper/node10.html")

As for the rest of it, many programs use shared libraries.  These are loaded from files with a '.so' suffix, often located in /lib.  You will probably find web pages describing the Linux shared library format, too.

One factor that complicates Linux installations is that not all distributions place certain critical files in the same places.  There is a Unix file system standard, but it's not yet universal, and many distributions try to make the transition gradual by using symbolic links.  This can end up as a bit of a mess.  Then, there's the tendency of developers to use specific versions of libraries, often many of them.  So you often find that you need to locate and install all of the libraries and other files that the program depends on.

---

### Post by asimon on 2006-01-03
So why do most apps come in many files instead of one single file? Because you
* want to be able to not install all translations with the application because most people don't need all translations on their system
* want to install some icon on a place so that it's available system-wide for file browsers, window managers, etc.
* want to install plugins or libraries or components seperately so that they can be reused by other apps
* want to be able to install the binary one some read-only place but the configuration somewhere else where the app can write to
* want to be able to split some big application into smaller parts because many users don't need the complete thing but may be only need/want some parts from it
* want to be able to install a .desktop file so that desktop environments know everything about the application to handle mime-types and have a correct entry in their application menu or more generally have the possibility to install some 'configuration' files somewhere else to integrate the app into some other services

etc.

---

### Post by Zonkle on 2006-01-03
[QUOTE=coredump]Then, there's the tendency of developers to use specific versions of libraries, often many of them.  So you often find that you need to locate and install all of the libraries and other files that the program depends on.[/QUOTE]
This is really annoying I think ....... I really hope Linux will be more standard, because then all the efforts will be united and go on the same path.
Thanks about the ELF format, I will read about it.

asimon, I think this is not what I meant :???: although you are right .... but what I meant by one file is as in installation without having lot of libraries files crap to download as coredump mentioned.

Thanks!

---

