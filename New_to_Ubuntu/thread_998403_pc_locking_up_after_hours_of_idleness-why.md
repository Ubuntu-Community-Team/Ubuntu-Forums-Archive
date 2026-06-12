---
title: "pc locking up after hours of idleness-why ?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by faron45 on 2008-11-30
Can anyone explain to me...I had rebooted my pc early this morn...I left 2 simple google search pages open for approx 8 hours...came back tried to start using the thing & it begins locking up on me.Why would this happen ? Even after I rebooted this morn I really didn't even use the thing that much.Why would this happen ?

           Thanks much fer any/all help:guitar:Rock-on ! <<<<<Looks like Jerry Garcia

---

### Post by OrangeCrate on 2008-11-30
Random freezes are hard to diagnose. Personally, I'd check the memory first. Boot up a Live CD, and run Memtest a minimum of 10 complete cycles to allow the algorithms to put a hard load on the memory.

It might be something as simple as a bad stick. If it's not that, it'll probably be quite a puzzle to figure it out. (Been there...)

Good luck.

---

### Post by Dr Small on 2008-11-30
There is a lot of problems there could be.
I had a similar issues with my old Compaq, and wrote it off as a CPU problem. Come to find out, I think it was the internal video card all along, as I am now using it as a server and it hasn't locked up in 23 days!

The video card in mine probably had a glitch or was overheating causing the screen to freeze. Of course, now that I am using it as a server, I never have this problem anymore.

But it could be RAM (as OrangeCrate suggested), CPU (doubt it), Video card and possibly other components.

---

### Post by faron45 on 2008-11-30
Orange-unfortunately I do not have the cd right now so,I guess that's kinda outta the question ? Hmmmmm ? I have down an extremely long long [hours] memtest on this pc before & every thing seemed fine.But,it has been a couple [2-3] months.

Thanks very much Dr.

---

### Post by mkvnmtr on 2008-11-30
Like they say it could be many things. I had a problem with mine getting to warm after being left for a few hours. Found a thread that said screen savers will keep using cpu until the use it all. I switched to the all black and haven't had a freeze on starting back since.

---

### Post by Dr Small on 2008-11-30
> **mkvnmtr said:**
> Like they say it could be many things. I had a problem with mine getting to warm after being left for a few hours. Found a thread that said screen savers will keep using cpu until the use it all. I switched to the all black and haven't had a freeze on starting back since.
Yeah, that was one of the first things I noticed when I moved to Ubuntu two years ago. The screensavers really hog the CPU. I think they should make a new screensaver set for Xorg, that are not quite as CPU intensive. I set mine to a text screensaver, which shouldn't use to much of my CPU.

---

### Post by faron45 on 2008-11-30
-Sorry everybody-seems "the service was temp unavail for me.That's why it took me so long to reply.
mkvnmtr-Thank you VERY much...I'll try that.

---

### Post by Dr Small on 2008-11-30
edit: double post

---

### Post by OrangeCrate on 2008-11-30
Didn't think of mentioning the screensaver. As said, that's a good place to look for a problem, after eliminating faulty memory.

On a fresh install, one of the first things I do, is dump Gnome screensaver, and install xscreensaver. Do both in Synaptic. (I'm running xscreensaver on both of my machines - fade to black screen only.)

---

### Post by jamesrfla on 2008-11-30
Could be a bad hard or power supply. I am having kind of the same issue except with a different OS. I am going to run some tests this week to see if it is a dieing hard drive or a dieing power supply. Try using a different power supply and run some tests on your hard drive.

---

