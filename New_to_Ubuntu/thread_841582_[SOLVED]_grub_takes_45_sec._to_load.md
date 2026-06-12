---
title: "[SOLVED] grub takes 45 sec. to load"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by jryprt on 2008-06-26
When I start the pc I get the nvidia splash then the dell splash then it takes 45 sec. for grub to show up.
Can this be fixed. It use to show up right after dell splash. I dual boot with xp using ubuntu 7.10.
Thanks

---

### Post by bobnutfield on 2008-06-26
This is a hard drive access issue.  If you have not changed anything (new hardware, etc.) it could be the beginning of difficulties with your drive.  This is an old post, but it is about the same issue and, internestingly, the same pc manufacturer.  I don't know if it is related to your issue, but it is worth a look.

[http://www.linuxquestions.org/questions/linux-newbie-8/bios-to-grublinux-boot-slow-after-disk-transfer-316220]("http://www.linuxquestions.org/questions/linux-newbie-8/bios-to-grublinux-boot-slow-after-disk-transfer-316220")

---

### Post by jryprt on 2008-06-26
> **bobnutfield said:**
> This is a hard drive access issue.  If you have not changed anything (new hardware, etc.) it could be the beginning of difficulties with your drive.  This is an old post, but it is about the same issue and, internestingly, the same pc manufacturer.  I don't know if it is related to your issue, but it is worth a look.

[http://www.linuxquestions.org/questions/linux-newbie-8/bios-to-grublinux-boot-slow-after-disk-transfer-316220]("http://www.linuxquestions.org/questions/linux-newbie-8/bios-to-grublinux-boot-slow-after-disk-transfer-316220")

That link took me the home page not the old post.

---

### Post by bobnutfield on 2008-06-26
[http://www.linuxquestions.org/questions/linux-newbie-8/bios-to-grublinux-boot-slow-after-disk-transfer-316220/]("http://www.linuxquestions.org/questions/linux-newbie-8/bios-to-grublinux-boot-slow-after-disk-transfer-316220/")

Sorry, don't know why it didn't post.

Bob

---

### Post by jryprt on 2008-06-26
I have not touched the hard drive .
This started about a week ago after a update I think ?

---

### Post by bobnutfield on 2008-06-26
As far as I know, an update to the operating system would have nothing to do with post times.  An update to the BIOS might, but it would surely have to be motherboard or hard drive related.  I only experienced it once, and that was installing a new motherboard using the same hard dives.  The POST time was doubled.  Hopefully someone can help pin point this for you.  Sorry I couldn't help more.

Bob

---

### Post by philinux on 2008-06-26
When the bios boots and does it's POST test there's normally one short beep if everything went well.

When your's boots does it beep and then there's the long wait before grub, or is it the other way round.

---

### Post by jryprt on 2008-06-26
> **philinux said:**
> When the bios boots and does it's POST test there's normally one short beep if everything went well.

When your's boots does it beep and then there's the long wait before grub, or is it the other way round.

I have on beep before or after .
I get a black screen with white curser top left corner
after dell splash and before grub.

---

### Post by philinux on 2008-06-26
I'd be tempted to reinstall grub. Either using your live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or supergrub

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by jryprt on 2008-06-26
> **philinux said:**
> I'd be tempted to reinstall grub. Either using your live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or supergrub

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I will try these and get back soon. Thanks

---

### Post by jryprt on 2008-06-26
It was not grub it turn out it was my camera's memory card trying to boot 1st, removed it now all OK .
Thanks for the help

---

