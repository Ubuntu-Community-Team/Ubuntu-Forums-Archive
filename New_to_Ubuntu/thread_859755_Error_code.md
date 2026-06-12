---
title: "Error code"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by fuzzylogic on 2008-07-14
I did a update manager and when it downloaded new updates it gave me an error code. the following message states: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.


Being a MS user for too long I don't know how and what it means to run "dpkg" 

I really like Ubuntu, I'm currently running 7.04 but need to update to 7.1 and then to 8.04

Thanks

---

### Post by appi2012 on 2008-07-14
open a terminal, and type:
```
sudo dpkg --configure -a
```

---

### Post by Jim! on 2008-07-14
Why not just upgrade straight to 8.04? There's not really any point going from 7.04 to 7.10 to 8.04... 

As for your problem, something disrupted the update so it didn't download or install properly. Have you tried running the command it asked you to?

---

### Post by ChameleonDave on 2008-07-14
Sorry on behalf of Ubuntu!  Error messages can be unhelpful at times.  They assume you are experienced.

What it means is that you ought to enter that command at a terminal.  You can find the terminal program in the application menu.

Once in, you need to type or paste this:

```

sudo dpkg --configure -a

```

The "sudo" part is so that you do it with admin powers.

---

### Post by nowshining on 2008-07-14
> **Jim! said:**
> Why not just upgrade straight to 8.04? There's not really any point going from 7.04 to 7.10 to 8.04... 

As for your problem, something disrupted the update so it didn't download or install properly. Have you tried running the command it asked you to?


well according to canonical going straight from 7.04 to hardy is unsupported - and they insist you go thru the middle versions of upgrading to get to the latest or install the newest version as a fresh install.

---

### Post by fuzzylogic on 2008-07-14
Ok, I like to load straight to 8.04 but had to load onto my usb 1gb thumb drive because I don't have a working floppy drive and, I only have a cd rom drive. how can I get it to load on a boot up?

---

### Post by Jim! on 2008-07-14
> **nowshining said:**
> well according to canonical going straight from 7.04 to hardy is unsupported - and they insist you go thru the middle versions of upgrading to get to the latest or install the newest version as a fresh install.

My bad I didn't word that properly, I meant a clean install. Thanks for pointing that out!:)

---

### Post by nowshining on 2008-07-14
well u can order a free CD from shipit.ubuntu.com :)

---

### Post by nowshining on 2008-07-14
> **Jim! said:**
> My bad I didn't word that properly, I meant a clean install. Thanks for pointing that out!:)

lolz that k, i've worded sentences wrong in the past also, all is forgiven. :)

---

### Post by Jim! on 2008-07-14
> **fuzzylogic said:**
> Ok, I like to load straight to 8.04 but had to load onto my usb 1gb thumb drive because I don't have a working floppy drive and, I only have a cd rom drive. how can I get it to load on a boot up?

Sorry, Whats loaded on a thumb drive? And whats this about a floppy drive?:)

---

### Post by fuzzylogic on 2008-07-14
Sorry I guess I'm getting ahead of myself...I started with the thought from hearing others stating I should increment the updates from 7.04 to 7.1 and then to 8.04 to avoid glitches, I thought 8.04 recognizes there is a previous version therefore it does a upgrade using previous programs.Yes I was trying to install all of the current updates before loading 7.1 but got an error code. If loading 8.04 will do a complete new install doesn't piggy back on the old version then I'm all for it. again that was the reason for the change in my last statement. Sorry guys..So Can I still load from USB?

---

### Post by nowshining on 2008-07-15
if u haven't done it yet - remember to backup all ur important files. :)

---

