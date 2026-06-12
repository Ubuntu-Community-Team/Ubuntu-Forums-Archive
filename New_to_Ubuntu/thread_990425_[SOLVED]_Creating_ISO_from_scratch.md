---
title: "[SOLVED] Creating ISO from scratch"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-11-22
Is it possible to create an ISO disk image from scratch with all the updates since 8.10 was first released. I would like to install Ubuntu on a number of systems but don't want to spend the time downloading all the updates.  A DVD is acceptable.

---

### Post by chazn85 on 2008-11-22
the easy way probably not unless all the machines are of the same spec

---

### Post by hankinator on 2008-11-22
I spent, and wasted a few dozen CD's trying to create an ISO, all i was doing was changing the boot screen, in ubuntu to something else with another image (same format, same resolution), and i used many different programs but yet it failed, so well yeah, your better off just letting it go, or buying uber professional software. cause its not the problem of getting the files together, its the problem of compiling the files for the ISO.

---

### Post by kestrel1 on 2008-11-22
If the machines are of a similar spev you may be able to get them running this way:
1) Install one system with all of the updates installed.
2) create an image of the hard drive of that machine on a DVD
3) restore the image on to the other machines hard drives.

To do this you could use something like Norton Ghost, Acronis TrueImage etc. There is a Linux based drive cloning program called Ghost for Linux:
[http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml](http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml)

---

### Post by ciscosurfer on 2008-11-22
> **Michaelg14 said:**
> Is it possible to create an ISO disk image from scratch with all the updates since 8.10 was first released. I would like to install Ubuntu on a number of systems but don't want to spend the time downloading all the updates.  A DVD is acceptable.Something like slipstreaming?

These should help:
[http://ubuntuforums.org/showthread.php?t=716892](http://ubuntuforums.org/showthread.php?t=716892)
[https://answers.launchpad.net/ubuntu/+question/38101](https://answers.launchpad.net/ubuntu/+question/38101)
[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+slipstreaming+ubuntu&btnG=Search]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+slipstreaming+ubuntu&btnG=Search")

---

### Post by Michaelg14 on 2008-11-22
Thanks to everyone.  I think using the /var/cache/archive packages will be enough.  I will try it after T-giving.

---

### Post by MunkyJunky on 2008-11-22
Theres some software you can use to make a snapshot of your system, for a personalised version of ubuntu, called remastersys, or reconstructor. I've never used them, but i imagine that would snapshot all the updates with it.

---

