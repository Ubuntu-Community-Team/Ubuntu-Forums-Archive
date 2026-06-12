---
title: "help w/ this error report please"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by determinedblkman on 2008-08-30
root@linspire:~# cd /home/david/ndiswrapper-1.53
root@linspire:/home/david/ndiswrapper-1.53# make
make -C driver
make[1]: Entering directory `/home/david/ndiswrapper-1.53/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.20-16-lowlatency/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/david/ndiswrapper-1.53/driver'
make: *** [all] Error 2
root@linspire:/home/david/ndiswrapper-1.53# ver
-su: ver: command not found

card specs:

Linksys WMP54G Wireless-G PCI Adapter
Networking 
Connectivity technology Wireless  
Networking type Network adapter  
Data link protocol IEEE 802.11b, IEEE 802.11g  
Data transfer rate 54 Mbps  
Status indicators Link activity  
Transport protocol TCP/IP, IPX/SPX, NetBEUI/NetBIOS  
Bandwidth 2.4 GHz  
Spread Spectrum Method DSSS, OFDM  
Networking standards IEEE 802.11b, IEEE 802.11g  
Line coding format CCK, OFDM, DBPSK, DQPSK

---

### Post by cariboo on 2008-08-30
You don't have to build ndiswrapper, the packages are on the livecd. Make sure how have the cdrom enabled in System-->Administration-->Software Sources. Then use Add/Rmove Programs, Synaptic package manager or the command line to install it.

An alternate method is to navigate to pool/main/n on the cdrom and just double click ndiswrapper-utils and gdebi will automatically install the packages for you. There is also a gui to help with installing your windows drivers. It is called ndisgtk it is also on the cdrom.

Jim

---

### Post by determinedblkman on 2008-08-30
> **cariboo907 said:**
> You don't have to build ndiswrapper, the packages are on the livecd. Make sure how have the cdrom enabled in System-->Administration-->Software Sources. Then use Add/Rmove Programs, Synaptic package manager or the command line to install it.

An alternate method is to navigate to pool/main/n on the cdrom and just double click ndiswrapper-utils and gdebi will automatically install the packages for you. There is also a gui to help with installing your windows drivers. It is called ndisgtk it is also on the cdrom.

Jim

the name of the OS is "linspire 6.0" it's under ubuntu. i dont see the dirctory ur talking about. i'm really concern about the module line of the error (ie. lib/module/????/build  not present)

---

