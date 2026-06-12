---
title: "Crashing OS; problems with quality of Full Screen."
date: 2016-06-29
forum: New to Ubuntu
---

### Post by Victor_Gilbert on 2016-06-29
I recently installed Ubuntu 16.04 as a stand alone system on an ACER E210, 32-bit AMD Athlon 4,200 MHz, 71.3 GB hard drive, 3 GB RAM, and 25GB BT Infinity 
About every other time I'm in Ubuntu it crashes when I try to open/close a programme.
I can't open any films on MUBI my favourite film website.
 
 
 I ran Boot Repair: [http://paste.ubuntu.com/18118805](http://paste.ubuntu.com/18118805)

Help please

Victor_Gilbert

---

### Post by Liam_Murphy on 2016-06-29
Any errors, or is it just a freeze? 

The most information you can give us, the better we can help.

---

### Post by X-RED_Tech on 2016-06-29
Boot repair has nothing to do with it. If the OS boots then Boot Repair isn't needed and will change nothing.
MUBI requires Flash.

---

### Post by Victor_Gilbert on 2016-06-30
Thanks Liam_Murphy 
It crashes - have to turn PC off

> **X-RED_Tech said:**
> Boot repair has nothing to do with it. If the OS boots then Boot Repair isn't needed and will change nothing.

MUBI requires Flash.

OK I'm a silly old duffer I know that! 
Installed Flash in Terminal .... ......  I can watch MUBI .... Thanks 

But I suspect it will crash again!

Victor_Gilbert  a 78 year old duffer

---

### Post by Liam_Murphy on 2016-06-30
Around a year and a half ago, I had a desktop PC that was randomly freezing in both Windows and Ubuntu.

I eventually was able to find that the Motherboard was dying, and swapping that out with a new one fixed my problems.

Of course you have a laptop so you can't do that, but I would recommend searching online for your laptop model and see if anyone else has reported similar issues.

---

### Post by Victor_Gilbert on 2016-06-30
> **Liam_Murphy said:**
> Around a year and a half ago, I had a desktop PC that was randomly freezing in both Windows and Ubuntu.

I eventually was able to find that the Motherboard was dying, and swapping that out with a new one fixed my problems.

Of course you have a laptop so you can't do that, but I would recommend searching online for your laptop model and see if anyone else has reported similar issues.

I had a new motherboard recently on this PC + Windows - don't remember Windows crashing .

 Following the last crash 20 mins ago I failed 3 times to boot up so I ran Recovery :
Ubuntu with Linux 4.4.0 - 24 - generic - recovery mode. 
(What is the difference between 24 & 28 -generic?)
It then opened in Safe Mode? and  now in normal opening.

Repeating this procedure  is a total pain!

Victor_Gilbert

---

### Post by X-RED_Tech on 2016-06-30
No much difference really between the kernels and probably nothing related to your problem. The graphics drivers may have something to do with it.

Please post the result of ```
lspci | grep VGA
```

---

