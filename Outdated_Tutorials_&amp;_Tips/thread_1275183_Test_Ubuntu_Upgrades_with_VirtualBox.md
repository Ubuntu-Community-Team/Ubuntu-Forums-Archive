---
title: "Test Ubuntu Upgrades with VirtualBox"
date: 2009-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by hambone79 on 2009-09-25
I originally posted this tutorial on my personal [website]("http://www.hacksawlabs.com"), but I figured I would go ahead and share it here since people may benefit from it. This is a method that I have been using to test major upgrades (i.e. jumping from 8.04->9.04) to make sure they work properly before doing the real thing. This way you can troubleshoot and repair problems before performing an update that could break your system.


[SIZE="4"]**The Backup Disk**[/SIZE]

To get started with this tutorial, you should create a backup disk using my tutorial on creating [Backups to an External Drive]("http://www.hacksawlabs.com/index.php?option=com_content&view=article&id=50:backup-to-an-extenral-drive-with-rsync&catid=36:system-administration&Itemid=53"). This will give you a fresh snapshot of your current system to test the upgrade.


[SIZE="4"]**Configuring VirtualBox**[/SIZE]

Configuring VirtualBox is pretty straight forward. You just create a virtual machine that is tailored to your specific to Ubuntu and configure the VM to boot from your external hard drive by using an Ubuntu live CD.


**_Check your groups_**

Before you begin setting up the virtual machine, check and make sure you are in the vboxusers group by typing groups in a terminal window. This should return a list of all the groups that you are currently a member of. If it is missing the vboxusers group, type this command in the terminal:

sudo usermod -a -G vboxusers your_username

This step is absolutely necessary because it allows VirtualBox to make the USB devices available to your virtual machine.


**_Create a New Virtual Machine_**

Fire up VirtualBox and create a new virtual machine:
[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade1.png[/IMG]


**_Memory_**

Set the memory to something reasonable. I set it to 512MB which isn't optimal, but it will give you plenty of memory to run the LiveCD with enough left over to handle the upgrade process.

[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade2.png[/IMG]

 
**_Skip Hard Drive Creation_**

A virtual hard drive is not needed for this trick because all of the work is going to be done on the external hard drive, so just uncheck the Boot Hard Disk option.

[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade3.png[/IMG]

 
**_Add a USB Filter_**

Now that the basic VM is configured, open the settings for your VM and go down to the USB options. You will want to make sure that the USB options are enabled and that a USB Device Filter exists for the external hard drive. IMPORTANT: Make sure that your external hard drive is not currently in use on your computer. If it is mounted to a directory (such as /backup in my case) just unmount the drive.

[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade4.png[/IMG]
 

**_Configure the LiveCD_**

Now go up to the CD/DVD-ROM option and mount the Ubuntu LiveCD disk image:

[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade5.png[/IMG]
 

**_Boot the VM_**

Now you can boot the VM. If all goes well, you should immediately see the Ubuntu options screen so just pick the "Try Ubuntu..." option and hit Enter.

[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade6.png[/IMG]


**_Check for Drives_**

When  you boot into the desktop, take a quick look and you should see the USB drive appear on the desktop. In my case it showed up as 250.1 GB Media. If you don't see the disk, you most likely forgot to add yourself to the vboxusers group or you selected the wrong device in the USB filters.

[IMG]http://www.hacksawlabs.com/images/stories/vb_upgrade/vb_upgrade7.png[/IMG]

 
***chroot to the External Drive***

This is where the magic of this whole trick comes into play. You are going to chroot to the USB disk and start the system upgrade. This way you are working with exactly the same files, in exactly the same configuration as the system you created the backup from. To get started, run the following commands in a terminal:

ubuntu@ubuntu:~# sudo mkdir /mnt/sandbox

ubuntu@ubuntu:~# sudo mount /dev/sda1 /mnt/sandbox

ubuntu@ubuntu:~# sudo chroot /mnt/sandbox /bin/bash

Now you should be logged in as root in your USB disk environment. Now all you need to do is run a few apt commands to get the system up to date, then proceed with the upgrade:

root@ubuntu:/# apt-get update

root@ubuntu:/# apt-get upgrade

root@ubuntu:/# apt-get dist-upgrade

root@ubuntu:/# apt-get install update-manager-core

root@ubuntu:/# do-release-upgrade -d

From here, just follow the instructions on screen!

 
***Wrapping Up***

If all goes well and the upgrade finishes without a problem, you should have a high confidence level that upgrading your normal system should go just as smooth (but keep a backup just in case!). If something goes horribly wrong, just take note of the problems, recreate the backup disk,  fix the errors you found, and run this tutorial again.

---

