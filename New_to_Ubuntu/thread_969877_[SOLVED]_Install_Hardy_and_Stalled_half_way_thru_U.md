---
title: "[SOLVED] Install Hardy and Stalled half way thru Upgrade"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-03
First Post:

I am trying to install Hardy 8.04 After almost 24 hours I finally got to the point which is labeled 'Installing the Upgrades'. We made it to the line: 'root@cocoknots-laptop:/#' on the terminal page. The system hung up & the Firefox icon is no longer on the tool bar. There is an electrical plug on the right top which states 'Unable to Get Data'... So I plugged in the LAN cable into the wireless router. Now the system is hard wired but no data. Now what. If I power down, I may not be able to come back on line without internet access.
	
Second Post:

Re: Install Hardy Upgrades... HELP
Please... Is anyone there, The system I tried to install 8.04 on has hung up. Does not read data. I am back on my original computer & rebooted using the Ubuntu 7.10 CD that I had. I can not access any files or data on my hard drive but I am able to get internet access indirectly. Is there any way I can re-install Ubuntu without loosing everything on my HD ?

---

### Post by pyromanic123boom on 2008-11-03
If it hung during installing upgrades, try getting into a terminal either in failsafe gnome or in the boot menu, and clearing the dpkg cache:

sudo dpkg -a

---

### Post by CoCoKnots on 2008-11-03
I'm not sure I can do that... I had to boot from a Ubuntu 7.10 CD & not able to access anything on my system. The Terminal page is what comes up via the CD. Will that still work ?

---

### Post by CoCoKnots on 2008-11-03
Can you please give me a little more information here on exactly what I need to do ?

---

### Post by pyromanic123boom on 2008-11-05
What happens when you boot your computer normally?

And can you mount your harddrive from the live cd?

---

### Post by CoCoKnots on 2008-11-09
Started over again & lost all data... But it worked this time. Thanks

---

