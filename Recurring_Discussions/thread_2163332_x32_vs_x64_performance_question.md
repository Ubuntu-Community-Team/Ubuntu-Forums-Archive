---
title: "x32 vs x64 performance question"
date: 2013-07-18
forum: Recurring Discussions
---

### Post by kbryant on 2013-07-18
Basically, is there a noticeable difference in speed between 32 and 64 bit versions of 12.04?  I ask because I had a number of problems installing only to find in the end I had installed the 32 bit version by accident...

---

### Post by sanderj on 2013-07-18
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=2](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=2)

---

### Post by HiImTye on 2013-07-18
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
64 bit will give you better performance than 32 bit, especially if using a PAE kernel. you will sacrafice a minimal amount of RAM for addressing.

---

### Post by rnerwein on 2013-07-18
> **kbryant said:**
> Basically, is there a noticeable difference in speed between 32 and 64 bit versions of 12.04?  I ask because I had a number of problems installing only to find in the end I had installed the 32 bit version by accident...
hi
you can read a lot of discussion. but fakt is. if you are running a 32bit phase on an 64bit system and you get an HSP > 2 GB the addresses must be mapped internal. this are a couple of steps in the system more. von nix kommt nix.
ciao

---

### Post by 3rdalbum on 2013-07-31
For ordinary desktop use, you wont notice a speed difference. When you are doing video encoding or certain other intensive tasks, that's where 64-bit really helps.

Otherwise there is very little difference between 32-bit and 64-bit. In theory, and probably in practice, there should be no bugs specific to 32-bit or to 64-bit. If you are having crashes or glitches, changing to 64-bit will not help.

---

