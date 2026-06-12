---
title: "[SOLVED] lost boot"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by AlanInVancouverBC on 2008-07-07
I dual-boot.
This morning I couldn't get past this line in the boot operation:
"ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!"
It actually stops a few lines later with this:
"[18.030690] usb1-2: configuartion #1 chosen from 1 choice"
but I don't think that means anything.

That's when I did the recovery-mode process.

In the normal boot option, I get to: (initramfs) _

I'm guessing this is a consequence of defragging in XP.

---

### Post by Yuki_Nagato on 2008-07-07
Are you trying to boot into Windows or Ubuntu?  Does GRUB still exist?

---

### Post by AlanInVancouverBC on 2008-07-08
ubuntu/disks/boot/grub exists, with these files:
menu.lst
menu.lst~
default
menu.lst.backup
device.map

files, and a splashimages folder.

---

### Post by AlanInVancouverBC on 2008-07-08
And, I'm trying to boot into ubuntu.

---

### Post by AlanInVancouverBC on 2008-08-01
I solved it by re-installing OS

---

