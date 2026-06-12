---
title: "Having several isses... [External DVD Drive and Internet]"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by innoxium on 2008-11-12
Okay, I have just moved from Windows XP to Xubuntu because I have been having issues with XP since my internal cd/dvd drive crapped out on me.

Now I have a external dvd writer, that works when I switched over [that's how I got Xubuntu on the laptop in the first place] but now it won't work, Xubuntu tells me that it's not a mounted drive.

On top of that, neither the wired or wireless internet connections work on my laptop, can't even seem to get them to work at all.

Some information though: I am on a Dell d810 Latitude, that is about three years old. WAS a Windows XP with SP2, just changed it about a week ago to Linux.

The External DVD writer I got is a HP dvd1040e, really big honking thing, but I got it for what I wanted to use it for, I don't care about size and weight of it.

When I do the lsusb command, it says that my HP drive is connected, but it still won't do work.

My internet is connected through a router, and when I hardwire it the laptop gets a router, but NOTHING comes up on Firefox.

help. Please. =(

-noxy

---

### Post by bobnutfield on 2008-11-12
1.  Open a terminal and type:

> sudo fdisk -l

This will list the attached disks on your system.  It may be a matter of just mounting the drive manually.

2.  Go to System>Preferences>Network configuration and make sure the wired setting is set to DHCP.  Open a terminal and type:

> sudo ifconfig -a

This will list all of your network devices and determine if an IP address is being assigned.  This will also indicated if your wireless chipset is being detected.  

Post this information and we may be able to help you.

---

### Post by innoxium on 2008-11-13
After running the sudo fdisk command I got:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
innoxium@thecougarianproject:~$ 

```

After running the sudo ifconfig command I got:

```
eth0      Link encap:Ethernet  HWaddr 00:14:22:E9:F6:5A  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fee9:f65a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9982 (9.7 KiB)  TX bytes:1554 (1.5 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878 (878.0 b)  TX bytes:878 (878.0 b)


```

---

### Post by innoxium on 2008-11-20
bumpity bump

---

### Post by superprash2003 on 2008-11-20
post output of the following commands from the terminal
1)lshw -C network
2)iwconfig

---

