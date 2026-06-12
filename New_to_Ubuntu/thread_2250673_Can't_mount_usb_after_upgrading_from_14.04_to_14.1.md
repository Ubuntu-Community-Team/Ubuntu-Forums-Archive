---
title: "Can't mount usb after upgrading from 14.04 to 14.10"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by sn0m on 2014-10-30
Hi
Dont seem to be able to mount usb drive anymore since upgrading.
Whenever I connect my Nook ereader and click on it I get:
Unable to access location, an operation is already pending
After leaving it for a bit, nothing happens.
Any idea how to restore this basic computer function????
also this is what I get from kernel:
koli@koli-K53E:~$ dmesg | grep error
[37135.650542] compiz[383]: segfault at 409000f5 ip b761ba6b sp bfe492cc error 4 in libstdc++.so.6.0.20[b758f000+e9000]
[40984.240440] gpartedbin[11123]: segfault at 0 ip b68e7010 sp bfeafb08 error 4 in libc-2.19.so[b67b4000+1a8000]
[41600.702707] hud-service[2383]: segfault at b3dce990 ip b3dce990 sp bf9aec70 error 15
######################
and also
koli@koli-K53E:~$ lsusb
Bus 002 Device 025: ID 2080:0003 Barnes & Noble NOOK Simple Touch
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:5120 IMC Networks 
Bus 001 Device 062: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
koli@koli-K53E:~$ 
#####

So any help is greatly appreciated
Koli
koli@koli-K53E:~$

---

### Post by sn0m on 2014-11-08
So I went back to 14.04 and everything was working fine for a while. However I was asked to install updates and I did. Guess what, the dreaded "An operation is already pending" warning came back when plugging in my usb drive. So now I have to drop to root and mount it manually to allow transfer of files, obviously there are risks involved as Im operating using sudo... Why couldn't they leave it alone......
Anyway, enough of a rant and I hope someone looks into this....

---

### Post by sudodus on 2014-11-08
> **sn0m said:**
> Hi
Dont seem to be able to mount usb drive anymore since upgrading.
Whenever I connect my Nook ereader and click on it I get:
Unable to access location, an operation is already pending
After leaving it for a bit, nothing happens.
Any idea how to restore this basic computer function????
also this is what I get from kernel:
koli@koli-K53E:~$ [COLOR=#ff0000]dmesg | grep error
[37135.650542] compiz[383]: segfault at 409000f5 ip b761ba6b sp bfe492cc error 4 in libstdc++.so.6.0.20[b758f000+e9000]
[40984.240440] gpartedbin[11123]: segfault at 0 ip b68e7010 sp bfeafb08 error 4 in libc-2.19.so[b67b4000+1a8000]
[41600.702707] hud-service[2383]: segfault at b3dce990 ip b3dce990 sp bf9aec70 error 15[/COLOR]
######################
and also
koli@koli-K53E:~$ lsusb
Bus 002 Device 025: ID 2080:0003 Barnes & Noble NOOK Simple Touch
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:5120 IMC Networks 
Bus 001 Device 062: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
koli@koli-K53E:~$ 
#####

So any help is greatly appreciated
Koli
koli@koli-K53E:~$

[I marked the error output red.]

It seems nobody know how to help you. And no, I don't understand it, but maybe we can get a discussion and some trouble-shooting started:

There is an error involving compiz. Maybe the NOOK Simple Touch is not compatible with compiz. If you try another flavour of Ubuntu, for example ***Xubuntu***, which does not use compiz, it might work better.

Edit: Have you considered filing a bug report at Launchpad?

---

### Post by whitesmith on 2014-11-08
+1 to @sudous for suggesting Launchpad. Far too many people encounter bugs with open source SW and just kick the can by saying, "Oh, well, it's only FOSS. You get what you pay for." No, no, no. Ubuntu is a top-shelf production worthy in every respect of  comparison to any OS, including, especially, that thing from the Pacific Northwest. But this is only possible because there are so many eyes on this OS, finding and fixing bugs before their counterparts in the commercial world are even noticed. If everyone--OK, most everyone--does a small part there's simply no way of putting brakes on the the FOSS movement. Maybe @sudous is right when he says, "There is an error involving compiz. Maybe the NOOK Simple Touch is not compatible with compiz. If you try another flavour of Ubuntu, for example Xubuntu, which does not use compiz, it might work better." There's only one way to find out. If his suggested solution works, please help others by using Thread Tools to mark the thread as solved. Warm regards to you.

---

### Post by sn0m on 2014-11-08
Hi,thanks for your replies. I am currently using lubuntu 14.04
It was working fine with everything just berfore the last update, which makes me think it is due to a bug in the kernel. The issue seem to be for all external hard hard drives, ie usb drives, not just Nook.
This is what I get after plugging my usb drive:
koli@koli-K53E:~$ dmesg | grep error
[   13.118187] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   92.101827] type=1400 audit(1415428158.575:65): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/" pid=2125 comm="init" fstype="proc" srcname="proc" flags="rw"
[   92.101864] type=1400 audit(1415428158.575:66): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/sys/" pid=2125 comm="init" fstype="sysfs" srcname="sysfs" flags="rw"
[   92.314337] type=1400 audit(1415428158.787:69): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/run/user/112/gvfs/" pid=2275 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
[ 1786.026603] type=1400 audit(1415429869.628:387): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/" pid=4938 comm="init" fstype="proc" srcname="proc" flags="rw"
[ 1786.026675] type=1400 audit(1415429869.628:388): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/sys/" pid=4938 comm="init" fstype="sysfs" srcname="sysfs" flags="rw"
[ 1786.337747] type=1400 audit(1415429869.940:391): apparmor="DENIED" operation="mount" info="failed mntpnt match" error=-13 profile="/usr/lib/lightdm/lightdm-guest-session" name="/run/user/113/gvfs/" pid=5109 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
[ 7419.577884] rndis_host: probe of 2-1.3:1.0 failed with error -71
[ 7419.595815] rndis_wlan: probe of 2-1.3:1.0 failed with error -71
koli@koli-K53E:~$ 

Ta
Koli

---

### Post by sudodus on 2014-11-09
Please report it as a bug at Launchpad. The more details you provide, the better.

And please add a link to the bug report in a reply here.

---

### Post by sn0m on 2014-11-09
thanks, will do.

---

