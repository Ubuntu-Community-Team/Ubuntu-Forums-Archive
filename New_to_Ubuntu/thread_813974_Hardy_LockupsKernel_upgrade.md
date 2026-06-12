---
title: "Hardy Lockups/Kernel upgrade"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Cront on 2008-05-31
Hi guys,

I'm experiencing frequent lockups with hardy requiring a hard reset.  The scroll lock and the num lock flash when it locks up.

I see there a different opinions on how to fix this and one is to upgrade the kernel.

I've tried to follow some steps to upgrade to .25 or now I see there is a .26 and I was wondering if someone could give me a quick step by step to upgrade the kernel and hopefully get rid of these crashes.

System:
C2D 6550
2GB samsung ram
GF8600GT
Gigibyte P35-S3
Dlink 510 wireless card

---

### Post by shifty_powers on 2008-05-31
well, that is a kernel panic, unfortunately. if you ever see you numlock and cpas lock dflashing, you know what it is.

is there anything specific you do when it locks up?

and what is the result of

```
uname -r
```

?

---

### Post by Cront on 2008-05-31
It happens pretty randomly.  Right now I'm mostly browsing the web using firefox so it'd be easy to say that is causing it but it has happened while running upgrades to...although I think FF was probably open then too.

2.6.24-17-generic

---

### Post by shifty_powers on 2008-05-31
well that is the latest in the repo's.

and i honestly would not recommend compiling a new kernel. it is a major pain in the *** in my experience ;)

what version of ubuntu are you running? and was it a clean install or an upgrade?

---

### Post by Cront on 2008-05-31
I'm running 8.04 and it's a clean install

Edit: x86 not 64bit

---

### Post by Jadd on 2008-05-31
I had a similar problem and it was caused by a bad wireless card driver.
Try disabling wireless by right-clicking on the network manager's icon in the upper right hand corner of the screen, and unticking wireless.

---

### Post by Cront on 2008-05-31
If this is the issue what is my way around it.  Unfortunately I can only connect via wireless and much as I hate it.

---

