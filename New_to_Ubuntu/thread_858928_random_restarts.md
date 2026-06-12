---
title: "random restarts"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Nickocosmicfatplanet on 2008-07-14
ubuntu keeps restarting on me, but it only seems to happen when i close a tab or window in firefox (especially when watching flash videos). it doesn't give any warning or error messages. the screen goes black and goes to a POST-like screen, where it seems to be restarting itself (saying it's running scripts or something). it only does this for about 15 seconds, and then my pc POSTs and brings me to the os selection screen, where i proceed to restart ubuntu, and then runs fine. this has happend twice today.

---

### Post by nsabatino on 2008-07-14
It could be hardware related... Try booting into memtest86 and letting it run a few iterations. May also be the power supply?

---

### Post by Nickocosmicfatplanet on 2008-07-14
i seriously doubt it is the power supply, unless linux itself requires (x) amount of watts that my psu can't dole out. and btw this never happend with windows. if it crashes again i'll boot it in memtest and post back.

---

### Post by zipperback on 2008-07-14
> **Nickocosmicfatplanet said:**
> ubuntu keeps restarting on me, but it only seems to happen when i close a tab or window in firefox (especially when watching flash videos).



Try using a different browser such as Opera and see if the problem still happens. 

There is a serious problem with the flash player on the Linux platform however.
Adobe is well aware of it, and hasn't done much to fix it.

A quick search on google turned up thousands of pages with problems about flash crashing.

[http://www.google.com/search?hl=en&q=linux+%2B+flash+crashing+%2B+reboot&btnG=Search](http://www.google.com/search?hl=en&q=linux+%2B+flash+crashing+%2B+reboot&btnG=Search)

I too have a similar problem with flash, but it doesn't reboot my system. Randomly it will cause Firefox to just vanish, or sometimes it just locks up the browser and I have to kill the process. The problem however occurs for me, regardless of the browser I am running.

- zipperback
:popcorn:

---

### Post by Nickocosmicfatplanet on 2008-07-15
ran memtest, didn't find any errors. hasn't crashed in a while though (even after watching several videos on youtube).

---

### Post by mgranet on 2008-07-15
> **Nickocosmicfatplanet said:**
> i seriously doubt it is the power supply, unless linux itself requires (x) amount of watts that my psu can't dole out. and btw this never happend with windows. if it crashes again i'll boot it in memtest and post back.

It could very easily be the power supply. I had very similar problems with my system, and a power supply took care of the problem. I've had Kubuntu suddenly log me out many times. That is an OS issue. But a restart is more probably a hardware issue, as said earlier.

---

### Post by Nickocosmicfatplanet on 2008-07-15
could it just be the 64-bit architecture? i know there have been problems with it and windows, just not sure about linux.

---

### Post by cariboo on 2008-07-15
I have yet to see software cause a spontaneous restart, I've been using computers for long enough that I should have seen something by now. I've also been a hardware tech for the last 20 years. I suggest that if you've got another power supply hanging around to swap them and see what happens.

Jim

---

### Post by Nickocosmicfatplanet on 2008-07-15
unfortunately no, but i'm having a hard time understanding why it could be the psu. my pc has been running strong for about a year, and has never restarted itself like that. it only did it after i started using ubuntu, and doesn't do it in windows. i'm not saying you guys are wrong, i just don't understand why the psu would start doing this after i start using linux.

---

### Post by GordSellar on 2008-07-15
I'm having the same problem too, and noticed some lag on programs... and when I checked my system monitor, I noticed that my 1Gig swap partition isn't getting used. Might that be a connection?

---

