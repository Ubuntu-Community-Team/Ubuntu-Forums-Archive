---
title: "HOWTO: Setup a Brother HL2070N for Network Printing on Xubuntu"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by hatsix on 2006-08-31
Alright, after wrestling with this for a while, I finally pieced together enough information to get my Brother HL2070N working over the network for Xubuntu.

First off, you need to be able to manage cups on xubuntu. You have two options, re-enable the CUPS web interface, or install gnome-cups-manager:

[SIZE="4"]For the Web Interface[/SIZE] (blatantly ripped from [here]("http://http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/")):
[I]Select “System”->”Administration”->”Users and Groups” from the main menu on your desktop.
Select “Show all users” and/or “Show all groups”.
Add the user “cupsys” to the group “shadow” in the “groups” tab.

Restart cupsys by issuing the command:
$sudo /etc/init.d/cupsys restart[/I]

[SIZE="4"]For gnome-cups-manager:[/SIZE] (this will not install a menu item, you'll have to start this from the command line)
```

$sudo apt-get install gnome-cups-manager

```


If we wanted to use USB, we'd follow the steps [here]("http://ubuntuforums.org/showthread.php?t=123539"), but we want to use networking, so lets continue!

login to your CUPS web-config at [http://localhost:631]("http://localhost:631"), or run gnome-cups-manager from the terminal.

Now tell CUPS that you have a network printer with IPP, with a URI of http:/aa.bb.cc.dd:631/ipp and that it should use the ESP HP LaserJet Series PCL 6 driver.

BAM, done.  I tried for a VERY LONG time to get Brother's drivers working over the network, but since the 2070N has HP Emulation automatically, and HP Networks are included, this works perfectly!!!

---

### Post by Cmdrfletcher on 2006-09-22
Thanks for this guide. It works perfectly. BUT... Iam scanning right now and it takes FOREVER. :-(

---

### Post by ckirk on 2006-09-23
Very Nice! Thanks for the posting. Worked perfectly. 

One note, I'm running the x64 version of Dapper Drake. Brother supplied drivers are for 32-bit only. This is a quick way to be up and running.

//ckirk

---

### Post by Iowa Dave on 2006-10-16
Hi, group,

I'm new to ubuntu but have worked with other distros for several years. Everything on this page made sense to me and I followed it carefully. My Brother sits on my LAN at 192.168.0.106. I can access the printer's web-based administrative tool at [http://192.168.0.106](http://192.168.0.106). But it doesn't get recognized by the Add New Printer process at [http://192.168.0.106:631](http://192.168.0.106:631).  When I search for printers on the network I find CUPS printers being shared by other computers. Even the Brother shows up there, via one of our Macs. However I cannot send a test page to the printer that way. I'm stumped. 

I'm using the "Live CD" version of Ubuntu 6.06, by the way, evaluating it for possible installation. Right now I'm feeling a little discouraged. Suggestions appreciated. Thanks.

---

### Post by vgrisham on 2006-12-16
To the author of this thread, THANK YOU! I tried all day to get the Brother drivers to work to no avail. You saved my evening. :-D

---

### Post by vgrisham on 2007-01-22
Since I've gotten more and more confident in my terminal skills, I decided to give the real Brother drivers for this printer a try; low and behold, the the afore mentioned HP PCL 6 driver performs much better (it even includes duplexing, which the Brother driver omits). The clincher was that Brother's driver really screwed up the print alignment and margins. The HP generic has no such problems. By the way, this comparison was on gnome Ubuntu Dapper 6.06.

---

