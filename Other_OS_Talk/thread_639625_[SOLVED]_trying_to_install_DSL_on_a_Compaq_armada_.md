---
title: "[SOLVED] trying to install DSL on a Compaq armada e500"
date: 2007-12-13
forum: Other OS Talk
---

### Post by Fanin on 2007-12-13
i'm trying to install DSL on a Compaq armada e500. picture [_HERE_]("http://www.mammut-computer.de/images/Compaq_E500.jpg")
it already has Win98.
I want to delete everything except DSL, but do i have to format the pc before installing DSL, or is there a way to delete it after DSL has been installed?. if so, how?.. just curious
btw, I'm a noob :)

---

### Post by mips on 2007-12-13
would be easier to wipe the HD first. Just use Gparted.

---

### Post by Fanin on 2007-12-13
> **mips said:**
> would be easier to wipe the HD first. Just use Gparted.

Gparted :confused:
could someone point me in the direction of a Gparted tutorial, or tell what this thing is?

---

### Post by mips on 2007-12-13
[http://www.google.co.za/search?q=Gparted&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.za/search?q=Gparted&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Shazaam on 2007-12-14
It does have a cd/rom drive, right?
gparted livecd:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

What is the size of the drive? Wipe the drive, make a 500meg swap, then an extended partition in the remaining space. Make logical partitions inside the extended partition where you can install dsl or others.

---

### Post by K.Mandla on 2007-12-14
> **Fanin said:**
> Gparted :confused:
could someone point me in the direction of a Gparted tutorial, or tell what this thing is?
GPartEd is a version of Linux that only allows you to partition your drive, but doesn't install anything (unless that has changed ... ?).

Rewriting the partition table (the "map" of the hard drive) effectively erases the drive.

If you want, you can use [DBAN]("http://dban.sourceforge.net/") instead, which erases the drive completely. It depends on what you have on there, and how long you want to spend cleaning it off, and what you're trying to get rid of. :mrgreen:

---

