---
title: "How do I install boot-repair from boot-repair CD"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by william67 on 2015-03-24
New install does not boot.  Black screen blinking cursor.

Acer Aspire 5750Z had Win7 64 bit on it.  Installed 14.04.2 on it.  Runs OK from USB.

Downloaded Boot-repair iso from Sourceforge and burned it to CD.

This Noob doesn't know how to install Boot-repair from CD.

Help is appreciated,
Thanks,
Wm

---

### Post by Vladlenin5000 on 2015-03-24
Hello and welcome.

As far as I know, boot-repair is to be used, not installed, from the bootable CD. There's no point in installing something you'll *hopefully* use only once.
Regardless of its use *per se *there are better people than me here that can help. I've never used it - never needed - but it looks like something quite intuitive, like "click here and let me work"...

---

### Post by yancek on 2015-03-24
You would generally burn it to a CD as an image similar to the way you would put Ubuntu or any other system on a CD/DVD to make it bootable, then boot the machine with the boot repair CD in the drive with the CD set to first boot priority.  If you look at the boot repair page, there is also a method to install it and use it that way.  Seems like it would be better to just make a bootable repair CD. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by william67 on 2015-03-24
Have tried to run it from CD, not happening.  Ubuntu computer is not connected to internet so can't install others from Apps space, etc.

---

### Post by Vladlenin5000 on 2015-03-24
How exactly have you burned that CD?

Because... > You would generally burn it to a CD _as an image_ similar to the way you  would put Ubuntu or any other system on a CD/DVD to make it bootable
If you burned the ISO file as is, you did it wrong.

---

### Post by william67 on 2015-03-24
iso image created CD

---

### Post by Vladlenin5000 on 2015-03-24
> **william67 said:**
> iso image created CD

I don't understand what you mean here and I suppose you don't either...

What are the contents of the burned CD? A single ISO file or several files/folders?

---

### Post by Geoffrey_Arndt on 2015-03-24
The CD/DVD burning tool (Nero, K3B, Brasero or similar) will do many types of "burns" (data, copy, etc).    Assuming you burned the downloaded iso file as an "image" (not just copied the iso) . . . (image being the key word), then the only other step is to ensure your PC has it's BIOS or UEFI firmware setup to boot from CD/DVD or USB-Flash ahead of anything else like the hdd, ssd, or even other types of removable media.    Then the CD will actually load-up and provide the "live OS" with the Boot Repair Tool already installed (so just click on it).

By the way . . . we are not talking about the Live Ubuntu CD . . . . we are talking about a different disk image CD altogether from:  [http://sourceforge.net/projects/boot-repair-cd/?source=directory](http://sourceforge.net/projects/boot-repair-cd/?source=directory)

---

### Post by william67 on 2015-03-24
Thanks yaneck,  booted from the Boot-Repair CD, it ran automatically.  Boots right up.

---

### Post by yancek on 2015-03-24
You're welcome.  That wasn't so hard, was it?

---

