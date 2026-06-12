---
title: "top shows hi cpu load averages"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-02-21
I installed a program from Linux Poison's 'blog about:

[Tool to move the web browser profile to RAM - Profile-sync-daemon]("http://linuxpoison.blogspot.com/2013/02/tool-to-move-web-browser-profile-to-ram.html#ixzz2LYsq2I00")

It moves the web browser profile into RAM. This should speed things up a bit. I use Chrome (browser).

After installing this, 'top' is showing crazy cpu load averages. I have a quad-core cpu and usually don't see higher than 1's on average.

More importantly, the hard drive is every so often, spinning like crazy and it's at that time, that I have the following 'top' screenshot. Please see attached and then may I have some help in determining what the cause of this is, in order to either change parameters or remove the cause of this problem.

---

### Post by Mark_in_Hollywood on 2013-02-21
I am temporarily marking this thread as 'solved'. I believe that the MythTV backend server is the cause of the problem. The various processes and modules started using so much system resources, mostly disk drive reads/writes that the mouse cursor vanished for periods of time.

Useful to know:

sudo stop pid=1689 (the 1689 is my MythTV backend process ID number or pid number).

---

