---
title: "whaa just happenned"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-20
on ubuntu last night, had to switch off computer because going so slow. When I turned it back on, the only ubuntu thing i got was mem test.
M

---

### Post by hyper_ch on 2008-11-20
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by irish66 on 2008-11-20
ok, ta.
M

---

### Post by philinux on 2008-11-20
Press escape when grub appears and choose the recovery mode option to boot.

---

### Post by irish66 on 2008-11-20
Thank you. I'm not advanced enough yet to know what GRUB is. Well at least not the computer kind. I presume it's the black screen i get with 
text telling me such things as "press esc for menu" When I do that, I get options for windows xp, ubuntu, and other operating systems. I don't have other op systems. So i choose ubuntu, and the only menu i get is mem test. 
I do that, after a while it stops, and I end up with half a red screen and half a blue screen. I rebboted a number of times. Ubuntu has now been uninstalled. That doesn't mean I've given up on it. I may come back to it. But Now I'm
trying out other linux distros with live cds.
M

---

### Post by philinux on 2008-11-20
Thats the one "press esc". Then use the up/down arrow to highlight the ubuntu entry that has recovery mode. Then press enter. If you need to get to the recovery mode ever again.

---

### Post by irish66 on 2008-11-20
Thanks again
But as i said, all i got was mem test.
oh! I should say, I had chosen to run ubuntu from within windows, so maybe that was the problem.

Anyway, here's a reasonable account of what happenned 
Boot up computer
Windows xp
Ubuntu


Choose Ubuntu
mem test starts. I decide to let it run.
Next morning, see that mem test is still on, but stopped, with the screen appearing half red, and half blue.
boot up again, choose ubuntu
This time I press esc at the appropiate time. 
But the only opion i get for Ubuntu is mem test.
I've run it a few times. I've never gotten the full menu back.
M










It stops with half red, half blue screen.

---

### Post by philinux on 2008-11-20
Right so it was a Wubi install from windows. It sounds like it got borked.

---

### Post by oldos2er on 2008-11-20
What are the hardware specs of this machine? From your memtest result, I'd think some or all of your RAM is bad.

---

### Post by irish66 on 2008-11-20
Hi Ann.I'll have to find out how to do that in kubuntu.
M

---

### Post by irish66 on 2008-11-20
Hi Ann. Is this what you need?
OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 2 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	BETTERWA-07BA6F
System Manufacturer	MEDIONPC
System Model	MS-7204
System Type	X86-based PC
Processor	x86 Family 15 Model 4 Stepping 4 GenuineIntel ~2999 Mhz
Processor	x86 Family 15 Model 4 Stepping 4 GenuineIntel ~2999 Mhz
BIOS Version/Date	Phoenix Technologies, LTD 6.00 PG, 07/10/2005
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.2180 (xpsp_sp2_rtm.040803-2158)"
User Name	BETTERWA-07BA6F\martin
Time Zone	GMT Standard Time
Total Physical Memory	1,024.00 MB
Available Physical Memory	638.82 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	2.40 GB
Page File	C:\pagefile.sys

---

### Post by dfowensby on 2008-11-20
what OS? if you are trying new 8.10, beware. it's sorta like a beta for LTS. i recommend going back to 8.04LTS. very stable, and you can leave it alone and update regularly until 2011. no issues like the "tween" releases have.
Ubuntu 8.04 is nearly a fault-proof unattended clean install. if this is NOT what you have been trying, i highly encourage you to do so.
luck --O.

---

### Post by irish66 on 2008-11-20
Hi dfowensby.
windows xp home edition
I'm installing xubuntu on shared windows drive now. I'll see how that goes first. 
Thanks for the advice though. Anyway i see there are loads of linux pacages to try out.
M

---

### Post by jimreynold2nd on 2008-11-20
Ohhhhh so you used Wubi..............

Yea, an unclean unmount of Wubi's virtual hard drive is likely to cause corruption to the whole virtual HDD. Anyway, I suggest you to do partitioning/dualbooting Win and Ubuntu if you know how to.
If you don't, reinstall Ubuntu with Wubi and _try_ to always shut down Ubuntu cleanly as not to damage the virtual disk image.

Hope this helps and didn't confuse you too much:KS

---

### Post by handydan918 on 2008-11-20
As old0s2er has previously noted, if you are getting red highlights out of memtest, you probably have some dead memory. Nothing else matters until you resolve that. You can spend the rest of the machines life chasing ghosts.

---

### Post by irish66 on 2008-11-21
Thanks for the tips, folks.
M

---

