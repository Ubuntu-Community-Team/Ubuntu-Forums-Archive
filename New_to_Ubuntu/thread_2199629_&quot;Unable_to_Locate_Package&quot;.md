---
title: "&quot;Unable to Locate Package&quot;"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by 9173 on 2014-01-14
I've had this issue when trying to add several programs to Ubuntu 13.1

In this example I'll use Unsettings.

Followed this [site]("http://www.noobslab.com/2012/04/install-unsettings-tweak-tool-on-ubuntu.html") exactly and I don't think there's much room to mess up so I don't know what I'm doing wrong

> sudo apt-get install unsettings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package unsettings



---

### Post by Bucky Ball on 2014-01-14
Well, the instructions you're following are for 12.04. There are no guarantees this will work on 13.10 or that the repo is even still in existence.

---

### Post by sandyd on 2014-01-14
There is no unsettings for saucy
[https://launchpad.net/~diesch/+archive/testing/+packages](https://launchpad.net/~diesch/+archive/testing/+packages)

---

### Post by deadflowr on 2014-01-15
Aside from there being no unsettings for saucy, when you added the ppa you should have then ran a reload, or
an apt-get update, so that the newly added package list was updated on your system.
If the ppa isn't there, it'll list it as an error, a "not found" error.
Best thing to do for that would be disable the ppa.
Open software and updates and go to other software and find the listing for the ppa and uncheck it.

Having used both unsettings and unity-tweak-tool, I will say that they both offer very similar abilities.
As such I would recommend installing unity-tweak-tool for saucy.
It's in the repos, so no need to break a leg trying to get a ppa installed.

---

### Post by 9173 on 2014-01-15
Okay then

---

