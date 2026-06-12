---
title: "Compiling Broadcom STA driver in kernel 2.6.30RC"
date: 2009-05-03
forum: Packaging and Compiling Programs
---

### Post by jordan420 on 2009-05-03
hello everybody. i was wondering if i could get some help with compiling the broadcom wireless driver in the new dev kernel. Ive read the readme and i follow the directions to a T. but i get this error ```
j@laptop:~/hybrid$ ls
broadcom-sta-5.10.79.10-linux-2.6.29.patch  built-in.o  lib  Makefile  src  wl_iw_v2.patch
j@laptop:~/hybrid$ make -C /lib/modules/2.6.30-020630rc3-generic/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
  CLEAN   /home/j/hybrid/.tmp_versions
make: Leaving directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
j@laptop:~/hybrid$ make -C /lib/modules/2.6.30-020630rc3-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
  LD      /home/j/hybrid/built-in.o
  CC [M]  /home/j/hybrid/src/wl/sys/wl_linux.o
/home/j/hybrid/src/wl/sys/wl_linux.c:60:27: error: net/ieee80211.h: No such file or directory
make[1]: *** [/home/j/hybrid/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/j/hybrid] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
j@laptop:~/hybrid$

``` any suggestions?

---

### Post by fakbill on 2009-05-06
Looks like gentoo guys have released a set of patches to solve this issue.
However, i was not able to apply them (some parts get rejected).

---

### Post by fakbill on 2009-05-07
With these two patches:

