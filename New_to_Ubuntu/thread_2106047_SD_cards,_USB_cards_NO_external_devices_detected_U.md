---
title: "SD cards, USB cards NO external devices detected UBUNTU 12.10"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by alibak on 2013-01-17
alright,...

searched everywhere..  got a new toshiba 64-bit system chip 7 intel.

installed latest ubuntu 12.10 

NO SD card NO USB port is detected!!! 

searched all day for an answer..
NO results
DON'T KNOW linux... 

NEED a recipe please.. I'm able to go to terminal and copy and paste commands... that's all.

I really hope someone can help me as this is very frustrating.

Thank you.

Ali

---

### Post by cariboo on 2013-01-18
Open a terminal nad type:

```
lsusb
```

the output should look similar to this:

```
lsusb
Bus 001 Device 006: ID 0bb4:0c87 HTC (High Tech Computer Corp.) Desire (debug)
Bus 002 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

In the listing above, you can see my smart phone, keyboard and mouse are connected.

To check if your sd card is detected, open a terminal and type:

```
dmesg | tail -n15
```

you should see something similar to this:

```
dmesg | tail -n15
[51875.510628] usb 1-7: SerialNumber: SH0CPR802330
[51875.512771] scsi5 : usb-storage 1-7:1.0
[51876.512582] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[51876.513123] sd 5:0:0:0: Attached scsi generic sg3 type 0
[51876.518579] sd 5:0:0:0: [sdc] 15544320 512-byte logical blocks: (7.95 GB/7.41 GiB)
[51876.520571] sd 5:0:0:0: [sdc] Write Protect is off
[51876.520577] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[51876.522577] sd 5:0:0:0: [sdc] No Caching mode page present
[51876.522583] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[51876.531561] sd 5:0:0:0: [sdc] No Caching mode page present
[51876.531567] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[51876.668462]  sdc: **sdc1**
[51876.680443] sd 5:0:0:0: [sdc] No Caching mode page present
[51876.680448] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[51876.680452] sd 5:0:0:0: [sdc] Attached SCSI removable disk
```

In the above output, you can see that the 8GiB sd card in my smart phone is detected, and given the device label of /dev/sdc1

---

