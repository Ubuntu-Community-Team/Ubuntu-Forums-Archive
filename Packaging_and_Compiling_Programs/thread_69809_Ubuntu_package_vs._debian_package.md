---
title: "Ubuntu package vs. debian package"
date: 2005-09-28
forum: Packaging and Compiling Programs
---

### Post by jklier on 2005-09-28
A package I'm compiling has dependencies on glib-2.0.

The runtime version comes with the breezy distro, but not the dev-lib. And I can't find the dev-lib anywhere. So I figured, fine, get the source and make it. Spent many hours getting to understand dpkg* tools.

Then I found that there is a full distribution of the packages I'm looking for (runtime + dev lib) on the debian depot ([http://www.debian.org/distrib/packages)](http://www.debian.org/distrib/packages)).

The problem though is that the debian packages use a slightly different version number schema. And so I can't match the dev lib from the debian depot with the already installed run-time lib (I get the dependency error - dependency not met because the breeze runtime is called 2.8.0-0ubuntu1 vs. the debian runtime is called 2.8.0-1). I tried re-loading the already installed run-time forcing the version to the debian package, but that looks like it would uninstall all kinds of stuff that depends on it.

So now I downloaded the source of the debian package to see if I can recompile it and just change the version number so it matches the ones from the existing run-time.

This just seems much more complicated than it should have to be. Am I missing something? Is the naming difference between 2.8.0-1 and 2.8.0-0ubuntu1 meaningful?

Jan

---

### Post by doclivingston on 2005-09-28
"libglib2.0-dev" is the package you are looking for, it should be available in the main repository (it won't be on the CD).

To answer your question:
2.8.0-1 means the 1st debian package of version 2.8.0
2.8.0-1ubuntu1 would mean that Ubuntu have taken the above and released a package with some additional bug fixes
2.8.0-0ubuntu1 means that there isn't/wasn't a debian package yet, and this is the first Ubuntu package of 2.8.0

Basically "X-AubuntuB" means version X of the program/library, Ath version of the debian package (A=0 if there isn't one) and the Bth ubuntu version based on that debian package.

---

### Post by DirtDawg on 2005-09-28
Check out this site:
[http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)
It's the web access for Ubuntu Packages.
Here's the package you may be looking for:
[http://packages.ubuntu.com/breezy/libs/libglib2.0-0](http://packages.ubuntu.com/breezy/libs/libglib2.0-0)
Tailored for Ubuntu and any dependancies are linked directly from the page. Very useful for people like me who don't have they're Linux box hooked to The Net.
I hope this helps. (Pardon if this is obvious)

EDIT: Aw crap. You're looking for libglib-dev2.0. Sorry.

---

### Post by jklier on 2005-09-28
Excellent. That's what I was looking for. I knew I was making this harder than it had to be :-)

Seems like this link is pretty hard to find though. Would it make sense to get it added under downloads on the Ubuntu homepage to save other folks the long journey it took me to get to it?

---

