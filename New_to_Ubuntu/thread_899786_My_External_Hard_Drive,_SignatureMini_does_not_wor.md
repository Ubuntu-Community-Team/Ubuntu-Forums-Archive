---
title: "My External Hard Drive, SignatureMini does not work correctly in Ubuntu Linux!"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by karlo on 2008-08-24
I am using Ubuntu Linux partially upgraded Hardy Heron.

I can't use my newly purchased SignatureMini external drive.

When I insert it into the USB, Ubuntu does not detect it. I tried including the drive in the fstab file and still it doesn't work. I need to run nautilus as rrot, then mount the drive there. Now it works. Weird though. When I unmount it, it doesn't disappear! Thus it keeps the hard drive running.. here's the specs [http://www.simpletech.com/parts/fsu25160bb.htm](http://www.simpletech.com/parts/fsu25160bb.htm)

By the way according to the manual ...

SimpleTech recommends that you stop your drive from running before unplugging it from your computer, to
prevent possible damage to your USB port.
      Before disconnecting your drive, close any open
      files and exit any applications running on the drive.

Well, when I unmount it, the drive still runs! It should be turned off even if i don't remove it from the usb right?

i really need to backup my files, reformat my laptop then install a very clean installation of ubuntu hardy heron and windows xp!

[http://www.simpletech.com/support/guides/user-guides/60000-00168-001.pdf](http://www.simpletech.com/support/guides/user-guides/60000-00168-001.pdf)

---

### Post by zamadatix on 2008-08-24
have you tried reformatting as fat32? i had to do that once

---

### Post by karlo on 2008-08-25
> **zamadatix said:**
> have you tried reformatting as fat32? i had to do that once
it's default format is NTFS already. And if you read the manual I included, it includes some famous backup helper applications for windows and macintosh. I don't know if I format my external hard drive, I don't know If I can still restore it, the softwares(backup softwwares).

---

### Post by kirenpillay on 2008-09-13
I'm having the same problem. Doesn't show up with dmesg.

I thought this had to do with my PC, but it also happens on my laptop, running Hardy Heron.

---

