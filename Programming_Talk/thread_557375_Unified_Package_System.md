---
title: "Unified Package System"
date: 2007-09-22
forum: Programming Talk
---

### Post by rudeboyskunk on 2007-09-22
That's right, every once in awhile somebody makes a post about it.

Well, I have started a project page for it.  I don't have a great deal of time to contribute to the project, but I want to get it started.

The project is up at [www.opensourcesociety.org](www.opensourcesociety.org).  It hasn't shown up yet, but it should be up within a day.

If you're tired of the non-interoperability of packages through all Linux distros, use your expertise here to help solve the problem!

---

### Post by Blue Sky on 2007-09-22
any details of this unified package system?

---

### Post by rudeboyskunk on 2007-09-22
None as of yet.  The key goals will of course be interoperability, ease of use and ease of build.  We want this to sort of replace tarballs as well as debs and rpms and everything else.  Instead of creating a program, tossing it into a tarball format, and then waiting for someone to come along and build it into a deb or rpm, it should be a completely one step process.  There will be no tarball that it is quickly thrown into.  It will be simple to make it into a new package that can be used and easily installed on any linux box without causing problems.  So in a sense, it will work exactly like a deb or rpm.

---

### Post by Rasitiln on 2007-09-22
I really like the idea. How it can be done I have only a few vague ideas.

---

### Post by cubytes on 2007-09-22
this will also make it easier to create a GUI  installer program for Linux applications as well

---

### Post by Nebby on 2007-09-22
People are always saying about one packaging system for all distros, but what I don't get is what's wrong with Autopackage? It already exists, and yes, there might be some problems with it, but surely fixing them would be easier than coming up with an entirely new system?
*Prepares to be proven wrong*

---

### Post by Ramses de Norre on 2007-09-23
You might want to take a look at Arch linux' pacman, it is the best package manager I know. It's really easy to use, uses a very transparent package format (unlike deb or rpm) and has quite a small codebase.

Once I got used to this system I couldn't imagine using something as complex and complicated as dpkg (although I think aptitude is a very good package manager too).

---

### Post by mostwanted on 2007-09-23
There is already the cross-package Smart Package Manager and a unified set of package tools called PackageKit is being developed by a bunch of Gnome developers at the moment.

---

### Post by rudeboyskunk on 2007-09-23
Thanks for the feedback guys.  Right now of course the project is in the "gameplan" stage, and I'm just trying to look at all the options.  One option I had hoped for was something like what Nebby said, where we can take something already being worked on and simply alter it to the specs we want to suit our purposes.

The BIG problem, of course, would be getting Ubuntu, Fedora Project, Debian, Gentoo, Mandriva, Suse, and everybody else to fall in line with us....

---

