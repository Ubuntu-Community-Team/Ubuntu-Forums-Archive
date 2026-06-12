---
title: "IDE drive shows up as sda"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by P86 on 2008-11-07
Why is my IDE drive showing up as dev/sda? Isn't sda for scsi and sata drives? As it is, I can't seem to enable DMA. This is probably any easy answer, but I appreciate the help!

---

### Post by gpsmikey on 2008-11-07
I had the same question a while back.  Turns out that as of a release or so back, all the drives are now sdx and the hdx designation is no longer used.  Not all documentation has been updated to reflect that though.  Here was my thread on that:
[http://ubuntuforums.org/showthread.php?t=913247](http://ubuntuforums.org/showthread.php?t=913247)

mikey

---

### Post by bsharp on 2008-11-07
Gpsmikey is right. As for the DMA, is it enabled in your BIOS?

---

### Post by P86 on 2008-11-08
> **bsharp said:**
> Gpsmikey is right. As for the DMA, is it enabled in your BIOS?

When the system goes through the POST the drive shows up as UDMA2, so I assume so. I will check.

If it is enabled in the BIOS, will the driver enable it?

Also, can you still set drive standby times with hdparm now that they have switched to the sda driver?

---

### Post by mapes12 on 2008-11-08
Main thing to look at is the last letter. sda with "a" Indicating first drive device. "b" would be second HDD and so on. sda is now the only configuration regardless of IDE or SCSI.

---

