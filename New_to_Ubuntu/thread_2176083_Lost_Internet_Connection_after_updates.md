---
title: "Lost Internet Connection after updates"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2013-09-22
This afternoon i installed 12.04 LTS on an old laptop i was given. All went fine, and all seemed to work.

Of course it had 600 updates to do, which i let it plod on with, BUT since it finished i lost my wired internet (I have not even thought about wireless yet).

The little Radar at the top now says 'No network devices available' when i right click.

I am presuming it has installed something wrong or bad driver etc.....

Can anyone dive me an idea how to resolve my problem.

Many Thanks in advance ;)

---

### Post by Hadaka on 2013-09-22
Hi, please post the output of..
```
lspci -nn | egrep '0200|0280'
```
*if it is a broadcom card all i need to have you
post back is the 2  [14e4XXXX] numbers.
thanks.

---

### Post by MadMonkey1966 on 2013-09-22
Many thanks for your help Hadaka...i tried what you said and got this back..

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Any help ? :)

---

### Post by Hadaka on 2013-09-22
Hi, please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
boot
you should now have a working wired connection.
from the wired connection..connected to the internet
please do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
disconnect the ethernet cable...boot
you should now have wireless.
post back the results please
thanks.

---

### Post by MadMonkey1966 on 2013-09-22
You are a star Hadaka...this is what i got
madmonkey@madmonkey-MM061:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for madmonkey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,952 kB of archives.
After this operation, 8,980 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Fetched 3,952 kB in 1s (3,777 kB/s)                 
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 169180 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
madmonkey@madmonkey-MM061:~$ sudo modprobe b43
madmonkey@madmonkey-MM061:~$ 


My wired connection is working, and it has detected the wireless as well :)

Many Thanks, hope that was not too much hassle for you
Cheers ):P

---

### Post by Hadaka on 2013-09-22
You did GREAT !!, glad its working.

---

