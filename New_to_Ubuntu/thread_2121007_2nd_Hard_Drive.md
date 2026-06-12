---
title: "2nd Hard Drive"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by 1200max on 2013-02-28
I have got Windows installed on my desktop computer but I have also got an 80gb internal hard drive that I have been using as an external drive for storage. 
Having got a proper external drive, the 80gb drive is now redundant and I am thinking about installing Ubuntu on it and putting it inside the computer.

How would I go about getting Ubuntu onto the drive and set it up so I have the choice of which os to use.

I have already got Ubuntu on a live usb and liked it but I don't want to install it as a dual boot on my C: drive as I don't quite know what I am doing.  That's why I am looking at the 80gb drive.

Many thanks in advance.

---

### Post by cortman on 2013-02-28
The Ubuntu installer is very helpful when it comes to selecting an HDD to install on. You'll get a drop down menu with your hard drives listed, simply choose the 80 GB one and you should be fine.
But as always, BACK UP your data first, before doing anything. Just in case.

---

### Post by kc5hwb on 2013-02-28
They way I've done it before was to just run the Ubuntu CD from Windows, and follow the prompts for installing it as a secondary OS.  I am not sure if it will prompt you for a dual boot if it isn't installed to the same drive as Windows, though.  When I did my dual boot on my laptop, it was already running W7, so I ran the Ubuntu CD (while in Windows) and it installed to a seperate partition I had already created.  I assume you could use the 80gb drive for this feature, but not 100% sure.

---

### Post by I8NY on 2013-02-28
During the installation process you will be given the option on where to install Ubuntu.  You can select your 80GB HDD and it will install on that.  Now the boot loader, GRUB, will need to be installed on the boot HDD that I presume is the Windows HDD.  It will replace the Windows boot loader with itself (GRUB) and on boot will allow you to select either Window or Ubuntu (default choice).  The other option is you can unplug your Windows HDD and then install Ubuntu with the GRUB loader on the 80GB HDD.  Once you've installed Ubuntu on the 80GB you can plug back in the Windows HDD and select what HDD to boot from the BIOS.  Usually newer BIOS (past 4yrs maybe) will allow you to select the boot devic on boot by pressing one of the F1-F12 keys.  If your BIOS doesn't have this then you will have to go into the BIOS options and manually switch which HDD should boot first in order to select what OS to launch.

---

### Post by grahammechanical on 2013-02-28
Another point to take note of. If you install Ubuntu on the 80Gb drive without the Windows drive connected Grub will not know about Windows. So, lets us call the Windows drive sdb and the Ubuntu drive is sda and grub is installed in the MBR of sda, then boot into Ubuntu and run this command

```
sudo update-grub
```

that command will search for other operating systems. It should detect Windows and record its location in its configuration files. Now, when you boot the Ubuntu drive you will get a menu that will let you choose either Ubuntu or Windows. Just in case you cannot choose the drive to boot from BIOS. Regards.

---

### Post by cortman on 2013-02-28
^^ graham makes a very good point here.

---

### Post by ajgreeny on 2013-02-28
When you get to the disk preparation stage of the installation, which is where you set up and format partitions, make sure you choose "**Something else**"; this is what used to be called "manually set partitions" or similar description.

If you do that you will be able to make the partitions to install to, and also which disk to use for the grub bootloader.  Make sure you choose to put grub on the MBR of your newly added ubuntu (second) disk, sdb(?).  I'm assuming you're still using the old style MBR BIOS, not UEFI.

Now at startup if you choose to boot from the ubuntu disk, you will go to grub, from which you will be able to choose either OS.  If you boot to the original disk you will go straight to windows from its own bootloader, bypassing grub entirely.  Choice of disk to boot from is usually made by the press of a single key.

This will give you an advantage should grub ever break and stop you booting to either OS, as you will still be able to boot windows and from that figure out how to mend the system and get grub back working again.

---

