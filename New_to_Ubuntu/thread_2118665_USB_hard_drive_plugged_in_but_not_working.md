---
title: "USB hard drive plugged in but not working"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by bertmung on 2013-02-21
I installed 12.10 using the windows installer.
My external USB hard drive was working fine until today.

Using 

sudo lshw 

I see my USB printer with information about the model and manufacturer. I don't see anything that looks like the external hard drive. 

I've tried searching on USB external hard drive won't mount and find nothing that seem relevant or usable at my skill level.

---

### Post by tgalati4 on 2013-02-21
While in Ubuntu, open a terminal, plug the drive in, post the output of:

```
dmesg | tail -40
```

Sometimes USB drives get sticky.  Try rapidy rotating with your wrist to loosen the drive platter.

---

### Post by bertmung on 2013-02-21
I should have done a search on my own threads. The answer was in:

[http://ubuntuforums.org/showthread.php?t=1979938&highlight=bertmung](http://ubuntuforums.org/showthread.php?t=1979938&highlight=bertmung)

I unplugged the power. Plugged the power back in. Now everything is copacetic.(That's good.)

Thanks for the help. 

Just in case here's the output from the dmesg

bert@ubuntu:~$ dmesg | tail -40
[  912.178632] usb 2-7: device descriptor read/64, error -62
[  912.458594] usb 2-7: new full-speed USB device number 5 using ohci_hcd
[  912.638561] usb 2-7: device descriptor read/64, error -62
[  912.922509] usb 2-7: device descriptor read/64, error -62
[  913.202481] usb 2-7: new full-speed USB device number 6 using ohci_hcd
[  913.610423] usb 2-7: device not accepting address 6, error -62
[  913.786407] usb 2-7: new full-speed USB device number 7 using ohci_hcd
[  914.194336] usb 2-7: device not accepting address 7, error -62
[  914.194369] hub 2-0:1.0: unable to enumerate USB device on port 7
[ 1634.233084] usb 1-7: new high-speed USB device number 9 using ehci_hcd
[ 1634.370035] usb 1-7: New USB device found, idVendor=1058, idProduct=0901
[ 1634.370048] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1634.370056] usb 1-7: Product: External HDD
[ 1634.370062] usb 1-7: Manufacturer: Western Digital
[ 1634.370068] usb 1-7: SerialNumber: 57442D574D414E4B32343537303333
[ 1634.390961] scsi5 : usb-storage 1-7:1.0
[ 1635.424616] scsi 5:0:0:0: Direct-Access     WD       2500JB External  0107 PQ: 0 ANSI: 0
[ 1635.427470] sd 5:0:0:0: Attached scsi generic sg3 type 0
[ 1635.432770] sd 5:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[ 1635.433883] sd 5:0:0:0: [sdc] Write Protect is off
[ 1635.433889] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 1635.434913] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1635.434919] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1635.438184] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1635.438198] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1635.442836]  sdc: sdc1
[ 1635.446190] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1635.446203] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1635.446210] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 1642.815858] usb 1-7: reset high-speed USB device number 9 using ehci_hcd
[ 1643.749821] REISERFS (device sdc1): found reiserfs format "3.6" with standard journal
[ 1643.749879] REISERFS (device sdc1): using ordered data mode
[ 1643.749883] reiserfs: using flush barriers
[ 1643.757303] REISERFS (device sdc1): journal params: device sdc1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1643.758735] REISERFS (device sdc1): checking transaction log (sdc1)
[ 1643.774924] REISERFS (device sdc1): replayed 2 transactions in 0 seconds
[ 1643.829530] REISERFS (device sdc1): Using r5 hash to sort names
[ 1697.681337] audit_printk_skb: 48 callbacks suppressed
[ 1697.681348] type=1400 audit(1361497860.614:28): apparmor="DENIED" operation="open" parent=2632 profile="/usr/bin/evince-thumbnailer" name=2F6D656469612F626572742F4D7920426F6F6B2F62657274312F446F63756D656E74732F2046616D696C792052656164696E657373 pid=2639 comm="evince-thumbnai" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 1697.697237] type=1400 audit(1361497860.634:29): apparmor="DENIED" operation="open" parent=2632 profile="/usr/bin/evince-thumbnailer" name=2F6D656469612F626572742F4D7920426F6F6B2F62657274312F446F63756D656E74732F2046616D696C792052656164696E657373 pid=2639 comm="evince-thumbnai" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

I'm marking this as solved.

---

