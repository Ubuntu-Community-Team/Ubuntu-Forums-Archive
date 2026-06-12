---
title: "wireless help (bcm43xx-fwcutter won't install)"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by help_moi on 2008-09-24
having only recently got ubuntu i have been having fun learning this unique OS but im stuck :(

I can't seem to download bcm43xx-fwcutter everytime i download and extract it i get this error in terminal:

```
zahir@zahir-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  bcm43xx-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.6kB of archives.
After unpacking 119kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bcm43xx-fwcutter.
(Reading database ... 105103 files and directories currently installed.)
Unpacking bcm43xx-fwcutter (from .../bcm43xx-fwcutter_1%3a006-1_i386.deb) ...
Setting up bcm43xx-fwcutter (006-1) ...
--05:13:14--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 209.85.173.118
Connecting to boredklink.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
05:13:15 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

:(, every time no matter what i do it get this

this is the driver i have:

```
zahir@zahir-laptop:~$  lspci | grep Broadcom\ Corporation
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

any help would be much appreciated

---

### Post by help_moi on 2008-09-24
tried installing it with synaptic and got the same thing

---

### Post by help_moi on 2008-09-24
is it because the file no longer exists?

---

### Post by RavUn on 2008-09-24
this link may help you:
[http://forums.debian.net/viewtopic.php?p=136863&sid=76f9928f04c1831fc038d6ff07abbcf8](http://forums.debian.net/viewtopic.php?p=136863&sid=76f9928f04c1831fc038d6ff07abbcf8)

---

### Post by help_moi on 2008-09-24
Cheers for anyone else having the same problem you can get the download here

[http://www.speedyshare.com/214793933.html](http://www.speedyshare.com/214793933.html)

Thanks again :D

---

