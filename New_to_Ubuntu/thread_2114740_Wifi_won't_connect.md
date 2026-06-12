---
title: "Wifi won't connect"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by Football098 on 2013-02-10
Hi everyone,

So I'm new to the Linux game and have been playing around with the Ubuntu 12.10 Live CD.  I've been really impressed with what I've seen and have been testing the stuff on the Live CD before I decide to install the real deal.  Everything seems to be looking good except I can't get my computer to connect to my wifi router.  It has no issues when connecting via a direct ethernet connection, but wifi is a no go.  When I try to connect via wifi, the OS looks like it is trying to connect, but never completes the connection.  Every 30 seconds or so, the connection dialog box will pop up asking me to connect (it already has my password pre-populated along with the network SSID).  I can see my connection and my neighbors as well, so I know that my adapter is at least half working in Ubuntu.  Any ideas how to fix this so my computer will complete the connection with my wifi router?

My machine is a Toshiba Satellite L655 with an Intel Wifi Link 1000 BGN as the adapter.

Many thanks in advance!

---

### Post by wingnut2626 on 2013-02-10
I remember having the same problem for a friend of mine, and i used the module iwlwifi to solve it.  Do a search on iwlwifi on these forums, and that will give you some groundwork to get this thing up and running.

---

### Post by wildmanne39 on 2013-02-10
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```

lspci -nnk | grep -iA2 net
```
this will let us see what wireless device you have so we will know if it will work when ubuntu is installed, but in my opinion it is not worth the trouble to try to get it to work from a livecd.
Thanks

---

### Post by Football098 on 2013-02-10
> **Wild Man said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```

lspci -nnk | grep -iA2 net
```this will let us see what wireless device you have so we will know if it will work when ubuntu is installed, but in my opinion it is not worth the trouble to try to get it to work from a livecd.
Thanks


Thanks for the quick replies!  Here is what the terminal displayed:

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fd50]
    Kernel driver in use: atl1c

---

### Post by wildmanne39 on 2013-02-10
Hi, your wifi should work fine once you have ubuntu installed. It might take a little tweaking but nothing that can not be done pretty easily, just start a new thread in the networking section when you have ubuntu installed if it does not connect automatically.
Thanks

---

### Post by Football098 on 2013-02-10
Thanks!  I appreciate the help!  I'll give the thread an update once I get the OS installed.  May take a while though with work, etc haha.

Thanks again!

---

### Post by wildmanne39 on 2013-02-10
Your welcome! take you time.

---

### Post by buzz999 on 2013-07-13
I'm having about the exact same issue, except I just did a full Ubuntu installation.  I can see the wifi, it looks like it connected briefly during installation, but I can't get it to connect now.  Wifi for all other home devices working fine.  Network specs are below.  Should there be any issues with Ubuntu?  

Thank you in advance for your help.  (As an aside, using Ubuntu to try to get a crappy little HP Mini netbook working better.  Was unusable with Windows 7...dragging, hanging, lagging...ready to toss this netbook.  So far it *flies* with Ubuntu, very happy, but HAVE to get the wifi working!)


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 04)
    Subsystem: Hewlett-Packard Company Device [103c:148a]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl

---

### Post by wildmanne39 on 2013-07-13
You should be able to get that card working, please start a new thread since your device is different from the OP's.
Thanks

---

### Post by buzz999 on 2013-07-13
Thank you for the quick reply Wild Man...will do!

---

