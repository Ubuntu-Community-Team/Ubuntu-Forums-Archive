---
title: "Not enough free disk space"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by pauloz on 2014-05-18
Greetings - I know there are postings about this subject on the forum but I'm a little slow on the uptake and will need help to free up disk space on my hard drive. I received the following message and I suspect it's related to messages I've also received concerning Dropbox having problems syncing and trying to copy files from external sources. The message I received when using Update Manager was as follows:

   Not enough free disk space. The upgrade needs a total of 74.1 M free space on disk '/'. Please free at least an additional 9194 k of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I've emptied my trash and tried the 'sudo apt-get clean" command but I'm still having issues. When I checked others who were experiencing similar problems, some responses wanted to know the output of the 'df -h' command. Here it is:

Filesystem      Size    Used    Avail   Use%   Mounted on
/dev/loop0      17G     17G    258M   99%          /
udev              2.0G    4.0K    2.0G    1%        /dev
tmpfs             395M   960K   394M    1%       /run
none              5.0M     0       5.0M    0%      /run/lock
none              2.0G    100K   2.0G    1%      /run/shm
/dev/sda2       559G    247G  313G   45%       /host
/dev/sdb1       699G    165G  535G   24%      /media/FreeAgent GoFlex Drive

Now I know it's obviously got something to do with disk '/' above (is this the root directory?) but I don't know what to do next. Please, if anybody can provide step-by-step instructions, I shall be very grateful.

---

### Post by Elfy on 2014-05-18
This appears to be a wubi install. 

You're right to notice / being full.

You are either going to have to remove data you might have in your home folders, remove packages or increase the wubi file size.

Personally I would say that if you've finished deciding if Ubuntu is for you, then now is the time to move to a proper install - Wubi was never meant as a long term solution, nor is it supported now.

[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk) for information on resizing the wubi file

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Impavidus on 2014-05-18
+1 to moving to a real dual boot. Apart from doing a clean install of the latest Ubuntu, there is also the possibility to migrate your current Wubi install to a partition of its own: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by pauloz on 2014-05-18
Thanks for your replies. My desktop dual boots using Windows Boot Manager, not Wubi - my screen briefly displays an error message concerning Wubi when it boots up. Don't know if that helps but do I still follow the instructions given in [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk) to proceed? Or would it be better for me to clean install Ubuntu 14.04? (provided I back up everything of course). I'm presently using Ubuntu 12.04 and I was going to wait until the upgrade became available in July. I love Ubuntu and if I could, I'd get rid of Windows tomorrow but unfortunately I need it for some applications.

---

### Post by Elfy on 2014-05-18
In your current situation you have _zero_ chances of upgrading to 14.04 - it'll need a whole lot more than 9194 k of free space ;)

If you use the migrate wubi option - make sure to read the notes in the wiki - there are 12.04 specific issues.

Given where you are, I'd personally be inclined to think about the following scenario.

Resize the windows partitions with the windows tool - don't bother formatting at that point - windows won't format it to a suitable type.

Download and boot the 14.04 image and start the installer

It **should** see the freespace and offer to install into that, if it doesn't - **STOP** and quit the installer.

You'll then be able to use gparted, available in the live session, to create partitions to install into.

Then restart the install, choose Something Else at the partition stage - at that point you can choose your recently created partitions.

Once you boot you will be able to access the wubi files from your new install - [https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

It is not easy to give you any idea of how large an area to free up - but given you've used 17Gb, I'd look at something like 10Gb for /, 20Gb for /home and some swap - we've no idea how much RAM you currently have - but as a rough guide you can look here [https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F](https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F)

---

### Post by pauloz on 2014-05-18
Elfy - please excuse my ignorance but this is all sweeping over my head and I'm not prepared to attempt any resizing using Windows Boot Manager. I can't understand why I have to resize in Windows if I'm able to do the same thing in Ubuntu when I'm installing 14.04. My hard drive is 1000GB of which Windows 7 takes up 600GB. Because I use Ubuntu more than Windows now, I would like to have Ubuntu take up 600GB and Windows 7 400GB. Anyway, my problem is all the other terminology I've been introduced to e.g "10Gb for /, 20Gb for /home and some swap" - it doesn't make much sense to my ageing mind! Is there anything wrong if I attempt a clean install of 14.04 and then when the message appears whether I would like to install 14.04 alongside 12.04, I delete everything related to 12.04? So I (hopefully) end up having dual boot with Windows 7. I know this sounds simplistic, but I'm relatively new to Ubuntu. By the way, I have 4GB of RAM. Thanks again.

---

### Post by Mark Phelps on 2014-05-18
The presence of the "/host" folder is proof positive of a Wubi install -- which means the entire Ubuntu filesystem is contained inside a single file (root.disk) which is, in turn, contained inside a Windows partition.  That's why Linux partitioning tools can't be used in your situation to expand the space allocated to Ubuntu.

Wubi installs, as mentioned, were not meant for long-term use, hence the limitation on file size.

If you try now to install 14.04 along side 12.04, that will create a complex situation that will be difficult to maintain.  Better solution would be to uninstall 12.04 and then install 14.04 to its own partitions.

But, before you charge into dual-booting with Win7, you would do best to read the following details ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, and you are using MBR partitioning (not GPT) that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by pauloz on 2014-05-21
Many thanks for your help Elfy and Mark - success! It's been a learning curve about partitioning for me. When I installed 12.04 I didn't realise what I had done as you have outlined Mark. Everything went seamlessly - long live the Ubuntu forums!

---

