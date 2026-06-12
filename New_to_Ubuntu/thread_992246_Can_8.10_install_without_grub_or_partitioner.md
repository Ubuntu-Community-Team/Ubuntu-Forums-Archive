---
title: "Can 8.10 install without grub or partitioner?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Lostin60's on 2008-11-24
If it's even possible, how does one install 8.1 without grub or partitioner?

---

### Post by ubername on 2008-11-24
[QUOTE=Lostin60's;6244072]If it's even possible, how does one install 8.1 without grub or partitioner?[/QUOTE

Why would you want to do this?

---

### Post by Lostin60's on 2008-11-24
I already have boot magic and partition magic installed, also on install Ubuntu keep telling me no root file system is selected, even though I formated the partition I want to install to. Maybe I am missing something, as I am a super-noob to Ubuntu.

---

### Post by handydan918 on 2008-11-24
> **Lostin60's said:**
> I already have boot magic and partition magic installed, also on install Ubuntu keep telling me no root file system is selected, even though I formated the partition I want to install to. Maybe I am missing something, as I am a super-noob to Ubuntu.

First foray into the world of Linux?

Listen, the partitioning program and the boot program will complicate things considerably, as well as necessitating support from outside these forums (fora?) if you get into trouble. 

The "no root file system is selected" thing is probably just a less than intuitive part of the installer that wants you to specify where / (root) is going to be living. It is a separate issue from formatting. 
Speaking of which, use ext3. 

I'd recommend setting up a dual-boot with windows on the first partition of the first harddrive, and Linux on the second, third and fourth. 

second = /  (=>10GB)

third = swap (varies greatly-default to 1GB)

fourth = /home (however much space you can spare)




HTH!

---

### Post by bapoumba on 2008-11-24
Main thread title changed as requested.

---

### Post by Lostin60's on 2008-11-24
> **handydan918 said:**
> First foray into the world of Linux?

Listen, the partitioning program and the boot program will complicate things considerably, as well as necessitating support from outside these forums (fora?) if you get into trouble. 

The "no root file system is selected" thing is probably just a less than intuitive part of the installer that wants you to specify where / (root) is going to be living. It is a separate issue from formatting. 
Speaking of which, use ext3. 

I'd recommend setting up a dual-boot with windows on the first partition of the first harddrive, and Linux on the second, third and fourth. 

second = /  (=>10GB)

third = swap (varies greatly-default to 1GB)

fourth = /home (however much space you can spare)




HTH!
Indeed, my first foray. I am not sure of the reasons that my boot and partition will cause probs. But I will simply take your word for now, and bombard you with questions later..lol. I will remove my boot and part. software, and install according to your suggestions. Too bad I can't broadcast my attempts, every one deserves a good giggle now and then..heheh. I appreciate every ones advice, even the advice I don't understand.

---

### Post by go_beep_yourself on 2008-11-24
You could always install Ubuntu in a VMWare product such as VMware Workstation without changing your current partition layout and bootloader. Other options would be installing it to a usb disk etc.

---

### Post by Lostin60's on 2008-11-26
Well, I am up and running. Kinda..sorta. I am trying to get my internet up now. I have ndiswrapper and ndisgtk working. I found the .inf file for my Broadcom. My realtek seems to have a .sys file but no .inf file. I am attaching a screen shot from my terminal. I had 2 but one won't open. There is a good bit of info on this one though. Do I need a network interface adapter? If so do I use the >inf file from it's driver? Some of this is a bit difficult because when the manual says "go here" here is somewhere else. Sys>admin>network turns out to be sys>admin>network tools. Or is it network manager? Whichever, it is not what the manual says. But I am working around that. Again, any help will be humbly appreciated. Well the attachment didn't work out as expected. I'll work on that.

---

### Post by Lostin60's on 2008-11-26
> **handydan918 said:**
> First foray into the world of Linux?

Listen, the partitioning program and the boot program will complicate things considerably, as well as necessitating support from outside these forums (fora?) if you get into trouble. 

The "no root file system is selected" thing is probably just a less than intuitive part of the installer that wants you to specify where / (root) is going to be living. It is a separate issue from formatting. 
Speaking of which, use ext3. 

I'd recommend setting up a dual-boot with windows on the first partition of the first harddrive, and Linux on the second, third and fourth. 

second = /  (=>10GB)

third = swap (varies greatly-default to 1GB)

fourth = /home (however much space you can spare)




HTH!


I am still working on this prob. Here is some info.

daniel@daniel:~$ sudo lshw -c network
[sudo] password for daniel: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ae:dd:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:14:76:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:4c:3b:0e:5c:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



daniel@daniel:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ae:dd:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

daniel@daniel:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

I can only find a .sys file for realtek, but no inf. I also wonder if I need the net adapters. I know I am close to having this fixed. Some of the prob is the manual points me to places in the sys>admin that are not there for instance, the manual say either "sys>admin>network" or else "sys>admin>networkmanager" I forget which. But what is actually there is "sys>admin>network tools" I plan to make extensive use of ubuntu,learn some code and some scripting, an just get move savvy in general. I will not be asking much in here, unless I just can't find an answer by research. I am just trying to get online quickly so I dont have to keep switching to XP to reasearch. As always, I am grateful for any and all advice.

---

