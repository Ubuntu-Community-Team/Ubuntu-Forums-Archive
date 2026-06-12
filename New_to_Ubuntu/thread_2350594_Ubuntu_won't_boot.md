---
title: "Ubuntu won't boot"
date: 2017-01-25
forum: New to Ubuntu
---

### Post by quicktruck on 2017-01-25
Hi, I ran the boot repair utility on one of our Ubuntu servers for our Direct TV systems.  The reason I did this was that the Server had frozen and rebooted itself.  It was coming up to the GRUB but when you entered a password the screen would go black and then a warning would flash stating that there was no storage space available.  After trying this a couple times, it quit booting at all.  All it would do is look to the CD drive, then the HD and then the network.  I ran the Boot Repair CD which let me find the file that had eaten up the entire 1TB.  It was a log file, absolutely no idea how this happened as all previous log files were 1MB.  I copied the log file to another drive and then removed it from the server.  This opened up about 900GB on the server.  Then ran the boot repair.  The machine still will not boot.  The software installed on it is proprietary from Direct TV so they are saying if we cannot get it going, we will be forced to buy another server.  There is a ton of setup once one of these is received to get it working with all the rooms so I am really hoping we can bring this back to life.  Here is the link provided by the repair tool.  Any help would be greatly appreciated!   [http://paste.ubuntu.com/23865734/](http://paste.ubuntu.com/23865734/)

---

### Post by quicktruck on 2017-01-27
Disregard, it is now up and running

---

