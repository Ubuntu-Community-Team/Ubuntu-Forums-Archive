---
title: "Netgear WG311 problems"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by ncoop23 on 2008-07-09
So I have read a lot on here about how easy it is to install this card but I am having lots of problems with it...  Here is what I did.  This is a fresh install of 8.04.1 on a emachine T2245.  Any help is greatly appreciated!

```

elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ ls
WG311v3.cat  WG311v3.INF  WG311v3.sys  WG311v3XP.sys
elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ ndiswrapper -l
No drivers installed

elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ sudo modprobe -v -n ndiswrapper
insmod /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko 

elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ sudo ndiswrapper -i WG311v3.INF
Installing wg311v3
Forcing parameter AdhocGMode|1 to AdhocGMode|0
Forcing parameter AdhocGMode|1 to AdhocGMode|0

elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ sudo modprobe ndiswrapper
elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ sudo modprobe -r ndiswrapper
elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ sudo modprobe ndiswrapper

[ 1491.103085] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1491.120651] usbcore: registered new interface driver ndiswrapper
[ 1550.630336] usbcore: deregistering interface driver ndiswrapper
[ 1553.027565] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1553.043277] usbcore: registered new interface driver ndiswrapper

elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ iwlist scan
lo        Interface doesn't support scanning.

elsie@elsie-desktop:~/Drivers/good_WG311v3-driver$ iwconfig
lo        no wireless extensions.

```

I did all that and still nothing in iwconfig, I am lost...

---

### Post by ncoop23 on 2008-07-10
Bump.  Does anyone have an idea on this?  it is really bugging me.

---

### Post by ncoop23 on 2008-07-14
anyone?

---

### Post by martbuang on 2008-07-14
Have you read this How-to;

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

---

