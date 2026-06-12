---
title: "Is there a way to download an ISO and update it before making a live USB image?"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by YQ002lc2 on 2014-04-14
Can you download an ISO,
update it,
and rewrap it as an ISO
before making it into a live USB disk?

---

### Post by pfeiffep on 2014-04-14
Others may have a different view.
If you make your USB persistent some of the updates will be saved.

---

### Post by YQ002lc2 on 2014-04-14
Yes, I'm aware of being able to set asside some persistent storage area in the USB creator that will allow updates and changes to be saved to the USB. (I assume this is what you are referring to)
However, I'm trying to install those updates and then make another ISO from the updated image.

Thank you.

---

### Post by YQ002lc2 on 2014-04-14
Reading around, I saw mention of remastersys dist option, but it seems that project is no longer active.
Please let me know if you know of alternatives.

---

### Post by pfeiffep on 2014-04-14
3 possibilities[URL="http://clonezilla.org/"]

Clonezilla[/URL]
[Relinux]("http://www.howtoforge.com/creating-your-own-distributable-ubuntu-dvd-relinux")
[Customization Kit]("http://sourceforge.net/projects/uck/")

---

### Post by aeyeaws on 2014-04-14
if you look around most of these iso's have daily releases

---

### Post by pfeiffep on 2014-04-14
> **aeyeaws said:**
> if you look around most of these iso's have daily releases
My understanding of the OP is there might be customization involved also

---

### Post by ian-weisser on 2014-04-15
You can do it, but it's NOT easy.
A live ISO is very complex. Much more complex than merely throwing a bootloader onto a data image.
It's an entire bootable, working system, with special settings for storage devices to make it operate in RAM only, wrapped in a read-only squashfs, plus special bootloader settings.

So after you update and test-boot your working Ubuntu install, you need to copy an image of it into a squashfs image, and edit the CD bootloader to point to that image. And test at every step along the way.
That's rather oversimplifying the process.

There's a good tool at [http://live.debian.net](http://live.debian.net) for creating live images that are maintainable, and shows you some of the complexity in the process. 'Maintainable' is different from 'updatable'.

---

### Post by Double.J on 2014-04-15
> **pfeiffep said:**
> 3 possibilities[URL="http://clonezilla.org/"]

Clonezilla[/URL]
[Relinux]("http://www.howtoforge.com/creating-your-own-distributable-ubuntu-dvd-relinux")
[Customization Kit]("http://sourceforge.net/projects/uck/")


+1 ubuntu customisation kit

Remastersys is a degraded ptoject. [Uck]("https://help.ubuntu.com/community/LiveCDCustomization") is in the repos

Jj

---

