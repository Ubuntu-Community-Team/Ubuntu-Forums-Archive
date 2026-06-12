---
title: "Error when CD inserted"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Lazer08 on 2008-06-14
Hi all, I'm happy to finally be in 8.04 after many attempts! I've got all the functionalities I need for now except one: I get an error when I pop in a disc!

I attached a screenshot of the error. I can browse the contents of this current disc (a 6.06 LTS ISO) and eject it.

Does anyone know why I'm getting this error and/or how can I fix it?

Edit - Here's my fstab:
[http://paste.ubuntu.com/20168/](http://paste.ubuntu.com/20168/)

Thank you all, I really appreciate it :) I hope to have this running expertly in a few weeks!

---

### Post by Yuki_Nagato on 2008-06-14
My first guess is this: is that CD-ROM name accurate?  You said that you can view the files on board the disk, so can you play other disks, perhaps one with images or music?

My theory is, that you are attempting to "play" an .ISO file.  These cannot be "played" in the normal sense of music and images.  They require their own applications.  The money driven world would perfer you to use CD-ROMs and DVDs, but sometimes users (like myself) do not have the hardware to read a DVD.

We turn to such programs as [GMount]("http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/"). These allow us to "play" or "mount" .ISO files as if they were written onto a CD.

In other words, if you want to play the CD-ROM with the .ISO file on it, use GMOUNT.  If you want the CD-ROM to run like it is supposed to, find out how to "burn an .ISO to disk" using one of these GUI frontends:

[CD-Burning Software]("http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html")

---

### Post by cariboo on 2008-06-14
The only thing that really sticks out is the bit where it says upgraded to edgy:

```
dev/hda2 -- converted during upgrade to edgy
UUID=2fc68c03-2a9a-4131-9502-05af5d8beca2 / ext3 defaults,errors=remount-ro 0 1

```

I'm sure it has nothing to do with your problem, but why not delete that bit and see what happens.

Jim

---

