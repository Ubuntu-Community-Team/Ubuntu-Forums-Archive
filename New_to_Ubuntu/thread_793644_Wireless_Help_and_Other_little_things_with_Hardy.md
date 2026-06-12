---
title: "Wireless Help and Other little things with Hardy"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by parnaudo on 2008-05-13
Hello all, eager Ubuntu newbie here running into some wireless and other troubles. I am running a compaq R4000 AMD64 on a dual partition with XP home and I just recently upgraded feisty to hardy. First thing is that when the partition's option comes up at the start, there are now 3 Ubuntu partition options, one for each upgrade since feisty I guess. Any ideas how I can clear this up? 
As for the wireless, I have the BCM4306 and I' ve tried some of the other ideas I've found on this forum. I installed the firmware (fwcutter?) and restarted twice, and it says that its enabled and I even got the little blue light. However, I have no luck getting any networks to come up or connect wirelessly. lshw -C network comes up:
parnaudo@Bigman:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6d:49:1a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.192 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:90:4b:ac:c1:77
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

As for iwconfig:
parnaudo@Bigman:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Anyone have any ideas? I see various posts about putting on a ndiswrapper but since I don't understand yet what that is I figured I'd ask first. Anyone have any ideas? Thanks a bunch!

---

### Post by ZabiGG on 2008-05-14
You are so NOT a newbie, sweetie. Why don't you try the x86-64-bit forum?

You might find better info there.

---

