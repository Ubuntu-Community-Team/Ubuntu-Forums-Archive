---
title: "wifi not working on ubuntu 12.04LTS and WIndows 7 but works on ubuntu 10.10"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by ZelAlex on 2012-08-04
I am using a wifi connection to connect to internet. I was having problems connecting to wifi in WIndows 7 but it was working fine in ubuntu 10.10. 


I was trying to update my ubuntu and finally did to 12.04LTS. But wifi stopped working. I had to uninstall 12.04LTS and reinstall 10.10. My wifi is working nicely in 10.10. 
Why is it not working on 12.04 and windows 7? ANy ideas?

I am using same wifi on all three -  windows 7, ubuntu 10.10 and 12.04LTS. But wifi is working only on 10.10.

Links to window forum and the update ubuntu prob

[http://ubuntuforums.org/showthread.php?t=2036495](http://ubuntuforums.org/showthread.php?t=2036495)

[http://windows7forums.com/windows-7-networking/83371-internet-working-ubuntu-but-not-windows-7-a.html](http://windows7forums.com/windows-7-networking/83371-internet-working-ubuntu-but-not-windows-7-a.html)

---

### Post by kc1di on 2012-08-04
It would be helpful if we knew what wireless card your machine has.

in a terminal type the following command and post the output here.

thank you,

```
lspci
```
Where the l is a lower case L not # 1.

---

### Post by ZelAlex on 2012-08-04
The output to lspci is:


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 1 8 )
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 1 8 )
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
12:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by thatguruguy on 2012-08-04
It appears that the kernel module for the wireless card you are using has issues with wireless N.

You may want to read [this thread]("http://ubuntuforums.org/showthread.php?t=1966860"). In particular, you may want to follow the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=11888778&postcount=36").

---

### Post by ZelAlex on 2012-08-04
I reinstalled Ubuntu 12.04LTS. And the wifi started working on its own. Don't Know what happened

EDIT:
I tried to use update manager but it told me to check my internet connection and in the details were some weird messages. Something wicked happened

> 
W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.


EDIT:
[http://ubuntuforums.org/showpost.php?p=10479823&postcount=3](http://ubuntuforums.org/showpost.php?p=10479823&postcount=3)
This solved it

---

