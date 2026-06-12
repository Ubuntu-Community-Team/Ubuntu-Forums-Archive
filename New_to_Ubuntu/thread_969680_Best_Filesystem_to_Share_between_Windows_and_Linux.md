---
title: "Best Filesystem to Share between Windows and Linux"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ps6000 on 2008-11-03
What are your thoughts on the best filesystem to share between Windows and Linux?

I want to put a VM on this partition and have it be accessed between both Operating Systems.

I don't want to put the VM on the native windows drive as I don't want to risk data corruption on windows. I don't mind ntfs though.

I think my choices are ntfs, fat32, ext2/3 with windows driver support.

---

### Post by stephanvaningen on 2008-11-03
You can easilly put everything on an NTFS, Linux will read it easilly using ntfs-3g, you can do it the other-way-around: there is a good tool to read ext2/ext3 from withing windows: a simple google-check will give you a free driver-download (you need to reboot of course;-))

---

### Post by ibutho on 2008-11-03
I would go with ntfs. Most distros released in the last couple of years can read and write to ntfs partitions very well.

---

### Post by ps6000 on 2008-11-03
I have both the ext2/3 tool in windows and the ntfs read write in linux.

Is there a speed difference? Does anyone still use fat32?

---

### Post by ibutho on 2008-11-24
I've never tried the ext2/3 tool in Windows, so I can't comment about it. I've never noticed any speed difference between fat32 and ntfs when accessing them from Linux.

---

### Post by Paqman on 2008-11-24
> **ps6000 said:**
> Does anyone still use fat32?

Some guides on the net still recommend FAT32, since having stable ntfs write support in the default install is relatively new in Linux (as in, within the last couple of years). Other people like it because they don't get caught out by unclean shutdowns of NTFS (especially if they aren't dual-boot)

So yes, there are likely to be some that still use it. Personally I think it's only good for flash drives, myself.

---

