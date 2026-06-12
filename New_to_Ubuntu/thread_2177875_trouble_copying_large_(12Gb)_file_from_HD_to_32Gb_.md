---
title: "trouble copying large (12Gb) file from HD to 32Gb flash drive"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by Old Jimma on 2013-09-30
Hi Community:

I've had difficulty copying a large (12Gb) file from my HD to a 32 flash drive.

 I get the error message: "Error splicing file: too large."

I don't understand this!

How do I copy that large file to my 32Gb flash drive?

Thanks!
Old Jimma from the Old Country

---

### Post by tophatandy on 2013-09-30
if your flash drive is formatted as fat it won't allow files over roughly 4.2 Gigs. If this is the case, just re-format it as ext4 or something other than fat.

---

### Post by Francisco Cardoso on 2013-09-30
Maybe you have it formatted as FAT32. If so, the maximum file size supported is 4.s GB.

---

### Post by Old Jimma on 2013-10-01
Thanks! I reformated it as ext4... and the large files transfered.

However, I'm not sure how to share the reformated drive with Windows and Mac users.

:(

Thanks for your replies!
Old Jimma

---

### Post by oldfred on 2013-10-01
Then you maybe should have used NTFS, but not sure what Macs support.

---

### Post by cool110 on 2013-10-01
NTFS will be read-only on Macs. HFS+ is writeable by Macs but won't work at all on Windows.

---

### Post by dannyboy79 on 2013-10-01
there was a driver for windows that could read ext3 partitions, not sure about ext4. if not, you'll have to format the usb stick to ntfs IF you want to share with linux, mac, and windows.

---

### Post by sandyd on 2013-10-01
> **cool110 said:**
> NTFS will be read-only on Macs. HFS+ is writeable by Macs but won't work at all on Windows.

it does if you install additional software like paragon or [http://osxfuse.github.io/](http://osxfuse.github.io/)

---

### Post by Impavidus on 2013-10-02
Alternatively, split the file into smaller pieces.

---

### Post by varunendra on 2013-10-02
> **dannyboy79 said:**
> there was a driver for windows that could read ext3 partitions, not sure about ext4.

Perhaps you mean "[Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/")". I've been using it and can confirm that it does read (can even write to) EXT4 partitions as well. As per a review on the linked page, it work with Win8 too.

But if the drive is to be used on Macs too, then unless installing utilities on all the target computers is an available option, I think OP must compromise with NTFS.

---

### Post by Morbius1 on 2013-10-02
One of the strange ironies about OSX is that it does allow write access to NTFS partitions natively - it's just implemented in a very strange way:
[https://discussions.apple.com/message/20943723#20943723](https://discussions.apple.com/message/20943723#20943723)

---

### Post by mc4man on 2013-10-02
You could also us exfat which is designed for flash drives,  has no file size limit that you'll ever reach & works in Windows & Osx (recent versions
Support for read, write & formatting a drive is available in 13.04/13.10 or [thru a ppa for earlier Ubuntu releases]("https://launchpad.net/~relan/+archive/exfat")
(packages in 13.04/13.10 are - 
exfat-fuse
exfat-utils

formatting a drive to exfat in Ubuntu is quite easy, & 13.04/13.10 need no help mounting, eariler may need to be manually done. 
No sense going further if not interested, otherwise this page gives basics
[http://www.unixmen.com/how-to-format-usb-to-exfat-in-linux/](http://www.unixmen.com/how-to-format-usb-to-exfat-in-linux/)

Note that 13.04/13.10 don't need the ppa nor any 'help' mounting, exfat drives are recognized & mounted like any other supported Fs

---

### Post by kurt18947 on 2013-10-02
There are other options for reading (only) ext4 in Windows.  Here are some, including Ext2Fsd referred to by Varundera.

[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

### Post by CyberLazi on 2013-10-02
Just format it as NTFS. It doesn't matter if it's ready-only on Mac. What matter is you'll be able to copy the file from your flash drive to other OSes (including Mac).
Unless you're planning to modify something on that 12Gb file from your flash drive.

With NTFS, you don't need to install additional software on your windows OS to copy the file from your flash drive.
I'm not sure though if Windows XP with FAT32 is able to read NTFS formatted flash drive or not.

---

