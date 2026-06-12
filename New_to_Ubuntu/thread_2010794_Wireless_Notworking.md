---
title: "Wireless Notworking"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by CallFaheem2 on 2012-06-26
Dear All,
using Linux after a very long time have forgotten almost every thing, I need a little help.
I have newly install Ubuntu in my desktop, problem is with the wireless connectivity. I am using TP-link wireless adapter.During installation it detects all the connections (wireless) but when password was given it failed to accept. However when connected to LAN it worked.

Could some one please assist me in this issue. 

Thanks and Regards.

---

### Post by spikoley on 2012-06-26
Try turning off all the security on the wireless router then connecting.  If you connect then turn it back on and try connecting again.

---

### Post by kurt18947 on 2012-06-26
TP-Link makes a few different adapters.  If PCI(internal card), could you open a terminal, type into it "lspci" and post the output?  If USB, post the output of "lsusb"?  We're looking for a line that says something like 'network controller' and might mention something like Atheros or Broadcom.  Something like this:

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**
Bus 002 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 002: ID 047d:2048 Kensington 
Bus 002 Device 003: ID 04f9:01f3 Brother Industries, Ltd 
```

---

### Post by wildmanne39 on 2012-06-26
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

