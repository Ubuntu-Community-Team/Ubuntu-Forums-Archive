---
title: "[SOLVED] OH NO! &amp;quot;Cannot Mount Selected Partition...&amp;quot;"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by LMD1990 on 2008-06-14
Balls! I just got done giving Xubuntu it's own dedicated partition using partitionmanager and the Loopmounted Virtual Partition Manager (LVPM), and it was all ready and working- and then after turning my PC on again, and going to the boot menu and selecting Ubuntu, it tells me "Cannot mount selected partition..."

Here's how it all went...

Earlier on, I posted a thread asking how to move my Wubi installation of Xubuntu onto a dedicated partition. I followed all the instructions expicitly, and it all worked just fine. I then proceeded to uninstall Wubi (I kept a backup iso of the installation just in case). While in Windows, I did a bit of tidying up, which included running Disk Cleanup and defragging. All appeared well, until i started up and went to the boot menu...

[img]http://img440.imageshack.us/img440/4966/dsc00757mp1.jpg[/img]

I selected the first option, and then it proceeded to tell me "cannot mount selection partition..." Note that this happens on ALL of the Ubuntu options, including recovery mode.

How do I remount the partition? Can it be done? If this is something I can't undo, I shall be gutted- it's taken me SO LONG to finally get Xubuntu to work...

Please help me, this just sucks... :p

Thanks in advance

---

### Post by Duck2006 on 2008-06-14
You will have to edit your menu.lst so it points the boot loader to the wright partition, some info on grub that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by LMD1990 on 2008-06-14
That would be great, but after reading it, I don't entirely understand how to do this. A more simple-terms step-by-step would be great. I've never used GRUB before, so I need to be helped through this from scratch.

---

### Post by Duck2006 on 2008-06-14
From the terminal with the live cd post the output of.

sudo fdisk -l

---

### Post by LMD1990 on 2008-06-14
I rain sudo fdisk -l from the Live CD and got the following:

[img]http://img440.imageshack.us/img440/9328/dsc00758kw5.jpg[/img]

I tried following [This Howto](http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux), but when trying to mount my Linux drive I got an error saying that there was no ntfs signature or something, and that I should check that I was mounting the device correctly as opposed to the entire disk.

Where do I go from here?

---

### Post by LMD1990 on 2008-06-15
Hey folks, I edited the grub line- it was showing as being hd0, 0 but after changing it to hd0, 1, and pressing boot, Xubuntu booted- kinda. It showed the boot screen, but then it was replaced by yet another prompt window displaying Sysbox v.1.1.3 or something like that, and I just want to get out and go to my Xubuntu :( Where do I go from here?

---

### Post by LMD1990 on 2008-06-15
Nevermind. I did a clean install. I had quite a few problems.

---

