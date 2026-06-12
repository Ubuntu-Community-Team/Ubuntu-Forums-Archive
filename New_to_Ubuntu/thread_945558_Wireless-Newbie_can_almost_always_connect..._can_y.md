---
title: "Wireless-Newbie can *almost* always connect... can you help figure out why?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by suzanneforums on 2008-10-12
Hi.  I'm new at this, but I'm trying to learn.  Thanks for your help.  I looked in the forums for an answer to my problem but didn't find one. 

I have a Dell Inspiron 1420, one of their out-of-the-box Ubuntu setups.  Wireless usually works fine at cafes and stuff.  At home, my neighbor shares her WEP password-protected network with me, and that's where I run into problems--sometimes I can connect just fine.  Other times the computer detects her network as available and shows 40% or 50% connection, asks for her password, and then seems to time out before it can connect.  What's the deal?  Is it just that her router is too far and the connection's not strong enough?  Why would it work only 70% of the time?

It's a minor annoyance and I've been just putting up with it, but it's time to get this problem solved and learn something new!  Can anyone shed some light on this?  Thank you! 
 
Don't know if this is relevant in this case, but here's the output of lshw -C network:

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:92:c9:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp firmware=14.2 1:0 () ip=192.168.1.110 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:fe:2f:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes

---

### Post by roger_1960 on 2008-10-12
If you can it would seem sensible to go and sit next to her router with your laptop and see if it works there.  If it does, then its probably a signal strenth problem at your house.  In my experience, anything less than about 60% is pretty unreliable.

---

### Post by suzanneforums on 2008-10-12
Hmm, good suggestion.  
She's not home right now, but I'll try that when she returns.  Thanks!

---

