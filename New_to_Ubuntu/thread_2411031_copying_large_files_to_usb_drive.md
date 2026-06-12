---
title: "copying large files to usb drive"
date: 2019-01-23
forum: New to Ubuntu
---

### Post by meburd on 2019-01-23
I am trying to copy some iso files to my usb drive and it copies sometimes half way or almost done and comes up with an error that file is too large.  These files are 5.1gb and 4.3gb respectively.
I am also trying to save my ubuntu18.04.1 iso which is only 2gb and it hangs after copying and never gives me a check mark for completion. I would think file size wouldn't really matter just doing a copy. Please help.

---

### Post by howefield on 2019-01-23
What is the file system of the USB drive ?

If it is formatted as FAT32 you will hit a maximum file size of 4GB.

---

### Post by davidvinh on 2019-01-23
I have the same problem

---

### Post by Impavidus on 2019-01-24
Most smaller usb drives are sold formatted with the FAT32 file system. This has the advantage of being supported on pretty much every OS in existence, but has a file size limit of 4GB. Your options are to format the drive to some other file system or to break the files into smaller chunks.

---

### Post by oldrocker99 on 2019-01-24
I only use FAT16 for live USBs. For any other use, I always use ext4.

---

