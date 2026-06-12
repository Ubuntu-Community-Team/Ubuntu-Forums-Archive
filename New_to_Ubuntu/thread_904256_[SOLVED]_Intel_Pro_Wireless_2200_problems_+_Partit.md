---
title: "[SOLVED] Intel Pro Wireless 2200 problems + Partitioning Problems"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by kokonobs on 2008-08-29
Hi everyone,
Hope you can help.
2 days ago i begun my ubuntu journey. I managed to install the latest version, Debian i think its called, with the help of another ubuntu user. After installation network manager does not automatically see wireless networks. My wireless card is Intel Pro Wireless 2200bg on an acer aspire 1690WLMi. I replaced the default ubuntu install drivers(ipw2100) with the new one from intel, ipw2200( there were 3 of them contained in the folder). I always have to turn on the wireless manually (2 presses of the switch) and then enter the password manually each time i reboot. My wireless comes up as eth1 with 'iwconfig' ,  any idea how to fix this? The led doesn't work either.
Second problem is, when i log into windows(XP home), the partitions i created during the installation of ubuntu dont show up, only the only partition shows. This is what i had: XP Operating system on 30GB partition and an empty 30GB partition. This is was i did during the installation: I repartitioned the drive with the XP on it to 20GB, added 4 more partitions, one for ubuntu (6GB) one for /home(15GB), one for /windows(15GB) and a swap one (2GB).
NB: I have been using XP foreva and i'm a complete beginner in Ubuntu so please make instructions as easy as possible.  :)

Thanks in advance

K

---

### Post by Crafty Kisses on 2008-08-29
Post the results of ```
lshw -C network
```

---

### Post by kokonobs on 2008-08-29
I forgot to mention, i'm at work at the moment, i'll but in the code as i get home. Sorry for that.

---

### Post by Crafty Kisses on 2008-08-29
OK be sure to do that and I'll get back to you. :)

---

### Post by kokonobs on 2008-08-29
kosi@kiki:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:65:7c:49
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.10.9 latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:a2:78:ad
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5788-v3.01 latency=32 mingnt=64 module=tg3 multicast=yes


for iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Ghana"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:9F:FA:7A   
          Bit Rate:36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=80/100  Signal level=-49 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


ifconfig
eth0      Link encap:Ethernet  HWaddr <mac add)>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr <mac add>  
          inet addr:192.168.10.9  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe65:7c49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:459 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:372898 (364.1 KB)  TX bytes:81258 (79.3 KB)
          Interrupt:17 Base address:0x2000 Memory:c8218000-c8218fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135794 (132.6 KB)  TX bytes:135794 (132.6 KB)



 Anything else i should add? thanks

---

### Post by kokonobs on 2008-08-29
Partition issue is solved now. I accessed the /windows file from ubuntu, then restarted the computer in XP. XP then recognised the partitioning.

---

### Post by WitchCraft on 2008-08-29
> **kokonobs said:**
> Hi everyone,
Hope you can help.
2 days ago i begun my ubuntu journey. I managed to install the latest version, Debian i think its called, with the help of another ubuntu user. After installation network manager does not automatically see wireless networks. My wireless card is Intel Pro Wireless 2200bg on an acer aspire 1690WLMi. I replaced the default ubuntu install drivers(ipw2100) with the new one from intel, ipw2200( there were 3 of them contained in the folder). I always have to turn on the wireless manually (2 presses of the switch) and then enter the password manually each time i reboot. My wireless comes up as eth1 with 'iwconfig' ,  any idea how to fix this? The led doesn't work either.
Second problem is, when i log into windows(XP home), the partitions i created during the installation of ubuntu dont show up, only the only partition shows. This is what i had: XP Operating system on 30GB partition and an empty 30GB partition. This is was i did during the installation: I repartitioned the drive with the XP on it to 20GB, added 4 more partitions, one for ubuntu (6GB) one for /home(15GB), one for /windows(15GB) and a swap one (2GB).
NB: I have been using XP foreva and i'm a complete beginner in Ubuntu so please make instructions as easy as possible.  :)

Thanks in advance

K

First of all: You don't have to create windows partitions. windows cannot read ext2/3 filesystems by default, but you can just use the linux file system by installing an ext2 pluggable/installable filesystem on windows.

Second: after ./configure, make, make install on the the ipw2200 drivers, you need to download the LATEST (3.0) firmware and copy it in the appropriate directory. (hotplug on debian, /lib/firmware/`uname -r`
 on ubuntu)
They definitely work, I've compiled them many times to patch them to get them to work with aircrack.

---

### Post by kokonobs on 2008-08-30
@ WitchCraft
thanks for your response.
When you say ./configure?what do you mean.(i'm a newbie)How do you compile them?
I copied the ipw2200 drivers( the latest 3.0) into lib/firmware. It works only when i manually turn on the wireless device on and re-enter password.

---

### Post by gmxgeek on 2008-08-30
> **kokonobs said:**
> @ WitchCraft
thanks for your response.
When you say ./configure?what do you mean.(i'm a newbie)How do you compile them?
I copied the ipw2200 drivers( the latest 3.0) into lib/firmware. It works only when i manually turn on the wireless device on and re-enter password.

In order to compile something from source, you must launch a terminal, and cd into the directory that includes the source files. Then use the command ./configure to configure the source files to your system. Next type in 'make' to create the customized installation scripts, then 'make install' to install it to your system.

---

### Post by kokonobs on 2008-09-01
Thanks very much guys. I followed the instructions contained in the ipw2200 drivers file. My wireless seems to work now. I'll see how it goes and i'll give an update. Thanks.

---

### Post by kokonobs on 2008-09-01
Wireless works now. I have so far tried my home wireless and girlfriend's.
This is what i did:

From : [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

I downloaded the new firmware and as copied them into /lib/firmware. Ubuntu may have installed ipw2100 drivers as this is what was there before. I deleted those.

I then downloaded the drivers 1.2.0 it was and found the very confusing instructions within the download.

Thanks guys

---

