---
title: "System unusable!  Slow, does not start properly"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Juhla Mokka on 2008-05-12
Yesterday mu Ubuntu became unusable. It takes a long time to start,  is incredibly slow (takes a few minutes to open an application). I cannot remember doing any weird stuff on it (installing etc). A few warning boxes came up couple of days before saying something like Applet not working properly, delete? Cannot remember! I clicked delete.
:confused:
What can be wrong? 
How to fix it?

I know that I am running short of disk space, but do not know how to extend the partition (I run Ubuntu & Vista dual boot). I partitioned the drive following instructions on web and they said I can extend the partition at later date - but that does not seem to be possible.

Thanks!:)

---

### Post by Juhla Mokka on 2008-05-12
Hi, looking at the System Monitor everything looks normal: CPU1 5-6%, CPU2 10-12%, User memory 11.7% (235.3MB), Swap 0%, network sent 350-420 bytes/s, received 0-476 bytes/s.

---

### Post by alienexplorers on 2008-05-12
What are your system spec's and what size swap file are you using.

---

### Post by Het Irv on 2008-05-12
To extend the partition you need to be on the Live CD.

As to your other problem.... you wouldn't happen to remember which applet, would you?
you may have a problem with the gnome applet if programs are taking a while to load.

---

### Post by Juhla Mokka on 2008-05-12
Hi, regarding partitions, I am having problems and have posted here: [http://ubuntuforums.org/showthread.php?t=718351](http://ubuntuforums.org/showthread.php?t=718351)

I have a new laptop. When I partitioned I allocated 10GB to Ubuntu 7.10. Vista has about 110GB. 1.46 GHz. Intel Pentium Dual core. Memory 2GB.
Linux swap 470.62 MB.

I cannot what the applets were... There were maybe 6 of them, relating to desktop..possibly. Quite stupid from me not noting what they were.

Hope this helps. Not sure what specs you were after?

---

### Post by Juhla Mokka on 2008-05-13
Hi, can anybody advise please? I am quite worried because my course work is on Ubuntu.

I cannot use Ubuntu because it is so slow (takes MINUTES to open things)

---

### Post by deepclutch on 2008-06-25
if you have enough memory and still system is slow ,compiz may not be the reason.

check from gnome-system-monitor or cli "top" or "htop" commands ,the application which is using most RAM. renice the app to a lower position .memory leak also may be a reason.

there may be some gconf entries which can/may speed up :) consider nvidia driver too.(**try "vesa" or "nv" driver by editing xorg.conf and check whether the problem is resolved.**) .
also consider download and install using nvidia installer ,the latest nvidia 173.14.5 driver .

disabling ipv6 is the most common solution which I found with most Ubuntu versions esp for faster inet connxns.(add "blacklist ipv6" without quotes in /etc/modprobe.d/blacklist file as root ).

also consider a  bug report and have a look at this thread:
**[ Hardy is BY FAR the worst Ubuntu version yet. LOCKUP WARNING!!!  ]("http://ubuntuforums.org/showthread.php?t=768200")**

some random tips :
enable "gnome-power-manager" at boot.
remove unwanted session startups.
and lastly try a different kernel or optimized kernel like the ones available rarewares.org(zen sources) or compile yourself a custom kernel.


some other things you can do : remove beagle,trackerd ,network-manager+dependencies ,make sure swap exists and enabled(free -m)

---

