---
title: "ubuntu not booting"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by mattc1977 on 2013-01-19
Hi Guys
On trying to boot ubuntu I get the message 
***gave up waiting for root device common problems:***
[I][B]-Boot args (cat /proc/cmdline)
-Boot rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; is/dev)
ALERT! /dev/disk/by-uuid/d7316e33-33bc-4b58-9fdf-852da57f7cf3 does not exist.
Dropping to a shell!

Busy Box v1.19.3 (ubuntu 1:1.19.3-7ubuntu)built-in shell (ash)
Enter 'help' for a list of built in commands.[/B][/I]

***(initramfs)***

I read that for some people its possible to type exit at this point to get it to boot but that dosnt work for me.
Im running ubuntu 12.10

Id be very great full of any help
Also im very green and not overly sure what im doing.
Many thanks :)

---

### Post by audiomick on 2013-01-19
It looks to me like it is having trouble reading the drive for some reason. First thing to do is make sure all connections are properly seated. If it is a desktop, open it up and unplug and reconnect the cables on the Hard drive. Sometimes the contacts can get dirty. If it is a laptop with a drive that can be taken out, make sure it is seated properly. 

Having done that, go here

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Use the option to generate a boot info summary. Post the results. There is a lot of useful info in there about the state of your computer.

---

### Post by mapes12 on 2013-01-19
Describe how you have installed Ubu? E.g. as a standalone OS, dual boot with something else, using wubi, in a VM etc. etc.

---

### Post by mattc1977 on 2013-01-19
its a stand alone :)

---

### Post by mapes12 on 2013-01-19
Looks to me like something screwed up when you installed Ubu.If the machine your installing on doesn't have any critcal stuff on it then I'd start again. But before installing Ubu I'd completely blank the HDD with something like Killdisk. Then install Ubu and let the GUI installation wizard lead the way by accepting all the defaults. You should then get a running system on your HDD.

Welcome to the land of fun.

---

