---
title: "please PLEASE help"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by lauragee on 2008-12-01
i'm almost at the point of going nuts.
i have tried so many times and in so many configurations to install ubuntu that its unbelievable.
Then finally i decided to disconnect EVERYTHING i have from my system except for my primary drive (boot drive) and my cdrom.
i deleted all partitions from the drive and started the live cd and let ubuntu do its thing right up to the final install. i chose advanced and chose for the grub to be loaded onto /dev/ads1 because i read here that a sdai drive is only recognized as such.
After the install and reboot i got the error 21.
i then did it all over again and chose /dev/sda leaving the No 1 off and on reboot i got a message 
Grub loading stage1.5.
Grub loading please wait
Grub>
i have no idea where to go from here.
Each and every time i have tried since disconnecting everything to install it has been on an empty drive and ubuntu was to use the whole drive and each time i get a similar error to the above.
i really hope someone can help

---

### Post by Kellemora on 2008-12-01
Hi L

Did you run the TEST to see that the CD you are trying to install from is correct with no errors?

You DID burn it as an .iso I assume?

It should be one of the options from the install screen that pops up when you insert the CD.

You could also select to do everything automatically on it's own.  There is nothing you cannot change later on, or add that wasn't added.

TTUL
Gary

---

### Post by hyper_ch on 2008-12-01
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by halitech on 2008-12-01
check here and see if this helps any

[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

---

### Post by ugm6hr on 2008-12-01
Have you tried leaving the GRUB install location as whatever the default is?

---

### Post by bobnutfield on 2008-12-01
Just curious why, if you have wiped all the partitions from the disk before the install, would you want to go to "advanced" when the standard install would automatically install Grub to the proper location.  In any case, try this:

When you start your computer and get to the prompt:

> grub>

Type this:

> grub> find /boot/vmlinuz

This is just to see if you get a response.  I am wondering if your actual install was successful.  If it is installed correctly you should get a response stating the kernel in your boot directory.

If you do, then it may be possible to just reinstall Grub to the MBR of the drive.

---

### Post by lauragee on 2008-12-01
i went into advanced and changed the grub location because i read somewhere here that linux does not recognize scsi as (HD0) and that was the only place i could see to change it to scsi


> **bobnutfield said:**
> Just curious why, if you have wiped all the partitions from the disk before the install, would you want to go to "advanced" when the standard install would automatically install Grub to the proper location.  In any case, try this:

When you start your computer and get to the prompt:



Type this:



This is just to see if you get a response.  I am wondering if your actual install was successful.  If it is installed correctly you should get a response stating the kernel in your boot directory.

If you do, then it may be possible to just reinstall Grub to the MBR of the drive.

---

### Post by bobnutfield on 2008-12-01
> **lauragee said:**
> i went into advanced and changed the grub location because i read somewhere here that linux does not recognize scsi as (HD0) and that was the only place i could see to change it to scsi

You are correct that the newer kernels recognize the drive as /dev/sdX, but when you install Grub should always be installed to /dev/sda.  When you install to /dev/sda1 you are installing it to the first partition of the first drive.

---

### Post by halitech on 2008-12-01
> **lauragee said:**
> i went into advanced and changed the grub location because i read somewhere here that linux does not recognize scsi as (HD0) and that was the only place i could see to change it to scsi

are you using scsi drives?

> **bobnutfield said:**
> You are correct that the newer kernels recognize the drive as /dev/sdX, but when you install Grub should always be installed to /dev/sda.  When you install to /dev/sda1 you are installing it to the first partition of the first drive.

depends on the kernel and the distro. My debian installs still see my hard drives as /dev/hda but usb drives as /dev/sda and ubuntu was bouncing back and forth there for a little while.

---

