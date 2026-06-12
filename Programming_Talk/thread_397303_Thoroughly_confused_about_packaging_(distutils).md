---
title: "Thoroughly confused about packaging (distutils)"
date: 2007-03-30
forum: Programming Talk
---

### Post by Buchuki on 2007-03-30
Hi there,

I'm trying to create a .deb package of a python application I've written. I have a setup.py for the program, and would like to find an easy way to create .debs from it. I searched the forum, but mostly found either links to programs designed to automate the process, none of which seem stable or popular enough to give me confidence in using them, or else, I found people saying "look at XYZ package to see how its distributed". The problem is, I don't actually know what I need to do to look at a package to see how its distributed.

I'm coming from Arch Linux where creating packages is as easy as writing a small file that runs the install commands and sets up a pkg directory. I'm not certain how this is done in Debian/Ubuntu. I read but didn't really understand an article describing the structure of Debian binary and source packages. However, it seems unlikely to me that I have to artificially create packages by setting up a directory structure and using 'ar' and 'tar' to create the packages. I think I'm missing something pretty basic.  Is there some sort of basic HOWTO that tells me how to create a package (preferably one that uses setup.py distributed programs as an example), instead of one that tells me how a package is structured?

At the moment, the least confusing method I've discovered is to use checkinstall to create the .deb, but even that seems to be risky, as the README says "The Debian support in CheckInstall is still new, so handle it with care.".

For the record, the program I'm trying to create a .deb for is located at [http://pallavi.sourceforge.net/](http://pallavi.sourceforge.net/)

Thanks for any insight into the "correct" way to create this package.

Dusty

---

### Post by Monk-e on 2007-03-30
I am not very experienced in packaging myself, but am learning through the [Packaging Guide]("http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html"). Good luck. :)

---

### Post by MilesZS on 2007-03-30
Actually, I was just looking into deb packaging myself (hence, I came across this post).  Not what you want to hear, I'm sure, but I do have a couple of links that may be helpful:

[Deb Guide]("http://doc.gwos.org/index.php/Deb_Guide")
[Debian New Maintainer's Guide]("http://www.us.debian.org/doc/maint-guide/ch-start.en.html")

Hopefully, these will help, though they are not exactly what you were seeking.  Good luck!

MilesZS

EDIT:  Unearthed this snippet (hopefully it's not worthless):

> 
[I]Quote:
Originally Posted by errr
Im trying to make a deb of an app with no configure script, and nothing to compile.. Its pretty much just a python module. All it has is a setup.py file. Im not sure where to get started on this, can someone give me a hand?

[http://fluxstyle.berlios.de/](http://fluxstyle.berlios.de/) this is what I want to make a package of.

Thanks.[/I]

You need to run the setup.py file inside debian rules.

Try getting the gaussum source package for an example

---

### Post by Megaqwerty on 2008-02-12
Can I assume you have figured it out, or do you still require help? 
I have only packaged a few python programs (which used setup.py) myself, so I don't know how much help I can be (I'll just have to look at them again to remember how I did it), but I can do my best to help guide you through packaging it.

--Megaqwerty

EDIT: Never mind, just visited the site and saw that you've figured it out.

---

