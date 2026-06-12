---
title: "CDROM Drive - Can not mount file."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by d58e7 on 2008-06-01
Not sure when it happened but right now I'm unable to use and CDs, as it seems unable to mount them, however the CD drive is still functional as I have used it fine in Windows. Is there anyway to reset the CD Drive and possibly restore the ability to use CDs again?

---

### Post by msidhard on 2008-06-01
JUST TRY THIS dmesg | grep cdrom IF IT DISPLAYS ANY RESULT THEN DO sudo mount /dev/cdrom /media/cdrom

---

### Post by d58e7 on 2008-06-01
> **msidhard said:**
> JUST TRY THIS dmesg | grep cdrom IF IT DISPLAYS ANY RESULT THEN DO sudo mount /dev/cdrom /media/cdrom

I tried dmesg | grep cdrom and nothing appeared.

Now I don't know if this effects anything on the cdrom but I followed this guide to install OSSv4 [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

---

### Post by d58e7 on 2008-06-01
Now it gave me a little bit more information.

```
mount:block device /dev/scd0 is write-protected,mounting
read-only mount: wrong fs type, bad option, bad superblock
on /dev/scd0,      missing codepage or helper program, or
other error  In some cases useful info is found in syslog
-try        dmesg|tail
```

Then I tried dmesg|tail and got

```
Linux-PC:~$ dmesg|tail
[ 6345.431316] Buffer I/O error on device sr0, logical block 22
[ 6345.812494] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6345.812501] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6345.812508] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 6345.812516] end_request: I/O error, dev sr0, sector 1248
[ 6345.921916] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6345.921921] sr 3:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6345.921928] sr 3:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 6345.921932] end_request: I/O error, dev sr0, sector 88
[ 6345.922009] UDF-fs: No partition found (2)
```

I've tried several different Data disks including the Ubuntu installation disk and all seem to have the same error.

---

