---
title: "USB is not showing up!"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by zFish on 2013-02-22
Ok my usb jumpdrive is not working at all. It will load for a second and just disappear. I have tried differents terminal commands I have found nothing is getting it to work. I have no idea what I have done. Hope some help is out there to help me out. Thank you for your time.

---

### Post by cariboo on 2013-02-24
Can you paste the output of:

```
dmesg | tail -n15
```

in your next post?

The output of the command, should look similar to this:

```
dmesg | tail -n15
[39355.361674] usbcore: registered new interface driver usb-storage
[39355.361675] USB Mass Storage support registered.
[39356.361841] scsi 4:0:0:0: Direct-Access     SanDisk  Ultra Backup     8.32 PQ: 0 ANSI: 0 CCS
[39356.362319] sd 4:0:0:0: Attached scsi generic sg3 type 0
[39356.363596] sd 4:0:0:0: [sdc] 15745023 512-byte logical blocks: (8.06 GB/7.50 GiB)
[39356.364071] sd 4:0:0:0: [sdc] Write Protect is off
[39356.364074] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[39356.364829] sd 4:0:0:0: [sdc] No Caching mode page present
[39356.364832] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[39356.367071] sd 4:0:0:0: [sdc] No Caching mode page present
[39356.367074] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[39356.370334]  sdc: sdc1
[39356.372587] sd 4:0:0:0: [sdc] No Caching mode page present
[39356.372593] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[39356.372596] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

---

