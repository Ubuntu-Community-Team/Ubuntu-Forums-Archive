---
title: "Grub error 15 when reinstall...?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by hopelessone on 2008-05-04
Hi,

I split the HDD in 2 1st half i formatted to ext3 second NTFS

I went to install Windowz and get grub error 15....BIOS is set to boot CD forst....UBUNTU boots from CD no prob....

what can i do?

thanks..

---

### Post by svk on 2008-05-04
Grub stores its configuration file in /boot/grub/menu.lst.  By formatting the partition, you deleted the file and Grub no longer knows what to do.

That's probably what happened, but I'm not really sure how one would go about solving it.

---

### Post by hopelessone on 2008-05-05
delete the ext3 and leave the other...solved

---

