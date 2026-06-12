---
title: "How to determine what version is installed?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by hbnmgr on 2013-04-08
What command in terminal can we use, or other way to determine what version of Ubuntu is installed?

Thanks!

---

### Post by BrunoLotse on 2013-04-08
Try this
*lsb_release -a*
*man lsb_release*

Cheers,
Bruno

---

### Post by vallvi on 2013-04-08
or: just click on 'Ubuntu help' on your desktop

---

### Post by philinux on 2013-04-08
Top right gear on top panel then choose About this Computer.

---

### Post by gnugen on 2013-04-10
You can go to System Settings and click on System Details.

---

### Post by hbnmgr on 2013-04-10
Thanks 'Brunoltse'  that worked.

'Vallvi' - When clicking on the lifesaver ring "HELP", I get the following;
> Firefox can't find the file at /usr/share/ubuntustudio-docs/about/ubuntustudio-index.html.

'PhilLinux' - I have no "gear" in top right. I'm running Ubuntu Studio v12.04 Precise, with XFCE DE.

'gnugen' - I have no "System Settings", I have "Settings / Settings Manager" and "Settings / Settings Editor". No Details under either one.


Thanks all, I will consider this Thread Closed ( if I can find out how - don' see a way while I am replying!)

Thanks!
hbnmgr

---

### Post by pinballwizard on 2013-04-10
> **hbnmgr said:**
> Thanks 'Brunoltse'  that worked.

'Vallvi' - When clicking on the lifesaver ring "HELP", I get the following;


'PhilLinux' - I have no "gear" in top right. I'm running Ubuntu Studio v12.04 Precise, with XFCE DE.

'gnugen' - I have no "System Settings", I have "Settings / Settings Manager" and "Settings / Settings Editor". No Details under either one.


Thanks all, I will consider this Thread Closed ( if I can find out how - don' see a way while I am replying!)

Thanks!
hbnmgr

Open a terminal, type: ```
cat /etc/*release
```

And to mark the thread, click on the thread tools button at the top right.

---

### Post by some1at127001 on 2013-04-10
There are two other ways to find out more about your OS version (actually, the kernel).

Start a terminal and try the following commands:

```

~$ uname -a
Linux it-desk 3.8.0-17-generic #27-Ubuntu SMP Sun Apr 7 19:40:26 UTC 2013 i686 i686 i686 GNU/Linux

```

```

~$ cat /proc/version
Linux version 3.8.0-17-generic (buildd@akateko) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.2-23ubuntu2) ) #27-Ubuntu SMP Sun Apr 7 19:40:26 UTC 2013

```

Have fun!

---

### Post by hbnmgr on 2013-04-10
> **pinballwizard said:**
> And to mark the thread, click on the thread tools button at the top right.

It reads
Show printable
Email to ...
Subscribe to thread

I know I saw it before - where did it go?
hbnmgr

---

### Post by ppjdee on 2013-04-10
check my sig for marking threads as solved

---

