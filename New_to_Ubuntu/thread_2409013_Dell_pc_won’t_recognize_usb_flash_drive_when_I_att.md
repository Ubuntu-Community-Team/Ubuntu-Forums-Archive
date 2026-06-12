---
title: "Dell pc won’t recognize usb flash drive when I attempt to install Ubuntu"
date: 2018-12-26
forum: New to Ubuntu
---

### Post by taylorben18 on 2018-12-26
I recently bought a Dell Optiplex 380 with no OS or hard drive. I installed a hard drive into the machine and then attempted to put Ubuntu onto the machine. 

So - I’m going to very thoroughly explain what I did because I assume this is a stupid error on my part. 

I formatted my 8gb flash drive on the Mac mini that I usually use. I then downloaded the most recent Ubuntu iso file onto the flash drive. I then plugged it into the new desktop and powered on and it would not read it. If I hit f12 it gives me the opportunity to select usb as the drive from which it will boot, but then the system freezes.

It also seems relevant that I ran a system scan on the desktop and it says the hard drive is not connected. I’ve opened it up three times and it’s plugged into the motherboard and the power supply so I can’t figure out why it would say that. 

Any help would be appreciated. Apologies for being new and probably foolish.

---

### Post by QIII on 2018-12-26
Hello!

There are two types of people who come here:  Those who have much to learn about Linux and those who have learned much about Linux.  Those in the latter group are still in the former.  So don't feel foolish.

When you formatted the USB on your Mac, as what form of filesystem did you format it?

---

### Post by SeijiSensei on 2018-12-26
Simply downloading an image file onto a flash drive will not create a bootable disk. There are other steps involved like writing the drive's boot record.

Looks like you're best answer might be: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos)

I don't use Macs, so there may be a better method.

And you don't need to apologize.  Most people have never created a system from scratch like you're trying to do.  Good luck!

---

### Post by taylorben18 on 2018-12-26
For some reason it would not let me format in fat32 - that option was not available - so I formatted in ms-dos (fat) and did not feel good about it

---

### Post by QIII on 2018-12-26
OK.  Not sure if that would be a problem or not.

But hearken to the advice of SeijiSensei and read through the information at the url given:  You don't just copy the file.  What you want by hook or by crook is a bit-by-bit duplicate of the ISO on the installation medium, not just a copy of the file.

---

### Post by oldrocker99 on 2018-12-26
If worst comes to worst, an .ISO can be burned as an image to a DVD. It's slow as dirt, but it will do the job. 

BTW: FAT may not be able to burn it, anyway. I think that a new USB thumb drive is already formatted as FAT32, which is what you want.

---

### Post by ajgreeny on 2018-12-27
Does the flash drive have a partition on it?

You will have to have a partition to be able to use the drive in Linux, and depending on what you have done with the drive in the past, it may or may not have a partition table or any partitions.

I also do not know Macs or anything about how they format disks/partitions so may be this is a red herring as far as your problem is concerned.

---

### Post by Geoffrey_Arndt on 2018-12-27
Recommend you try "Etcher" to create the boot-able usb stick.   It is the default goto app for folks needing a simple and fast way to make these bootable flash-stick drives.    Works on OS X, WIndows and Linux.

See:   [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

---

### Post by zorlax on 2018-12-28
Given that the machine isn't new there could be something wrong with the mobo. Do you have a hdd that you know works that you can try or another machine that you can try the new hdd in?

Stuff I would do before worrying about the USB stick. Download the latest BIOS for the machine, install it, load default BIOS settings, enable USB boot and then try again.

---

