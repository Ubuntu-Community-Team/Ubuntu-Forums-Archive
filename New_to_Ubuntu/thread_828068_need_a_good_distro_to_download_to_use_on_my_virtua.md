---
title: "need a good distro to download to use on my virtual box"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by hazman on 2008-06-13
need a good distro to download to use on my virtual box.can i download a iso image and run it sraight from hard drive or do i have to make a cd has i have no cd writer and ubuntn doesn't see my external pcmcia cd rom any way to run it.never used a virtual machine before

---

### Post by cariboo on 2008-06-13
You don't have to burn an iso to run it in a virtual box. Using Virtualbox or other types of virtualizing software is a good way to test other linux distributions.

Jim

---

### Post by aeiah on 2008-06-13
you can select the .iso. if its a livecd it'll just run, if not, it will go to the installation page.

i think thats how it works anyway. if not, you could mount the .iso file to a folder and then configure the virtual machine's cdrom drive to be the mount point you've just created.

---

### Post by philinux on 2008-06-13
The iso file can be anywhere on your machine you just point virtualbox at it and bingo you're installing. Very easy to use.

---

### Post by wolfen69 on 2008-06-13
[TakeYourPick]("www.distrowatch.com")

---

### Post by MystaMax on 2008-06-13
The manual walks you through adding an ISO as a Virtual CD-ROM drive. Here is the excerpt:

>  If you have downloaded installation media from the Internet in the form of an ISO image file (most probably in the case of a Linux distribution), you would normally burn this file to an empty CD or DVD and proceed as just described. With VirtualBox however, you can skip this step and mount the ISO file directly.

VirtualBox will then present this file as a CD or DVD-ROM drive to the virtual machine, much like it does with virtual hard disk images. 

In this case, in the settings dialog, go to the &#8220;CD/DVD-ROM&#8221; section and select &#8220;ISO image file&#8221;. This brings up the Virtual Disk Image Manager, where you perform the following steps:

[LIST=1]
[*]Press the &#8220;Add&#8221; button to add your ISO file to the list of registered images. This will present an ordinary file dialog that allows you to find your ISO file on your host machine.

[*]Back to the manager window, select the ISO file that you just added and press the &#8220;Select&#8221; button. This selects the ISO file for your VM.
[/LIST]



Thats on page 34 of the [VirtualBox User Manual (PDF)]("http://virtual-box.org/download/1.6.2/UserManual.pdf")

Good Luck.

---

### Post by housam on 2008-06-13
> **hazman said:**
> need a good distro to download to use on my virtual box.can i download a iso image and run it sraight from hard drive or do i have to make a cd has i have no cd writer and ubuntn doesn't see my external pcmcia cd rom any way to run it.never used a virtual machine before

You can send a request to [[COLOR="Red"]_shipit_[/COLOR]]("https://shipit.ubuntu.com/") to send you a cd of Hardy free of charge . so you'll have the option to choose to get a fresh install or inside windows through wubi or through the VM.

---

### Post by billgoldberg on 2008-06-13
Ubuntu ?!

---

