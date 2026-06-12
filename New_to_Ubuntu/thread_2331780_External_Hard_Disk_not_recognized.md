---
title: "External Hard Disk not recognized"
date: 2016-07-25
forum: New to Ubuntu
---

### Post by aleiex on 2016-07-25
Hello everyone, 

I have a sony external HD (HD-E1), up until yesterday it worked perfectly, but suddenly it stopped being recognized by ubuntu nor windows. I've tried pluging it into different usb ports, and I am able to use other drives, so I've discarded the possibility of a malfunctioning usb port. I looked at previous posts regarding this issue, but I couldn't get past the following:

I tried lsusb, fdisk and and this are the correct outputs**:

> alex@Gurren:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alex@Gurren:~$ 





> alex@Gurren:~$ sudo fdisk -l
[sudo] password for alex: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc197614f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.



> alex@Gurren:~$ dmesg | tail -n 20
[   14.398542] audit_printk_skb: 15 callbacks suppressed
[    14.398545] audit: type=1400 audit(1470841413.334:17): apparmor="STATUS"  operation="profile_replace" profile="unconfined" name="/sbin/dhclient"  pid=939 comm="apparmor_parser"
[   14.398551] audit: type=1400  audit(1470841413.334:18): apparmor="STATUS" operation="profile_replace"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=939  comm="apparmor_parser"
[   14.398555] audit: type=1400  audit(1470841413.334:19): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=939 comm="apparmor_parser"
[   14.398836] audit: type=1400  audit(1470841413.334:20): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session"  pid=938 comm="apparmor_parser"
[   14.398840] audit: type=1400  audit(1470841413.334:21): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="chromium" pid=938 comm="apparmor_parser"
[    14.398871] audit: type=1400 audit(1470841413.334:22): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=939  comm="apparmor_parser"
[   14.398875] audit: type=1400  audit(1470841413.334:23): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=939 comm="apparmor_parser"
[   14.399036] audit: type=1400  audit(1470841413.334:24): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=942  comm="apparmor_parser"
[   14.399040] audit: type=1400  audit(1470841413.334:25): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=942  comm="apparmor_parser"
[   14.399042] audit: type=1400  audit(1470841413.334:26): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="pxgsettings" pid=942 comm="apparmor_parser"
[   16.652020] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   16.652052] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.118982] audit_printk_skb: 123 callbacks suppressed
[    42.118984] audit: type=1400 audit(1470841441.994:68): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="/usr/lib/cups/backend/cups-pdf" pid=2176 comm="apparmor_parser"
[    42.118989] audit: type=1400 audit(1470841441.994:69): apparmor="STATUS"  operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd"  pid=2176 comm="apparmor_parser"
[   42.119279] audit: type=1400  audit(1470841441.994:70): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/sbin/cupsd" pid=2176  comm="apparmor_parser"
[  797.886676] audit: type=1400  audit(1470842198.034:71): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3031  comm="apparmor_parser"
[  797.886681] audit: type=1400  audit(1470842198.034:72): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/sbin/cupsd" pid=3031  comm="apparmor_parser"
[  797.886879] audit: type=1400  audit(1470842198.034:73): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/sbin/cupsd" pid=3031  comm="apparmor_parser"




¿Any suggestions on what could I do?

All help will be greatly appreciated!


Thank you all very, very much in advance!


**[Edit: Posted the outputs for a different disk, corrected with the outputs for the damaged disk]**

---

### Post by Habitual on 2016-07-25
> **aleiex said:**
> 
```
alex@Gurren:~$ dmesg | tail -n 20
[ 1081.004132] hfsplus: write access to a journaled filesystem is not  supported, use the force option at your own risk, mounting read-only.
[ 1081.021604] hfsplus: write access to a journaled filesystem is not  supported, use the force option at your own risk, mounting read-only.
[ 1081.035389] hfsplus: write access to a journaled filesystem is not  supported, use the force option at your own risk, mounting read-only.
[ 1081.051138] hfsplus: write access to a journaled filesystem is not  supported, use the force option at your own risk, mounting read-only.

```

Alex, is that an Apple Product?

Found this: [https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

Sorry, Not much help, otherwise.

---

### Post by aleiex on 2016-08-10
> **Habitual said:**
> Alex, is that an Apple Product?

Found this: [https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

Sorry, Not much help, otherwise.


Oh, my mistake!

I have two sony HD, one is my GF's apple backup, the other one is the damaged one .__.  Sorry about that! 

I'll post the correct output in a second! :D

---

### Post by aleiex on 2016-08-10
These are the correct outputs:

> alex@Gurren:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 045e:07b2 Microsoft Corp. 
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. 
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
alex@Gurren:~$ 





> alex@Gurren:~$ sudo fdisk -l
[sudo] password for alex: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc197614f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.



> alex@Gurren:~$ dmesg | tail -n 20
[   14.398542] audit_printk_skb: 15 callbacks suppressed
[   14.398545] audit: type=1400 audit(1470841413.334:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=939 comm="apparmor_parser"
[   14.398551] audit: type=1400 audit(1470841413.334:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=939 comm="apparmor_parser"
[   14.398555] audit: type=1400 audit(1470841413.334:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=939 comm="apparmor_parser"
[   14.398836] audit: type=1400 audit(1470841413.334:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=938 comm="apparmor_parser"
[   14.398840] audit: type=1400 audit(1470841413.334:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=938 comm="apparmor_parser"
[   14.398871] audit: type=1400 audit(1470841413.334:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=939 comm="apparmor_parser"
[   14.398875] audit: type=1400 audit(1470841413.334:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=939 comm="apparmor_parser"
[   14.399036] audit: type=1400 audit(1470841413.334:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=942 comm="apparmor_parser"
[   14.399040] audit: type=1400 audit(1470841413.334:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=942 comm="apparmor_parser"
[   14.399042] audit: type=1400 audit(1470841413.334:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="pxgsettings" pid=942 comm="apparmor_parser"
[   16.652020] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   16.652052] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.118982] audit_printk_skb: 123 callbacks suppressed
[   42.118984] audit: type=1400 audit(1470841441.994:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2176 comm="apparmor_parser"
[   42.118989] audit: type=1400 audit(1470841441.994:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2176 comm="apparmor_parser"
[   42.119279] audit: type=1400 audit(1470841441.994:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2176 comm="apparmor_parser"
[  797.886676] audit: type=1400 audit(1470842198.034:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3031 comm="apparmor_parser"
[  797.886681] audit: type=1400 audit(1470842198.034:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3031 comm="apparmor_parser"
[  797.886879] audit: type=1400 audit(1470842198.034:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3031 comm="apparmor_parser"




I also tried to see if the USB drive appears in Gparted, but it doesn't :(

---

