---
title: "Remove Windows after Ubuntu install"
date: 2015-12-18
forum: New to Ubuntu
---

### Post by Erez_Manor on 2015-12-18
Hi All,

Need your help.
I would like to remove Windows 7 from my harddrive

here is the history and status of my system:
1. I had Windows 7 64 bit (122GB) + 2 partitions available (116GB,700GB)
2. I install Ubuntu on one of the other partitions (122GB)  
3. I want to _**completely**_ remove the windows but I fear that my Ubuntu will not load as I see some windows system partitions (100MB)  

Please advise how to remove Windows completely from my hard drive.
See attached screen-shot
[ATTACH=CONFIG]266220[/ATTACH]

here is the content of grub file:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="persistent"



Thanks,
Erez

---

### Post by deepakdeshp on 2015-12-18
Please take backup of your data before this process. If there is any error,system may become unbootable

Boot Ubuntu and run command shown in code in terminal.
In the example sda2 and sda13 are the partitions which are used by Ubuntu. 
Other partitions except sda02 and sda13 can be deleted by gparted.
run update-grub so that grub will probe the os and update
Grow the ubuntu partititions in gparted ,
You are windows free now.Good luck

```

$mount |grep sda
**/dev/sda13 **on / type ext4 (rw,errors=remount-ro)
/**dev/sda2** on /boot/efi type vfat (rw)

$sudo gparted ## delete Windows part

$sudo update-grub

## Grow the Ubuntu partitions in gparted

$sudo reboot

```

---

### Post by Erez_Manor on 2015-12-18
Thanks for your reply.
Few questions:

1. sda2 is the partition of the windows and also marked as boot. You wrote that I should not delete it as it is used by ubuntu, but this is my main purpose! I want to delete this partition.
2. sda13 - I can't find this partition. where do you see it in the screenshot?
3. when my computer starts I see grub menu with option to boot from Ubuntu or Windows. How can I make sure that if I delete the boot partition (sda2) and the system reserved of the windows (sda1), my Ubuntu will boot properly? 

Thank you for your help

[ATTACH=CONFIG]266227[/ATTACH]

---

### Post by yancek on 2015-12-18
If you want detailed instructions on your particular computer you will need to post detailed information on it.  The best way to do that is to run the boot repair software from Ubuntu.  It is avaiable for download from the site below and you can either burn it as a bootable image to a CD or install it in Ubuntu by following the instructions on the page.  Make sure you select the option to "Create BootInfo Summary" and do NOT try to make any changes.  Post the output or a link to it here as that will give us all the necessary information.

> 1. sda2 is the partition of the windows and also marked as boot. You wrote that I should not delete it as it is used by ubuntu

No, that was just an example on his computer.  The boot partition for windows is not used by Linux.  Having a partition marked as active/boot is only required for windows operating systems and I have never seen a Linux OS that used or needed it.  You should be able to delete sda1 and sda2 and still boot Ubuntu if you are using the Grub bootloader to boot both Ubuntu and windows.  sda3 appears to be a windows data partition, correct?  If so, leave it along.  

I would suggest that you run the boot repair and post the output or a link to it first

---

