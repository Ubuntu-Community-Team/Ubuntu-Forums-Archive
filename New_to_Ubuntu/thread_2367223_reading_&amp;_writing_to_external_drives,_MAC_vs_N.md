---
title: "reading &amp; writing to external drives, MAC vs NTFS"
date: 2017-07-27
forum: New to Ubuntu
---

### Post by wfriedwaldgmail.c on 2017-07-27
I am trying to copy some files (2TB worth, actually) from one hard drive to another using Ubuntu.  both are in the Mac format.  (Yes, I have a reason for wanting to use the Ubuntu machine rather than my mac.)

I currently have two external drives attached the Ubuntu system. One is in the Mac format, the other is NTFS.

I see that I read both on Ubuntu (yay!), but I can only copy to the NTFS drive.

is there anything that I can do that will allow me to copy to the Mac drive?  Some kind of SUDO magic or something?

thanks for any feedback!

w

---

### Post by Futant on 2017-07-27
I've never tried it but maybe [this]("https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os#332317") could help you?

---

### Post by wfriedwaldgmail.c on 2017-07-27
thanks !  it did something.  but I still can't copy to the drive ... not sure why, possibly an HFS Mac permissions issue of some kind.

w

---

### Post by yancek on 2017-07-27
The software to read/write to Mac filesystems is not installed by default on most Linux distribution so you would need to install that.  The link below provides information and explains how to install.

[https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

### Post by Futant on 2017-07-28
Yancek that is the exact link that I already posted. Can't help you any further W., but maybe you'll find someone in the Apple hardware users section...

---

### Post by johndough2 on 2017-07-28
Hi

If you installed the hfs files, perhaps re-formatting the drive and re-mounting will clear any flags that may be preventing full use.

---

