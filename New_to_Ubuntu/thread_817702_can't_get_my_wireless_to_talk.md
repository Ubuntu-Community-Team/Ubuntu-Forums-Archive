---
title: "can't get my wireless to talk"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-06-03
I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

And although the wireless card seems to be recognized I can't get it to talk to any wireless networks.

It  does not list them.

What should I do?

---

### Post by iaculallad on 2008-06-03
Try visiting this [thread]("http://ubuntuforums.org/showthread.php?t=285809"). It's updated for Feisty and hope it could work with you.

---

### Post by sam_delta on 2008-06-03
do you have a wired connection? with the wired plugged, try going into system>administration> hardware drivers, and check if theres a broadcom driver listed. if not, you can try installing b43-fwcutter, 

to install b43-fwcutter
open a terminal with a wired connection and type ```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
``` make sure you answer with YES when asked to fetch a firmware,
restart your pc, and check if internet now works or if its now listed under system>administration>hardware drivers

tell us how it goes
sam

---

### Post by sam_delta on 2008-06-03
also, making all updates might help. with a wired connection go into system>administration> update manager, i believe there are few broadcom wireless updates among all updates

sam

---

### Post by saskatchewan on 2008-06-03
I have a wired conncection and will try your suggestion.

---

### Post by sam_delta on 2008-06-03
if you can, make all updates first, before going into sys>admin>hardware drivers etc

sam

---

### Post by saskatchewan on 2008-06-03
I went to sys>addmin>hardware>drivers after doing all updates and there is a Broadcom b43 driver that is enabled but things still do not search for wireless networks.
I am going to try some of your other suggestions as well.

---

### Post by saskatchewan on 2008-06-03
I tried the 
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter

Although there is supposedly a wireless card recognized it still does not pick up any networks.
Help!!

---

### Post by sam_delta on 2008-06-03
just curious 
whats the output of 
```
 sudo iwlist scan
```
```
 iwconfig 
```
sam

---

### Post by iaculallad on 2008-06-03
Here's the step by step method to work your Broadcom Wireless BCM4312 (rev 02).

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by saskatchewan on 2008-06-03
Here is the response that I got from sudo.

allan@allan-laptop:~$ sudo iwlist scan
[sudo] password for allan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

allan@allan-laptop:~$

---

### Post by saskatchewan on 2008-06-03
and iw config

allan@allan-laptop:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

allan@allan-laptop:~$

---

### Post by saskatchewan on 2008-06-03
I tired the following instructions but I still can't get it to work.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by sam_delta on 2008-06-04
if you installed ndiswrapper, you need to disable the proprietary driver under system>admin>hardware drivers. and did you installed the correct drivers? you can find it out with the command ```
ndiswrapper -l
``` ,the output should be something like xxxx driver installed, device present, 
also, do you have your wireless settings set to roaming mode? 
sam

---

### Post by saskatchewan on 2008-06-04
The reply I get from the command ndiswrapper -l is nothing.  Here is the output:

allan@allan-laptop:~$ ndiswrapper -l
allan@allan-laptop:~$ 

I have checked the settings and roaming is enabled.

---

### Post by sam_delta on 2008-06-04
if "ndiswrapper -l" returns nothing, that means that you have not intalled any drivers

to install drivers: 

open a terminal with internet connection and type ```
mkdir Desktop/wireless
cd Desktop/wireless
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
``` 

now, confirm that the drivers installed correctly by typing  ```
ndiswrapper -l
```the output should be something like "driver xxxx installed, device present"

confirm if you get your drivers installed correctly and ill guide you through the rest of the steps, i just need to make sure you install the ddrivers correclty.

also, ull need to delete b43-fwcutter so type
```
sudo apt-get remove b43-fwcutter
``` and go into system>admin>hardware drivers and disable any wireless drivers listed in there

sam

---

