---
title: "[SOLVED] Broadcom not working after upgrading to Hardy"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by wil313 on 2008-06-09
I've tried everything that I know to do, I'm not a complete Ubuntu guru... Help...? lol

---

### Post by skrribble on 2008-06-09
1. what is the chipset that you are using?  bcm4318?  this can be found by typing ```
lspci
```in the terminal.

2.do you have the windows drivers?

---

### Post by Otto-C on 2008-06-10
> **wil313 said:**
> I've tried everything that I know to do, I'm not a complete Ubuntu guru... Help...? lol

If your chipset is in the 43xx range take a look at:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Things changed with 8.04

hth
otto-c

---

### Post by drs305 on 2008-06-10
> **wil313 said:**
> I've tried everything that I know to do, I'm not a complete Ubuntu guru... Help...? lol

Without troubleshooting (i.e. a shot in the dark). I have a Braodcom 4311 and it stopped working with kernel -18. I ran the following command and it starting working right away:
```
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

good luck.

---

### Post by lswest on 2008-06-10
useful info we could use:

what model of card is it? ("lspci" will give us some info, you can also post the output of ```
lshw -C network
``` to give us a bit more info on what drivers are being used, if any)

how did you have it working in **gutsy** (7.10) or dapper (6.06 [last LTS release])? (the one in bold is the most likely version you had before, if you don't know)

---

### Post by wil313 on 2008-06-11
Well at first the new kernel did not recognize that there was a card plugged in at all but I followed this walk through and I finally got it up and running:

[http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy](http://ubuntuforums.org/showthread.php?t=779754&highlight=wireless+work+hardy)

---

