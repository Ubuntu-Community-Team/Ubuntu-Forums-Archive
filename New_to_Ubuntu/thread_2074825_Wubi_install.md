---
title: "Wubi install"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by AndyL1937 on 2012-10-22
HI I installed ubuntu 12.04 using the Windows installer "Wubi". It worked well except it didn't give me an option to install to an .ext3 partition I had set up. Instead it installed to a NTFS partition on on sda2 drive which has windows files on it. questions are:1) Will ubuntu run as fast on the NTFS drive,
2) Will Win7 and ubuntu try to overlay files?
3) If I uninstall ubuntu and reinstall from a DVD install, can I then load it to a .ext file system drive. 
I also have Puppy linux installed on a .ext3 partition so Grub runs twice. So fr I love what I'm seeing with ubuntu, though there are Win7 programs I use that are not available in Linux yet such as Family Tree Maker.
Thanks for any help,
AndyL

---

### Post by mlentink on 2012-10-22
> **AndyL1937 said:**
> HI I installed ubuntu 12.04 using the Windows installer "Wubi". It worked well except it didn't give me an option to install to an .ext3 partition I had set up. Instead it installed to a NTFS partition on on sda2 drive which has windows files on it. questions are:1) Will ubuntu run as fast on the NTFS drive,
That's normal behavior. Wubi installs Ubuntu in a virtual Disk, that is actually a windows file. On modern PC's the performance hit is negligible
> **AndyL1937 said:**
> 2) Will Win7 and ubuntu try to overlay files?
No, as Windows will obviously not overwrite its own files (or will it? Don't use Windows all that often)
> **AndyL1937 said:**
>  3) If I uninstall ubuntu and reinstall from a DVD install, can I then load it to a .ext file system drive. 
Sure you can. just select the 'Do something else' option in the installer when it asks you where and how to install. Obviously do not use the wubi installer, but use the dvd or usb.
> **AndyL1937 said:**
> though there are Win7 programs I use that are not available in Linux yet such as Family Tree Maker. You might want to try out Gramps

---

### Post by AndyL1937 on 2012-10-22
Thanks, guess I can just leave it as it. I'll try Gramps, though Family Tree Maker is tightly integrated with the info on Ancestry.com.
AndyL

---

