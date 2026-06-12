---
title: "xorg.conf or xorg.conf.dist-upgrade"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by jeneverboy on 2012-04-03
Hi

I want to change the xorg.conf file but I noticed that there are multiple xorg.conf files in the /etc/X11/ directory. Which one is used?

> -rw-r--r-- 1 root root  1164 2012-04-03 11:20 xorg.conf
-rw-r--r-- 1 root root  1037 2009-09-04 22:20 xorg.conf.20090904222046
-rw-r--r-- 1 root root  1095 2009-09-29 11:09 xorg.conf.20090929110909
-rw-r--r-- 1 root root  1095 2009-10-13 13:12 xorg.conf.20091013131208
-rw-r--r-- 1 root root  1094 2010-08-24 12:56 xorg.conf.dist-upgrade-201008241256
-rw-r--r-- 1 root root  1094 2011-03-08 19:16 xorg.conf.dist-upgrade-201103081916
-rw-r--r-- 1 root root  1095 2012-04-03 11:25 xorg.conf.dist-upgrade-201103151804


I tried to adjust and copy the original xorg.conf file as tou can see. Can I delete all the others and use xorg.conf?

Thanks!

---

### Post by NikTh on 2012-04-03
Hello , 
the first file that system reads is xorg.conf . All other files maybe they are backups or safe mode graphics and used by system when xorg.conf is corrupted. 
If you want to change something you must do it to xorg.conf , but i don't know if its safe to delete others. Are only few KB's . 
Wait for someone who knows for sure.

---

### Post by jeneverboy on 2012-04-03
yeah they are all the same. 

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2640 800
	EndSubSection	
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

So I guess its save to delete them. I leave one for backup.

---

