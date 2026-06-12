---
title: "boot hangs after trying new monitor settings"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by jordanStone on 2008-09-11
I have been running ubuntu for a while.  After messing around with the monitor settings (a lot!)  I can't boot.  In the course of trying to get my laptop to display to a widscreen i did:

   1. sudo apt-get update
   2. sudo apt-get install linux-restricted-modules-$(uname -r)
   3. sudo apt-get install xorg-driver-fglrx
   4. sudo aticonfig --initial

It booted a few times after that, however I messed with the monitor settings a bunch after.  Now it won't boot.  It first stopped at /etc/rc.local  

I can boot in recovery mode, where I looked at rc.local and saw only

#!bin/bash
#comments
exit 0

I removed rc.local in recovery mode because from other threads it seemed that ubuntu looks for init.d instead of rc.local anyways.

Now the boot appears to stop after *checking battery state...

HELP!

---

