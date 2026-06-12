---
title: "HOW TO: Broadcom wireless + wpa + fix fatal errors"
date: 2006-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by mrvgarg on 2006-11-01
After reading many broadcom wireless guides this is what finally worked for me. You should also install automatix2

Open terminal and type this:

sudo rmmod bcm43xx

sudo gedit /etc/modprobe.d/blacklist

add "blacklist bcm43xx" to the bottom of the file. Without the quotation marks. 

Close terminal.
Open automatix2 and install ndwiswrapper.

Download your broadcom driver from the manufacturer's site to your desktop. If it is a .exe file use cabextractor to extract it. You should have a .inf and .sys file.

Open terminal. and go to desktop. (cd Desktop). Now type

sudo ndiswrapper -i bcmwl5.inf

sudo ndiswrapper -m

sudo gedit /etc/modules
and add ndiswrapper

sudo modprobe ndiswrapper

At this stage if you get fatal errors do

sudo apt-get install ndiswrapper-utils-1.8 ndiswrapper-utils-1.1 ndiswrapper-utils ndiswrapper-common

To get WPA working install the network manager.

---

### Post by accel on 2006-11-01
I also tried the other guides and I also had the fatal error message
a couple of times. 
I managed to get my Broadcom 4306 pcmcia card (linksys) working but when I restart Ubuntu the connection is lost and I have to start it manually every time I restart.

Does your guide "hold" the wlan connection after a restart?

---

### Post by mrvgarg on 2006-11-01
No it does not. I am on kubuntu so knetworkmanager always ask me for the password.

---

### Post by nutz on 2007-08-13
I used this guide and it worked perfectly! This is on an HP Pavilion zv6000 notebook.

One final question. When the process is complete is it okay to delete the two driver files or do they need to remain in place? I just dumped them in my home directory for the install and was wondering if I can delete them now that the wireless is working.

Thank for sharing!

---

### Post by nutz on 2007-08-13
Also...

Could you explain the process of getting wpa working? I have the network manager installed and it does detect wpa from the router and prompt for the passphrase but it doesn't connect after I provide the passphrase.

---

### Post by totalnub on 2007-08-28
nutz, do you have an actual zv6000? i had wireless working in edgy, but when i went to fiesty, it broke and now i'm back at school where wireless is my friend. any help is appreciated. btw my ifconfig and iwconfig are as follows.....notice i don't even have a wlan0 or anything of the sort.
```
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0F:B0:6D:52:0E  
          inet addr:146.201.176.178  Bcast:146.201.176.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe6d:520e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:95031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96209145 (91.7 MiB)  TX bytes:4686093 (4.4 MiB)
          Interrupt:20 Base address:0x6400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB)

clay@claylap:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.


```

---

