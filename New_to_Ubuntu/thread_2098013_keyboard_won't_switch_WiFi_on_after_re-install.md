---
title: "keyboard won't switch WiFi on after re-install"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Yoast on 2012-12-25
Hi there,

I have an acer 5742Z laptop on which I have used for two years without serious probblems. I have continously keptthe most recent stable versions. So I was on 12.10 for a while without wireless problems. Until I did a re-install.
It is dual boot with win 7. Under windows I can still use the key-combination of Fn+F3 to switch on wireless. And everything works fine.
Under Ubuntu I have done a re-install after somne problems and everythings sees to be working fine except for the fact that I can no longer use wireless because I can no longer switch on the WiFi NIC. 

The Fn+F3 keys do not work, but the Fn+[other keys] do work. (I can still do Fn+<Up> to increase volume etc.).

My initial impression is that the keyboard just intercepts Fn+F3 and does not allow it to switch Wireless on. 

sudo lshw -C network gives:
  *-network UNCLAIMED
       description: Network controller
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b2400000-b2403fff

Any Ideas? Do I need to install another driver?

---

### Post by Pjotr123 on 2012-12-25
Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Switch-the-wireless-card-on)

---

### Post by Yoast on 2012-12-25
Thanks piotr.

I just tried re-installing again, but this time with WiFi active, rather than just wired LAN active.
Everything is working now. Great.

Thanks for your tips. I may read them.

---

