---
title: "Lost windows"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by tony56 on 2014-07-23
Hello All,

I am completely new to Ubuntu and any form of Linux.

I have/had windows XP running as my system and decided to investigate Ubuntu by loading it in parallel. I used the book "Linux in easy steps" by Mike Mcgrath as a guide. on switching on the system, Ubuntu loads and appears to work ok although I have a lot to learn about it. As it starts to load I get a menu (grub menu?) with Ubuntu at the top, then two memory test and the fourth item is windows. If I select windows I get an error message "Error # 5016 building the partition list on disk #0" and nothing more.

When I installed Ubuntu, I first cleaned up my hard disk with defrag, I loaded Ubuntu 14.04 in ram as suggested in the book and then ran install. I followed the suggestions in Mcgrath's book to partition the disk which was - 1. select manual partition specification, 2. select "free space" and add button, 3. Specify a logical swap partition of twice ram size, 4. select remaining free space and add 10Gb partition of type “ext4” with a mount point of “/”, 5 Select the remaining free space and create another partition of type”ext4” but with a mount point of “/home”.
 
Clearly I must have got something wrong. Can I get back to check the partitions? Suggestions would be gratefully received.
 
Thanks.

---

### Post by sotiris2 on 2014-07-23
Please login to your ubuntu install and run [bootinfoscript](http://ubuntuforums.org/showthread.php?t=1821980&p=11136267#post11136267). Note that you can open a terminal with ctrl+alt+t and if it asks for your password it will not show back any asterisks but it is reading it, just type it and press enter. Do not run any repairs with the program just create the bootinfo summary and post the link here.

---

### Post by tony56 on 2014-07-23
Hi, thanks for replying.
I have been trying to get this to work for some time. I went to your link "bootinfoscript" and got a post from "yannubuntu" and then created the terminal and typed in the code shown at stage 3. Then my password which seem to work ok but I do not get the screens illustrated at stages 4 & 5. However on the terminal I do get a key 60D8DA0B
Is that any help?
Thanks again - sorry to be so dumb!
Tony.

---

### Post by Mark Phelps on 2014-07-23
> Can I get back to check the partitions? 

If the XP partition was gone, you would not get that error message as Windows would not boot at all; instead, you would get a brief flash and then back to the GRUB menu.

The bootinfo script you were told to run will provide us info on what is there now.

---

### Post by Bucky Ball on 2014-07-23
Boot to Ubuntu, open Gparted (partition manager). Look for the NTFS partition, which will probably be at the beginning of the drive, and will probably be /dev/sda. If it's there, it's probably Windows. Try Boot Repair before going much further. That could remedy things quickly. If not, continue the quest:

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Boot repair with 'automagically' create the bootinfoscript output for you after it's run.

---

### Post by tony56 on 2014-07-24
I am having trouble following these suggestions. help.ubuntu.com does not respond. Is it down? Firefox seem to be working OK otherwise.
Thanks to you all who have responded.
Tony.

---

### Post by yancek on 2014-07-24
You indicate that you are able to boot Ubuntu, correct?  You said in your original post that when you select windows from the Ubuntu Grub menu, you get an error and it won't boot.  As indicated above, that means that your windows partition is still there, in some form but something wrong with the boot files.  Once you select windows from the Grub menu, that's it for Grub/Ubuntu.  You are now in windows.  Did you try doing an online search by simply typing in the error you got trying to boot windows.

You can get information on disk/partitions from Ubuntu.   Boot it and open a terminald and type:  sudo fdisk -l(Lower Case Letter L in the command)  That will show whatever drives/partitions you have connected, at least those recognized.  You can get the same information from a terminal with:  sudo gparted,

Go to the site below and read the instructions in the link in the Description box then download and run the script.  You will get a results.txt file as output in the directory from which you run it.  Post that here as it has a lot of pertinent information which should help.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by tony56 on 2014-08-03
Hi there,
Many thanks to all who have replied. All is ok now. It became clear that Ubuntu had not installed correctly ie I could not get to the links that were suggested also access to other website was fine - odd! A complete re-installation has cleard the problems and I am now finding my way around.
Again, mant thanks.

Tony.

---

### Post by oldrocker99 on 2014-08-03
Congratulations on your success, and, **please** don't hesitate to ask any other questions that may come up for you. Ubuntu (and any other GNU/Linux distro) has a learning curve, like any other new OS to you, and this forum exists to help you over that curve.

---

### Post by Bucky Ball on 2014-08-03
Good news. Please mark thread as solved by following the second link in my signature and don't hesitate to post a new thread for any further issues/questions. Good luck.

---

