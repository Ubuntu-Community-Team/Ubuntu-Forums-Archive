---
title: "How to fix GRUB Error 21"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by mbadawi23 on 2008-07-31
Hello All,
      I have been playing with ubuntu for a while now. Last night I tried installing it on an external 120GB Toshiba USB hard drive on my IBM ThinkPad T41. I performed the installation WITH the internal hard drive attached (WinXP Pro). Apparently GRUB screwed my boot record on the xp drive; now it gives GRUB Error 21 whither the external drive is connected or not! I have my boot sequence in BIOS set to boot first from DVD, USB, HDD. Any thoughts? Thank you.

---

### Post by Separ on 2008-07-31
You could try reinstalling grub from the Live CD
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or you could try a supergrub Live CD.

---

### Post by Diabolis on 2008-07-31
Try to reinstall grub, that will generate the menu.lst file again.

Steps to reinstall grub:
```

sudo grub
find /boot/grub/stage1    It will find all the places **from where** you can install grub.
root (hd?,?)              Select **from where** you want to install grub
setup (hd?)               Select the drive **in which** you want to reinstall grub
reboot
```

So the output of the **find** command is the input of **root**.

If you can't boot, you can follow this steps from a live-cd.

Look at the grub page: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Grub errors: [http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors)

Error 21:
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

---

### Post by mbadawi23 on 2008-07-31
Thank you for your reply. so do suffest then that I do this without the XP internal drive connected? I suppose after moving the GRUB to the external drive and hopefully being able to boot into linux from there; then I can disconnect the external and boot using WinXP CD and fix the MBR again, right?

---

### Post by Diabolis on 2008-07-31
Sorry, but I don't understand what you want to do.

You can install and use the boot loader of your preference grub, mbr, supergrub, lilo.

---

### Post by mbadawi23 on 2008-07-31
The main goal I want to achieve is that when the external drive is unplugged, the WinXP loads normaly without having any bootloader. I would like it to remain in its original state from the factory.

---

### Post by Diabolis on 2008-07-31
Fix mbr when the external(linux) drive is plugged in. So windows will always be available.

You may also use grub if you want it, just make sure that it gets installed in the windows drive.

The boot loader must be installed in the drive that is going to be always connected.

---

### Post by caljohnsmith on 2008-07-31
> **mbadawi23 said:**
> Hello All,
      I have been playing with ubuntu for a while now. Last night I tried installing it on an external 120GB Toshiba USB hard drive on my IBM ThinkPad T41. I performed the installation WITH the internal hard drive attached (WinXP Pro). Apparently GRUB screwed my boot record on the xp drive; now it gives GRUB Error 21 whither the external drive is connected or not! I have my boot sequence in BIOS set to boot first from DVD, USB, HDD. Any thoughts? Thank you.
I think I know exactly what happened to you: when you installed Ubuntu to your USB HDD, it overwrote the MBR of your internal HDD with Grub. Keep in mind that Grub actually resides in two places--in the MBR of your internal HDD, but also in the /boot/grub directory of Ubuntu on your USB HDD (that's where all of Grub's configuration files are). So when you boot up *without* your USB drive, Grub complains with "error 21" because it can't read any of its configuration files. 

If your BIOS allows you to boot from your USB drive, then probably the best solution to your problem is to replace the MBR on your internal HDD with a Windows XP MBR, and then install Grub into the MBR of your USB drive. That way Windows will boot fine without the USB HDD plugged in, and when you do plug in your USB HDD, you can boot Ubuntu (assuming you changed BIOS to boot USB before the internal HDD). 

I would download the [Super Grub Disk]("http://www.supergrubdisk.org") and use that to do all this; although it is possible to do it without it, it is a bit complicated to type out all the steps here.

---

### Post by Diabolis on 2008-07-31
Yep, you are right. Except for this part:
> Keep in mind that Grub actually resides in two places--in the MBR of your internal HDD, but also in the /boot/grub directory of Ubuntu on your USB HDD (that's where all of Grub's configuration files are).

Grub is installed just in one drive. The config files tell grub where the bootable drive is, but the drive that had grub was unplugged and this error appeared:

> 21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

Which is already telling you what happened :smile:

People is just not used to read and comprehend error messages, most of the times you just have to read them a couple of times to know what to do.

---

### Post by markbuntu on 2008-07-31
I used to have my machine set up with xp on one drive and Ubuntu on another with grub on the ubuntu drive which I installed in the SATA 1 plug so it would show up as sda (master for PATA/IDE) which is where grub will install itself. Since the mbr of my xp drive was never messed with, I could run xp without the Ubuntu drive in the machine.

My suggestion, restore the mbr on the xp drive and then add these lines in the grub/menu.lst

```

# chainload xp
root          (hd0,0)
chainloader     +1

```

When you select this option grub will hand over the boot process to whatever boot is on that partition, no questions asked. You can use the chainloader option to load any operating system with a boot sector.

---

