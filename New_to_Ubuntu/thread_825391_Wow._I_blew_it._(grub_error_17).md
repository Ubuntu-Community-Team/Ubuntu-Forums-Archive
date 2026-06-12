---
title: "Wow. I blew it. (grub error 17)"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by 2jane on 2008-06-10
Im was dual booting with Vista on a different hard drive.
I reformatted the Linux partition, because with college starting in a few months i wouldnt be using it all too often (SolidWorks and MathCAD dont work well with Linux, i reckon).
WOW, what a mistake.

When I boot, its the GRUB booter and I'm getting error 17.
I wanted to boot into a DOS bootdisk to run the fdisk /mbr whole deal, and its not booting from the DVD (it probably needs a CD).

From what i hear I need to reinstall GRUB to the mbr partition, but i followed the directions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
But on the find /boot/ blahblah step I get Error 15, "Not Found" or something very similar.

And, when I try to reinstall Ubuntu, it doesnt even recognize that my second hard drive has partitions! It lists it all as Unallocated Space. Which seems, uh, pretty bad.
And to top it all off, I dont believe this Laptop came with a reinstall disk, even though I bought it from a large retailer (i might want to rummage through that box again)

Whoa.
What did I get myself into, and how the hell do I get out of it?

---

### Post by wolfen69 on 2008-06-10
check your BIOS to see which drive is booting first. and then change it. this is sometimes the cause.

---

### Post by 2jane on 2008-06-10
> **wolfen69 said:**
> check your BIOS to see which drive is booting first. and then change it. this is sometimes the cause.

It only lists one notebook hard drive... the other being a USB hard drive. I guess it doesn't let the secondary HD hold the boot sector? Its displayed like that as far back as i can remember...

---

### Post by meierfra. on 2008-06-11
You don't need to reinstall Ubuntu.  Click on FixMBR in my signature for lots of ways to restore the MBR.

---

