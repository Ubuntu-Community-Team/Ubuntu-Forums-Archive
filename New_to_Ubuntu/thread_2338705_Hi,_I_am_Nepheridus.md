---
title: "Hi, I am Nepheridus"
date: 2016-09-30
forum: New to Ubuntu
---

### Post by nepheridus on 2016-09-30
Hey There!

I am Nepheridus. I am extremely brand new to Ubuntu or anything about it all.
I am having a hard time choosing what to do. INstall Ubuntu and erase everything on my alienware
or not? i dont know. i dont know what to do. lol. I tried to run alongside windows but it doesnt give me a option to do that
so i am figuring just jumping right in and erase everything and learn the OS.

Could anyone give a suggestion of what i need to do before i wipe out my drive?

Thanks again everyone!

-Nepheridus-

---

### Post by yetimon_64 on 2016-09-30
I would suggest you use Windows tools from within windows to shrink the windows volume and use the newly created spare space to install ubuntu into, that is, set up a dual boot with both windows and ubuntu.

Wiping windows may not be such a good idea if you are not experienced with linux. Linux has quite a steep learning curve and you may regret wiping windows if you are used to it and very new to linux. 

One more important point; you should do a complete backup of or image the drive before doing any partition based tasks. If a problem/fault occurs you will then have an image or backup to restore your hard drive from.

---

### Post by nepheridus on 2016-09-30
Understood. I did shrink and made available space for linux however and changed it to "/" but it doesnt look the same everyone elses and there is literally like 8 different partitions that i have no idea whats what and everything shows as "Unknown".
I have tried looking at alot of tutorial's and how to's but still not coming up with anything. Ubuntu gives me a message that Partition is formatted correctly and i am not sure exactly what its talking about but it said that it could cause trouble/faults in installation.
So i am kinda gun shy on clicking continue. As far as backing up windows i have a bootable USB and Product key for my windows 10. So if worse comes to worse i could always just fresh install and wipe everything from day one right?

-also i have a SSD and HDD so if that would create a issue-

Well.. I just re-read this post and i sound like a complete idiot. I will go back and research.

---

### Post by cariboo on 2016-09-30
I guess the first thing to learn is partitioning, below is an image of gparted, that shows the different partitions on my my hard drive

[[img]https://s14.postimg.org/40jrz5uct/Screenshot_from_2016_09_30_20_03_38.png[/img]](https://postimg.org/image/40jrz5uct/)

[LIST]
[*]Partition 1, diagnostic, hidden
[*]Partition 2,  Boot,EFI
[*]Partition 3, boot partition for Windows
[*]Partition 4, Where Windows 10 is installed
[*]Partition 5, More diagnostics, hidden
[*]Partition 6, Recovery data, hidden
[*]Partition 7, Ubuntu / partition, where Ubuntu is installed
[*]Partition 8, Linux swap
[*]Partition 9, /home, where my personal data is stored
[/LIST]

I used the windows Disk management utility to resize the windows partition to create enough empty space to install Ubuntu. During the installation process I used the Something Else option to create a 40GiB  / partition, a 4GiB swap partition, and a 300GiB home partition.

If you just want to try Ubuntu, you could probably get away with a single 20GiB partition and a swap partition.

---

### Post by yancek on 2016-10-01
If you currently have windows 10 installed, you are probably using UEFI so it would be a good idea to read the Ubuntu documentation at the  link below.  The second link below gives some detailed information on installing Ubuntu but does NOT discuss using UEFI.  There is good information on dual-booting, formatting and partitioning.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

After reading, post back with any specific questions.  One thing I would suggest is to not use the auto-install method, the Install Alongside but rather select Something Else which is the manual install method.

---

### Post by Bucky Ball on 2016-10-01
Welcome. Make sure you boot into Windows and switch off hibernation, boot to the BIOS and switch off secure-boot and fast-boot. When you boot from the install media (usb or disk) there will probably be two entries. One will have [UEFI] next to it. Important: If you have Windows pre-installed in UEFI you *must* install in UEFI, as noted above.

When you boot from the install media you should get to a screen of options, 'Try Ubuntu' 'Install Ubuntu' etc. Does everything go ok when you 'Try Ubuntu'? If so, you can click the icon on the desktop there to install Ubuntu.

When you get to the partitioning section, choose 'Something Else'. In there you will be able to set up partitions. You need to think about what you want there. You are going to need at least / and /swap. These are both available default mount points you can select during the partitioning. 

There are a few options for partitioning. If you already have your personal data on a data partition (NTFS filesystem) and you want to share that between Win and Ubuntu, then you can probably get away with / and /swap and link to that data partition from within Ubuntu.

If you don't you might want to add a /home partition. In that case

/ = 20-25Gb
/home = big as you can make it
/swap = 2Gb at the end

Hope that helps in some way.

PS: In the partitioning section, you should see the existing Win partitions. Just leave them as they are. You are looking at the free, unallocated space. That is where you are going to be putting your Ubuntu partitions. Don't bother preparing these partitions beforehand in Windows as Win can't create EXT partitions which Linux needs. You'll just end up deleting and recreating anyhow. Just leave blank space where are going to install, NO partitions. (You could, though, create the partitions from 'Try Ubuntu' and launch Gparted and partition with that. Six of one, half a dozen etc ...)

---

### Post by nepheridus on 2016-10-02
Okay. Appreciate the help above. Today i have actually got alot further then i have in recent attempts. So... when i was making these partitions i noticed the same message that pops is about needing a partition for a bootloader. So i made a partition for the boot loader and actual got the almost to the end of the set up and it crashed saying something werent able to be downloaded so i am not sure exactly what i need to do to fix that but finally i am feeling like i am making progress. Also, After reading alot i read that there were some issues about Windows 10 Anniversary Update is causing problems for people dual booting is there any truth to that?

---

### Post by nepheridus on 2016-10-02
I know i shouldnt post bump... but this is not what that is... I would like to say thank you guys for all the suggestions and links and pointers in getting me here... But i have dual booted Ubuntu and windows. I really do appreciate the help everyone!!!! THANKS AGAIN!

---

### Post by jeremy31 on 2016-10-02
If your issue is fixed, please use the thread tools menu near the top right of this page to "Mark as Solved"

---

