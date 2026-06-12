---
title: "Booting Ubuntu from an External HDD"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Climhazard on 2008-09-30
Hey guys, I'm an absolute n00by when it comes to any of this stuff, so sorry if it sounds idiotic
I really want to try out Ubuntu, firstly because I'm bored with Windows and secondly because I want to broaden my knowledge of other operating systems, especially a Linux OS.
Basically, I'm planning on installing and booting Ubuntu from my External USB hard drive. One reason for this is that I don't want to partition my internal hard drive anymore and I'm running out of internal hard drive space as it is. My external hard drive mostly just sits around doing nothing, so I thought this would be the perfect use for it.
I have a couple of questions regarding this idea:
My External HDD is FAT32, which I understand Ubuntu will not run on, but I've heard Ubuntu runs on it's own Ext3 partition which it creates itself. Is this true?
Do I have to completely reformat my External HDD, because I currently have photos backed up on it. Can I keep some of the FAT32 partition so I can still backup stuff from Windows?
If there is anything else you think I'll need to know, please feel free to tell, I honestly have no idea what I'm doing :D Thanks in advance!

---

### Post by kk0sse54 on 2008-09-30
You can partition your external hardware to have one FAT32 and one EXT3 partition so as to preserve your data. As for booting off your external hard drive make sure your BIOS supports booting off a USB mass storage device. Otherwise you can use your external hard drive as storage for both windows and Ubuntu and then try to clear some space on your internal and install Ubuntu on a small partition there

---

### Post by wolfen69 on 2008-09-30
see [this]("https://help.ubuntu.com/community/Installation") for help with installation. i would unplug your windows drive during the install process. after you defrag your usb drive, during installation, you will be given the choice to use only part of the drive for ubuntu, creating another partition for your files. just do a little reading first. it's not hard.

---

### Post by Climhazard on 2008-09-30
Fantastic! Thank you so much for the speedy replies guys. Last couple of things before I bite the bullet. I can't actually unplug my Windows drive because it's on my internal HDD and I'm using a laptop. Does this matter? Also, how do I find out if my BIOS supports booting from a USB device? Thanks in advanced!

---

### Post by Crafty Kisses on 2008-09-30
Well in the BIOS you can check to see if you're external HDD is on the boot list and if it is, you want to set that as your primary boot device, it should just show up on the list.

---

### Post by wolfen69 on 2008-09-30
> **Climhazard said:**
> I can't actually unplug my Windows drive because it's on my internal HDD and I'm using a laptop.

get a phillips head screwdriver and take off the plate on back and remove the hard drive. easy.

---

### Post by Gannon8 on 2008-09-30
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401)

Tutorial on installing ubuntu to a flash drive.

---

