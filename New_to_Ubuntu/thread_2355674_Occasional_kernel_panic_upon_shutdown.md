---
title: "Occasional kernel panic upon shutdown"
date: 2017-03-15
forum: New to Ubuntu
---

### Post by shayacrich on 2017-03-15
I installed Ubuntu 16.04 64bit as dual boot on a brand new Asus UX360C laptop that came pre-installed with Windows 10.

There was initially an occasional, though frequent, problem where Ubuntu would hang forever during the splash screen at startup. Reinstalling Ubuntu did not help. It was magically solved when I removed "splash quiet" from GRUB_CMDLINE_LINUX_DEFAULT.

Now I have an occasional and less frequent problem where it gets stuck during shutdown. I get a "Kernel panic - not syncing: fatal exception in interrupt".
I tried testing this, and here are the results:
On the 4.8.0-41 kernel this happened after 9 restarts, and then after 12.
On the 4.8.0-36 kernel this happened after 5 restarts, and then after 14.

Here's the screen I got to with the 4.8.0-41 kernel:
[http://imgur.com/JOjsYDe](http://imgur.com/JOjsYDe)

On the 4.8.0-36 kernel, when I first got the error message, I saw these screens:
[http://imgur.com/rzbWm0b](http://imgur.com/rzbWm0b)
[http://imgur.com/mGEI37H](http://imgur.com/mGEI37H)

And the second time, I saw these:
[http://imgur.com/lr5nQg3](http://imgur.com/lr5nQg3)
[http://imgur.com/HZpI110](http://imgur.com/HZpI110)

Any help would be greatly appreciated.

---

### Post by norafaithrainbow on 2017-03-15
How much ram does your machine have, and how many cores, at what clock speed? These can contribute to errors within ubuntu. I would suggest reinstalling ubuntu given it could be easier than trying to fix this.

---

### Post by shayacrich on 2017-03-15
Thanks for the reply norafaithrainbow!

I have 8GB RAM, m3-6Y30 CPU, 2 cores, base frequency of 900MHz.
Windows reports a max frequency of 1.51GHz and the Intel spec says it can go up to 2.20GHz.

I've already re-installed Ubuntu once attempting to fix this issue, and wouldn't want to do this again, as it's wearing my SSD

---

