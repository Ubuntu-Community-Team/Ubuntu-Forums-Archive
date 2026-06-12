---
title: "GPU hang/error"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by supratroopa on 2013-04-06
Hi there,

I have a Lenovo notebook with a dual-boot of Ubuntu 12.10 and   Windows 7. I'm kind of a beginner with Linux, and I've been having a few issues with Ubuntu that are starting   to make it unusable. 

A few weeks ago, after a   software update was installed, I started getting these hang-ups for three to five   seconds every minute or so, after which I get a "System program problem   detected" message box concerning a file called   /usr/share/apport/apport-gpu-error-intel.py. Graphical glitches may also   appear on screen after such freezing. I don't have the same problem in   Windows 7. My graphics card is an integrated chip; Intel HD 3000.

Does anybody have a solution to this problem? If so, please share!

---

### Post by Proliferant on 2013-04-07
You're not alone, bud!  I have exactly the same issue with my Lenovo G570 and there are many others reporting the same issue on this forum.  There's no fix yet but there are enough people submitting the error reports that *hopefully* there's some attention on this.

On my side, everyday internet browsing seems to cause the most trouble, especially when using the scroll wheel a lot.  I'm thinking to start using Windows more until this is sorted.

---

### Post by CamPsych on 2013-04-07
Hi guys, 

I was having the same issue with my new install as well, check out [http://ubuntuforums.org/showthread.php?t=2073060&page=7](http://ubuntuforums.org/showthread.php?t=2073060&page=7), Matt_symes provides a link to another discussion which addresses the problem (essentially need to upgrade your kernel), also follow the advise of linusisfast to download PPA drivers, which will ensure everything is up to date, seems that this is a bug with the Sandy Bridges type processors.

---

### Post by stig on 2013-04-07
Yes, it's a real hassle and happens with 12.04 64-bit too. I'm still stuck with booting into an older kernel to avoid freezes. At first I thought my computer had died and I bought a new one only to find that there is nothing wrong with the computer, it's the Ubuntu that's the problem. I can boot into a `Try Ubuntu' live CD and the computer works perfectly but the install from the CD freezes frequently.

---

### Post by supratroopa on 2013-04-07
Hey CamPsych, thanks for replying to the thread.

I think I found linusisfast's solution, but where does Matt_symes address the issue, and where is his list of graphics chips? He just links to a seven page thread.

EDIT: I just installed the x-swat and glasen PPAs as per linusisfast's suggestion, but I still get the error messages.

---

