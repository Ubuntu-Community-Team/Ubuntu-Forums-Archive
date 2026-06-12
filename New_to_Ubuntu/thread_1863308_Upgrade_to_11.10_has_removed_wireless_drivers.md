---
title: "Upgrade to 11.10 has removed wireless drivers?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by pablo0151 on 2011-10-17
Hi all

I'm sorry if this has already been covered, I did search but couldn't find this specific query.

I've just updated to 11.10 and after the PC restarted I seem to have the ability to connect to the internet over wireless. After reading the help section I tried to install any missing drivers, but the upgrade has somehow locked me out of authenticating any changes, and I can't download updates because I'm not online.

If anyone could shed some light I'd most grateful...reaching my wit's end with this now!

Cheers

Paul

---

### Post by TeoBigusGeekus on 2011-10-17
Can you post us the output of
```
lshw -C network
```
and
```
ifconfig
```
?

---

### Post by pablo0151 on 2011-10-17
> **TeoBigusGeekus said:**
> Can you post us the output of
```
lshw -C network
```
and
```
ifconfig
```
?


Thanks for getting back to me, the outputs:

lshw -C network:

pablo0151@Nettopski:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:0e:7c:28
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fbffb000-fbffbfff memory:fbffc000-fbffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

ifconfig:

pablo0151@Nettopski:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr d0:27:88:0e:7c:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4800 (4.8 KB)  TX bytes:4800 (4.8 KB)



If there's anything else I can provide, just let me know.

Paul

---

### Post by jawilljr on 2011-10-17
To answer your question... yes your drivers were removed by this [this commit.](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fefecc6989b4b24276797270c0e229c07be02ad3)

Please post output of:

```
cat /etc/modprobe.d/blacklist.conf
```

Jerry

---

### Post by pablo0151 on 2011-10-18
> **jawilljr said:**
> To answer your question... yes your drivers were removed by this [this commit.](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fefecc6989b4b24276797270c0e229c07be02ad3)

Please post output of:

```
cat /etc/modprobe.d/blacklist.conf
```

Jerry


Sorry for the late reply, I've only just finished work, the output is:


pablo0151@Nettopski:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
#

alias expansion, usually so some other driver will be loaded for the
# device instead.

# 

evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

#

replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# 

causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

#

snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
#

hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

#

Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

#

causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

#

replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

#

most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

#

replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

#

low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

#

ugly and loud noise, getting on everyone's nerves; this should be done by a
#

nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
#

from being initialised (Ubuntu: #297750). Blacklist so that the driver
#

continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800pci

Thanks again.

---

### Post by pablo0151 on 2011-10-19
Sorry to bump my own thread, but can anyone help with the above?

Cheers

Paul

---

### Post by fontis on 2011-10-20
I've got RT3090 as well, before 11.10 I used to just blacklist a few drivers and it would work.. but now that doesn't work anymore.

I also tried to force install the Ralink drivers from the PPA but its still fubar.

---

### Post by amjjawad on 2011-10-20
How to blacklist: [http://ubuntuforums.org/showpost.php?p=10987428&postcount=17](http://ubuntuforums.org/showpost.php?p=10987428&postcount=17)

How to reactivate: [http://ubuntuforums.org/showpost.php?p=11005305&postcount=23](http://ubuntuforums.org/showpost.php?p=11005305&postcount=23)

---