[http://llama.gs/stuff/hybrid-portsrc-x86_32-v5_10_79_10.patch](http://llama.gs/stuff/hybrid-portsrc-x86_32-v5_10_79_10.patch)
and
[http://bugs.gentoo.org/attachment.cgi?id=189250](http://bugs.gentoo.org/attachment.cgi?id=189250) 
I'm able to compile the wl 5_10_79_10 module on a 2.6.30-rc4.
Be careful, it is *not* the last version of the driver (I was not able to find patches for the last version)

I do load the wl module at boot time (/etc/modules)
However, avahi does no create any eth1 wireless interface.
It looks like avahi is happy with this new module (no crash) but it does not detect the wireless card neither it creates the network interface.

No real clue why up to now...

---

### Post by fakbill on 2009-05-08
ok. For some reason, the ssb module is loaded at boot time.
It should not if you want to use wl (at lest on my box).
Without this ssb module loaded, the wl module works just fine :D

---

### Post by jordan420 on 2009-05-10
oh sorry man i hadnt been checking my threads... i will try to compile later tomorrow. anyway you are saying i have to blacklist the ssb module before i insmod? and i also need to apply both patches?

---

### Post by Amaranth on 2009-05-10
Based on the patches mentioned above I've patched the 5.10.91 driver to work with the 2.6.30-2-generic kernel in karmic. This is the first time I've been able to actually connect to a wireless network with 2.6.30 as my previous attempts at patching led to a driver that worked but wouldn't do DHCP.

I've attached the updated patch I used to make this work.

---

### Post by jordan420 on 2009-05-11
@amaranth  could you umm refresh me on how to patch source code in ubuntu? and does 2.60.30-2 mean i can  use this on the latest kernel (rc4)? just trying to make sure i dont want to screw anything up.

---

### Post by jordan420 on 2009-05-11
Ok. thanks to you guys i have managed to get my wireless up and running in the new kernel! im ecstatic. marking solved.

---

### Post by Kyle_ on 2009-05-22
Thanks for the patch worked first try on 2.6.30-5-generic!

---

### Post by tux21 on 2009-05-23
made note of this
it seems to be the driver version which have different different patches not the kernel

the patch above works for 2.6.29.4
save as .pl instead of .txt

apply 

patch -p1 < broadcom-sta-5.10.91.9-linux-2.6.30.patch.pl 

where you extracted the driver and build

works only for this sta driver version

---

### Post by ortizdante on 2009-05-25
Thanks Amaranth !!

I has been trying to compile the module with other patch files without success, this patch runs great in 2.6.29-04 !!  ;)

My configuration is HP Mini Note 2140, after upgrade to 2.6.29 (because 2.6.28 has usbserial as internal module & I can't mount my mobile modem), but with this patch everythig is runs again!

Great work !

---

### Post by Vaun on 2009-05-25
I've been using the debian sid packages along with module assistant on my Dell Vostro A90 and it's been working great for the last three kernels.  I'm now on 2.6.30rc7.

[http://packages.debian.org/sid/broadcom-sta-source]("http://packages.debian.org/sid/broadcom-sta-source")

[http://packages.debian.org/sid/broadcom-sta-common]("http://packages.debian.org/sid/broadcom-sta-common")

```
sudo apt-get install module-assistant
```

Then from command line run:

```
sudo module-assistant
``` 

Follow the steps and select broadcom-sta.

---

### Post by tbonedude on 2009-05-30
Hey, I wanted to thank [[COLOR=#76482c]**Amaranth**[/COLOR]]("http://ubuntuforums.org/member.php?u=11397") and others for this info on getting the sta driver working on custom kernels.  I got it up and running with no problems, but since I got it working, I cant see my wired Ethernet connection in network-manager.  I can see it when using b43, but not STA.  I would really like to keep using STA (as I get much better reception with it).  Any help would be greatly appreciated!! :)

---

### Post by heluani on 2009-06-04
> **Amaranth said:**
> 
I've attached the updated patch I used to make this work.

Thank you very much!

R.

---

### Post by Mikrozaur on 2009-06-24
> **Amaranth said:**
> Based on the patches mentioned above I've patched the 5.10.91 driver to work with the 2.6.30-2-generic kernel in karmic. This is the first time I've been able to actually connect to a wireless network with 2.6.30 as my previous attempts at patching led to a driver that worked but wouldn't do DHCP.

I've attached the updated patch I used to make this work.

Thx for patch

---

### Post by Amaranth on 2009-06-24
Ok guys, you can stop using my patch. :) Just install the bcmwl-kernel-source package. It uses dkms to automatically build for your kernel on updates.

---

### Post by tbonedude on 2009-07-03
any way to get  bcmwl-kernel-source in jaunty?  It doesn't show up in the repos.

---

### Post by agazzo on 2009-07-12
thank you so much amaranth! now i finally get my wireless working again in 2.6.30 kernel :)

---

### Post by CJIECAPb on 2009-07-17
Do somebody know how to compile the module in jaunty for 2.6.31-rc3?

---

### Post by Vaun on 2009-07-17
```
sudo apt-get install bcmwl-kernel-source
```

```
sudo modprobe wl
```

---

### Post by CJIECAPb on 2009-07-17
> **Vaun said:**
> ```
sudo apt-get install bcmwl-kernel-source
```

```
sudo modprobe wl
```
This package don't included in jaunty.

---

### Post by CJIECAPb on 2009-07-18
Install bcmwl-kernel-source in jaunty from keramik.
It's work.

---

### Post by JamieKitson on 2010-10-07
Since this is the first hit for "compile braodcom driver" I thought I'd add my two-penneth.

If you get an error such as:

```
In file included from /home/jamie/Downloads/src/shared/linux_osl.c:19:
/home/jamie/Downloads/src/include/linuxver.h:23: fatal error: linux/autoconf.h: No such file or directory
```

You probably need to apply the first patch as described in the txt file.

If you then get an error such as:

```
/home/jamie/Downloads/src/wl/sys/wl_linux.c: In function &#8216;_wl_set_multicast_list&#8217;:
/home/jamie/Downloads/src/wl/sys/wl_linux.c:1434: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_list&#8217;
/home/jamie/Downloads/src/wl/sys/wl_linux.c:1434: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/jamie/Downloads/src/wl/sys/wl_linux.c:1435: error: dereferencing pointer to incomplete type
/home/jamie/Downloads/src/wl/sys/wl_linux.c:1441: error: dereferencing pointer to incomplete type

```

You probably need to apply the second patch in much the same way.

After copying the wl.ko file as described in the readme add "wl.ko" to /etc/modules. Unfortunately it seems a little slow to start, but it works.

---

