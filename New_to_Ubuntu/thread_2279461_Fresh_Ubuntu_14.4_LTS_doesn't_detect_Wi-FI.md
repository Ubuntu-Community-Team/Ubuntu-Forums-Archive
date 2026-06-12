---
title: "Fresh Ubuntu 14.4 LTS doesn't detect Wi-FI"
date: 2015-05-23
forum: New to Ubuntu
---

### Post by Sonihal on 2015-05-23
I just installed Ubuntu 14.4 LTS on 32-bit Dell Inspiron 1545 (that was actually pre-packaged with Ubuntu 10.x in about 2010).


  For some reason, it doesn't have the capacity to scan for nearby wi-fi network.


  I tried adding wi-fi network manually, but Ubuntu still acts as if it doesn't know about wireless

[IMG]http://i.stack.imgur.com/Az9JV.png[/IMG]




When I try executing


  sudo apt-get install linux-firmware-nonfree



  I get error 


  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



  I'm at my wits end!

UPDATE

sonihal@sonihal-Inspiron-1545:~$ lspci -knn | grep Net -A2 

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)     Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]     Kernel driver in use: b43-pci-bridge

---

### Post by grahammechanical on 2015-05-23
Did you install using an ethernet (wired) connection? Then you should have a network manager icon (2 arrows pointing in opposite directions) in the top panel. click on it do you see a list of wireless access points in range? Is there a tick mark against Enable WiFi?

You may need a driver but I do see "kernel driver in use." Perhaps you have 2 wireless network adapters and the one you are using does not have a driver. Go to System Settings>Software & Updates>Additional Drivers tab and see if you get offered an wireless driver for that Broadcom card.

Regards.

---

### Post by Sonihal on 2015-05-23
Actually I got it solved.

I executed:


lspci -knn | grep Net -A2

and got

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)     Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]     Kernel driver in use: b43-pci-bridge


Then I was advised to execute the following

sudo apt-get install bcmwl-kernel-source
sudo modprobe -r b43 bcma
sudo modprobe wl


Now I am connected via wi-fi

---

### Post by RobGoss on 2015-05-23
Great to see you got it resolved good job.

---

