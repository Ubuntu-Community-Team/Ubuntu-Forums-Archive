---
title: "ubuntu hard drive, placed in ext case and then accessed from windows"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by cichlet on 2012-01-15
I had a server for storage that used ubuntu. Can I place the hard drives in an usb external case and plug it into a windows 7 computer and access the files.

---

### Post by carl4926 on 2012-01-15
[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

---

### Post by Double.J on 2012-01-15
Hi there, and welcome to the forums!

Unfortunately windows can't read/write EXT4, so that's a no go,

But unlike windows, Ubuntu will boot over USB, so you can boot up Ubuntu from USB hdd by selecting it at boot and copying the files from inside Ubuntu to Windows... or you could do this with a live CD/USB is for some reason your Ubuntu on the external wouldn't boot?

Hope it helps!

---

### Post by Sigma1 on 2012-01-15
No, not unless the ubuntu hard drive was formatted in FAT or NTFS. However, you might be able to boot from a LiveCD (ubuntu or another linux), and access your ubuntu hard drive that way. Then you could copy whatever you're interested in, into C:\Documents and Settings\User etc. in Windows.

I see I was too slow on the typing... But the replies tally, in any case!

---

### Post by halitech on 2012-01-15
> **gnu/mirow said:**
> 

Unfortunately windows can't read/write EXT4, so that's a no go,



I'm not using EXT4 on any of my systems but I do believe  you are partially incorrect in saying Windows can't read or write EXT4. Natively it can't but as the link carl points to says

> The ext4 or fourth extended filesystem is a journaling file system for Linux, developed as the successor to ext3.

It was born as a series of backward compatible extensions to remove 64-bit storage limits and add other performance improvements to ext3.However, other Linux kernel developers opposed accepting extensions to ext3 for stability reasons and proposed to fork the source code of ext3, rename it as ext4, and do all the development there, without affecting the current ext3 users

Ext2Read is an explorer like utility to explore ext2/ext3/ext4 files. It now supports LVM2 and EXT4 extents. It can be used to view and copy files and folders. It can recursively copy entire folders. It can also be used to view and copy disk and file

now, how reliable it is, I'm not going to say but I know it works great for EXT3

---

### Post by anewguy on 2012-01-16
I'm not sure if the drives would boot as-is.  Since they were in a server, and now in a USB enclosure, I would suspect that the grub entries may not be correct now.  If you want to actually boot ubuntu from those drives, I think I would use a LiveCD and run update-grub but making sure the destination is the USB drive, not your Windows drive.

dave ;)

---

