---
title: "Question about hardare upgrade and 12.04"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by pjamessmith on 2013-08-03
Hi Forum People:

I'm
[LIST]
[*]running 12.04 from a separate SSD (SATA2), and
[*]my home directory is on another HD.
[/LIST]

I want to upgrade my hardware to

[LIST]
[*]SATA6 SSD from SATA2, and
[*]get a new mobo.
[/LIST]

Is it possible simply to 
[LIST]
[*]copy the contents on the SATA2 SSD to the SATA6 SSD, and
[*]install the new mobo
[/LIST]
in a way that when those changes are made and the SATA6 SSD is installed and SATA2 removed that all my software (OS, etc) will work seamlessly?

Thanks!
Old Jimma from the Old County

---

### Post by grahammechanical on 2013-08-03
The problem with this idea is that in Linux/Ubuntu hard disks and partitions on those hard disks are given a UUID - Universally Unique Identification. It is a string of alpha-numeric characters 31 characters long, not counting the dashes that break the string into groups. The boot loader uses this character string to find where Ubuntu has been installed. By copying the OS from one drive to another you will break the connection that the boot loader (Grub) has with the drive/partition that Ubuntu is on. 

The best way and I mean the way that has the best chance of returning you to a working machine, is to do a new install of Ubuntu onto the new SSD using the Something Else option. At the partitioner stage you can direct the installer to put Ubuntu into the new SSD. 

You select the SSD and click Change and in the dialog box you change "do not use" to "Ext4." Then you give the drive a mount point of /. You mark the drive to be formatted and click accept.

Next you select the HD that has  /home on it. Click Change. You change "do not use" to Ext4" but you do not mark the drive to be formatted. This is important. So, I will repeat, Do Not Mark the Drive to be Formatted. Set the mount point to /home.

Now look at the panel which tells you where the Grub boot loader is going to be installed. By default it is set to sda. Is it set to the new SSD? Make sure it is set to the new SSD. There is a drop down menu on that panel. Now continue with the installation.

In this way the installer will identify the new hardware on the new motherboard and put in the correct drivers. The new install of Ubuntu will detect all the settings in /home. Remember, the HD has not been formatted so everything is still there on the HD. All you will need to do is reinstall any non-default applications that you have installed.

Well, you did put "seamlessly" as a condition, did you not?

Regards.

---

