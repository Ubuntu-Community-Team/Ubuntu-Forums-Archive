---
title: "How to clone recovery partition to USB drive"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by karsus2 on 2016-01-22
Hello everyone,

I am new to Ubuntu trying to install it through dual boot on my ASUS N61JQ laptop. That laptop has a recovery partition from ASUS that I don't want to mess up. It was pointed out to me (on another forum here) that I can make a copy of it through dd command. I have a 32gb USB 2 flash drive that should be enough to handle it. I also have Ubuntu installed in a USB stick that I can use to load Ubuntu (through option try Ubuntu without installing) for pre install things I need to do.

Can anyone point out to me how to do this (ie make a copy [bootable?] of my recovery partition on a USB drive through commands from the command line?

Note: I tried googling copy recovery partition to usb but god weird results that I couldnt make use of. I suspect I need to know more about this in order to google it properly and get a good result with instruction.

Any help is appreciated.

regards,
Karsus

---

### Post by leunam12 on 2016-01-23
I always use clonezilla for cloning drives and partitions; however, I think that the best course of action is to boot into Windows and press the start button and type "recovery" and see if you have an utility that will create a set of recovery DVD's or USB stick. Most computer that ship with Windows pre-loaded have this option. If you have Windows 8 with the metro interface and no windows7-style start button  do a search wherever it is that search is located

---

### Post by Mark Phelps on 2016-01-23
The problem with relying on a Recovery partition and OEM software is that, once you move or resize the partitions, it typically doesn't work anymore.  SO, copying it to an external drive, with the hopes of using it later for recovery, nearly always does NOT work.

Instead, if you simply want the ability to restore the Windows install you currently have, then consider using a third-party imaging/restoring Windows app known as Macrium Reflect.  

What I recommend is the following:
1) Download and install Macrium Reflect (MR)
2) Run MR and choose the option: "Create an image of the partition(s) required to backup and restore Windows" to write a full backup to an external drive or USB stick
3) Use the option to create a boot USB stick or CD

I use this all the time and it typically takes less than 10 minutes to do the image backup and about the same time or less to do a restore.  Plus, MR has the option to Add a Recovery Boot Menu entry.  This allows you then to boot into WinPE, and you can then use that to do a restore -- when you can't boot into Windows!

---

### Post by karsus2 on 2016-01-23
Thanks for the tip Mark, Macrium Reflect looks like an awesome tool.

To verify that I did things right.

After Installing Macrium reflect I created a recovery USB stick with WinPE (I followed suggestions, only place where I took initiative when I clicked add UEFI boot (sth) option).
Then I used the option create an image of the partitions required to backup and restore windows. I selected only the recovery partition and as destination I put F:\ (which is the destination of the USB I just created for recovery). I left the default recommended image name.

Is the above procedure correct? (Mainly putting the image like that? Will I be able to see it and use it?

After creating the recovery USB MR suggests to test it but I don't want to start it risking a format on my PC. Any suggestions on this?

Kind regards,
Karsus

Also another weird thing is that instead of 1 image at 11 gb (the size of my recovery partition) MR created 3 at 4, 4 and 3gb. Is that normal?

---

### Post by Mark Phelps on 2016-01-24
You don't use MR to save the recovery partition; instead, you use MR to image off the OS partition and whatever else is needed to be able to restore the install.  Saving off the recovery partition is a waste of time.

---

