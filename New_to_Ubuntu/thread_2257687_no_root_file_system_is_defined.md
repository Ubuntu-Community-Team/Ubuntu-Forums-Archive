---
title: "no root file system is defined"
date: 2014-12-21
forum: New to Ubuntu
---

### Post by Anon_Eemus on 2014-12-21
I am brand new to ubuntu. I just downloaded lubuntu for the first time onto my Windows laptop. When I rebooted my computer, it started setting itself up, but soon have me an error saying No root file is defined, please Correct from partitioning menu. I don't know what this means or how to fix it. Please help!

---

### Post by nerdtron on 2014-12-21
You are still on the manual partitioning screen or you already finished the installation?

---

### Post by Anon_Eemus on 2014-12-21
I did not get any manual partitioning screen,the only options were the amount of Hard drive space. I then clicked install and it restarted,almost immediately giving me this error. Btw, this is lubuntu, not ubuntu,although I assume they are the same.

---

### Post by lisati on 2014-12-21
A quick question: were you running an installer within Windows by any chance?

---

### Post by nerdtron on 2014-12-21
So you booted from USB and ran the installer? Seems to me like a new laptop with EFI problems.
What is the laptop model.

---

### Post by Anon_Eemus on 2014-12-21
Yes. Wubi on Vista.

---

### Post by Anon_Eemus on 2014-12-21
It is a very old Gateway MT6709

---

### Post by lisati on 2014-12-21
Wubi is no longer supported. Have a look [here]("http://ubuntuforums.org/showthread.php?t=2229766"), and if you have any further questions, feel free to ask.

---

### Post by hakuna_matata on 2014-12-22
> **Anon_Eemus said:**
> but soon have me an error saying No root file is defined
IMHO, it is [bug 1385930.]("https://bugs.launchpad.net/wubi/+bug/1385930")

So, try to avoid Wubi. 

But if you must use it, it is possible to patch it: [workaround]("http://ubuntuforums.org/showthread.php?t=2251986&p=13162861#post13162861"). If you trust me, you can use a patched version, too: [wubi1410.exe]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AABxUTQhS1RHUHuzXl5Zvl5xa/wubi1410.exe?dl=0")

---

