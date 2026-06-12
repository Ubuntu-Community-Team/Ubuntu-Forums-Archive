---
title: "Continuous Freezing 7.10"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by wthoang on 2008-04-26
Apart from how happy i am with the performance with Ubuntu (7.10) i must say there is one problem that i have found with my introduction to linux. I was sent the live CD last thursday..on the day 8.04 came...i installed it because i cant download 8.04 just yet, and even on the live cd, i came across a freeze, where my comp just stopped working completely, the screen just froze and i had to turn my comp off by holding the powerbutton. I thought that installing it would help but no...nothing. There doesnt seem to be any pattern to the freezes. Last time i was searching through this forum for a solution and i was on Pidgin. (rite now im fearing the freeze)
Is anyone else suffering from this?

Here's some info on my comp. ( i dont noe wat to provide so ask if u want more)
Computer: IBM Thinkpad T43 notebook
Harddrive: 60gig
Ubuntu in Partition 2: 40gig
Windows Paritition 1: 20gig
1gig of ram

Thnx,
Will

---

### Post by aimpau on 2008-04-26
[http://ubuntuforums.org/showthread.php?t=762507&highlight=irritating+lock](http://ubuntuforums.org/showthread.php?t=762507&highlight=irritating+lock)

post in here your syslog entry right before your system crashes. Next time, don't press the off button but rather the restart. I'm having the same problem and I'm on a mission on solving it.

I think this is what you should type in the terminal:

```

sudo gedit /var/log/syslog

```

---

### Post by wthoang on 2008-04-26
im using a notebook...theres no restart button...just a powerbutton. sorry...
but should i type that in terminal once i restart after a freeze? cos how do i noe when its just about to crash?

---

### Post by wthoang on 2008-04-26
this needs a bump for this major problem

---

### Post by Clodd on 2008-04-26
I'm not sure if this is the same problem as yours but sounds like it. When this happened to me it turned out that I needed to reconfigure xorg.

here is a link to the thread which might help you:

[http://ubuntuforums.org/showthread.php?t=745093](http://ubuntuforums.org/showthread.php?t=745093)

---

### Post by wthoang on 2008-04-26
cheers...ive givin u a thnx..ure first one..lol...just got to wait and see now..

---

