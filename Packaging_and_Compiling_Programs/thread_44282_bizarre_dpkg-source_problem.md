---
title: "bizarre dpkg-source problem"
date: 2005-06-25
forum: Packaging and Compiling Programs
---

### Post by spookylukey on 2005-06-25
I've just recently started having a problem with "apt-get source -b", and more particularly with "dpkg-source -x".  When ever I try to use these commands (the first calls the second), I get an error like this:

$  dpkg-source -x amarok_1.2.3-1ubuntu4.dsc 

dpkg-source: extracting amarok in amarok-1.2.3
patch: **** Can't create file 2/ppkDIc8W : No such file or directory
dpkg-source: failure: patch gave error exit status 2

This is utterly bizarre, as I successfully compiled this exact same package from the same files a few weeks ago, and various others too.  I haven't made any big changes to my system, and it is almost entirely straight Ubuntu hoary packages (with a few peripheral packages from elsewhere).

I now always get an error like this when building Debian/Ubuntu source packages, apart from ones I know don't have any patches (e.g. one of which I'm the upstream author).  It's always "Can't create file 2/ppXXXX" where the XXXX bit changes apparently randomly.

Has anyone seen anything like this, or got any ideas about what could be causing it?  I've tried re-installing patch and dpkg-dev, to no avail.  The only other thing I can think of is that my system has been hacked and something has been broken (I do run one publically accessible server, ssh, but obviously I haven't been leaving my passwords lying around).  Does anyone know how you can even check if you've been hacked?  I understand a good root-kit is hard to detect and harder to remove.  

Cheers

---

### Post by spookylukey on 2005-06-30
My problem has magically disappeared, having done nothing in terms of changes to my system (AFAIK).  I'm thoroughly confused - if this was Windows, I'd have no problem believing it!  The only thing I can think of is that the environment of the xterm I was in was somehow messed up, and perhaps just closing it, logging out and logging back in fixed things at some point.

Oh well, sorry to waste your time!

---

