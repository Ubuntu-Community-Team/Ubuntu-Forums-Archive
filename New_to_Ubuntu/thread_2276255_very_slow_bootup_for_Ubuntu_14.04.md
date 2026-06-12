---
title: "very slow bootup for Ubuntu 14.04"
date: 2015-05-01
forum: New to Ubuntu
---

### Post by Victor_Gilbert on 2015-05-01
I have an Acer Extensa E series,  AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ × 2, 43.6 GB disk, 2.7GiB ram. Yesterday I removed dual booted Lubuntu & Ubuntu 14.04 and installed a stand alone Ubuntu 14.04.

Today I ran Bootrepair and was told to post this......** [http://paste.ubuntu.com/10960248/](http://paste.ubuntu.com/10960248/)** 

Appreciate help

vicsat

---

### Post by TheFu on 2015-05-01
I don't have an Acer laptop, but for my netbook, the really slow boot (3+min) was due to a TPM module. My netbook and non-high-end laptops generally don't include a TPM chip.  Disabled that with grub and boots are 2 sec.
File /etc/grub.d/10_linux, line 19:
```
GRUB_CMDLINE_LINUX_DEFAULT="tpm_tis.force=1"
```

Don't know if this is the same issue you are having - just thought it would be worth you researching to see if others with the same laptop model have disabled it and gotten faster boots.  10% chance this will help.

TPM - [https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) for an explanation.

Anyway - good luck.
Would be good to look at the **boot.log** to see what is taking lots of time.

---

### Post by oldfred on 2015-05-01
Another possibility.
Grub seems to scan every drive even when booting just from one.
And if a drive has issues like needing fsck or chkdsk it can take time to read & fail to read the drive.

So what is a 2TB drive with FAT16 doing? That is highly unusual. Or does that drive have issues?
We do not suggest FAT32 for larger partitions as it does not have a journal and cannot store files over 4GB. I assume FAT16 is even worse.

---

### Post by TheFu on 2015-05-01
@oldfred - Looks to me like that is a 2GB Kingston flash drive - FAT16 isn't an issue. I even put on my reading glasses to double check it. ;)

The unfound storage devices are probably a USB multi-card reader. Might be worth unplugging that to see if it helps with boot speed. I love those things!

---

### Post by oldfred on 2015-05-01
@TheFu
You are right and FAT is ok for a flash drive. I missed the MB and was thinking GB or a very large drive. I do have my glasses on, but does not always seem to help. :)
Good suggestion on unplugging things just to see if it makes a difference.

---

### Post by Victor_Gilbert on 2015-05-01
Thanks TheFu & oldfred.

Removed 274 GB external hard drive - seems quicker.

vicsat
PS How can I show this as CLOSED ?

---

### Post by oldfred on 2015-05-01
I might run fsck if ext3 or ext4 formatted or chkdsk if NTFS or FAT formatted on external drive then.

See note at bottom of my signature.

---

