---
title: "Windows on Ext3?"
date: 2006-09-14
forum: Other OS Talk
---

### Post by napsilan on 2006-09-14
Simple question, probably with a complicated answer.  

Can Windows be installed on an Ext3 filesystem?  I know drivers exist for windows to read/write ext3 ([http://www.fs-driver.org/faq.html)](http://www.fs-driver.org/faq.html)), and I know you can load extra drivers (mainly for SATA/SCSI) during a windows install.  Would it be possible to put the ext2fs.sys and ifsdrives.sys file from the driver package onto a floppy, load them during the windows install, and have it work on an ext3 filesystem?

---

### Post by BoneKracker on 2006-09-14
Why don't you give it a try and let us know.

No, seriously... I very much doubt it.

---

### Post by mvdw on 2006-09-14
I doubt whether this would work. Consider the C:\ drive like your linux root partition. All FS drivers for the root partition need to be built into the kernel, ie not modules. the *.sys files are essentially kernel modules, so windows will likely not be able to boot from an ext3 drive.

This is all speculation on my behalf, but this is how I would imagine it to be.

---

### Post by jdong on 2006-09-14
The answer is simpler than that. No. The current ext3 windows driver does not support storing the same permissions information that fat32 or ntfs is capable of under Windows.

Also, ext3 is actually ext2 under windows right now (the driver does not implement journaling), so I really struggle to comprehend why you'd want to choose that over ntfs or even fat32 for that matter.

Other than that, it should be possible to install windows onto an ntfs drive, then clone that setup over to an ext2, and with a bit of bootloader magic get Windows started. Note that the bootloaders won't understand ext2, so you'll probably need some fat32/ntfs partition to do the first part of booting.

---

