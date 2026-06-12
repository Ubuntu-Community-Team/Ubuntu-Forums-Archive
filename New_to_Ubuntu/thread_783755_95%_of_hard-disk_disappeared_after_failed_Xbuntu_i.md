---
title: "95% of hard-disk disappeared after failed Xbuntu installs"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ambercomm on 2008-05-06
Hi All, 

I would be grateful for any pointer on how to solve the following problem:

After failing to install Xbuntu 8.04 using Wubi under Window98 (the machine froze and I had to pull the power plug), I then tried to install directly from the Xbuntu 8.04 live CD. Each time the installation reached 82% and stopped at a message about checking apt. Eventually I had to pull the plug to get out. When I reboot to the original windows98 and on checking, I found that about 79G of the original 84G hard disk space has disappeared. 

Of the original 34G in the C: drive, only 4G is left (3.8G used and .2g unused). Of the original 49G in D: drive, only 0.4G is left.

I then re-boot using a Gparted Live CD. Gparted said that "no device detected"!

My computer specs are: Processor: AMD-K6 3D processor 450 MHz, L2 cache, 512K; RAM Memory: 256 M RAM; Main board: SiS-530; Video Card: SiS-530; Hard Disk: 83G, originally partitioned into C: and D:; MS Window98 and the associated application programs reside in drive C:. Drive D: was empty. 

How do I recover the lost hard disk space? Any help will be appreciated. 

Many thanks!

---

### Post by ichbinesderelch on 2008-05-06
i'm not sure if windows98 comes with the disc management programm by windows, but you could try editing the harddrives with that program. otherwise maybe try downloading some new ubuntu-xubuntu image, could be that yours is kinda broken!

---

### Post by tjwoosta on 2008-05-06
> 
I then re-boot using a Gparted Live CD. Gparted said that "no device detected"


i hate to be the one to say it but thats definatly not good if the partition manager doesnt detect it anymore

> 
the machine froze and I had to pull the power plug


there is a good possibility you caused some damage to the disk when you unplugged in the middle of an install

i would recommend trying a different gparted cd or try using the gparted that comes on the xubuntu live cd  "its under System-Administration-Partition Editor"

---

### Post by ambercomm on 2008-05-06
Hi ichbinesderelch,

Thank you for your comments. 

I think my first priority would be to recover the lost hard-disk spaces. The problem is that I do not know what tools to use and what do I need to do to the hard-disk to achieve that. 

You mentioned disk management program under Window. What is its name and how do I invoke it? Grateful if you would point me to to site which explain how to use the program? 

It would appear that during the Xbuntu installs, some hard-disk spaces were improperly written-over. So in my simple-minded way, I thought if I could only see the drives C: (or sda1 in Linux parlance) and D: (sda5 or similar) under Gparted, I could somehow try to expand their respective spaces to cover the whole 83G. Unfortunately, Gparted could not even find any device. So I am stumped. 

Any suggestion where I went astray?

Many thanks.

---

### Post by hyper_ch on 2008-05-06
(0) DO NOT TOUCH THAT HARDDISK ANY LONGER
(1) Get another harddisk that you can use to setup a system with
(2) ... (someone else has to help here)

---

### Post by NightwishFan on 2008-05-06
I have heard rumors that Wubi does not agree well with 98.

---

### Post by ambercomm on 2008-05-06
Hi All, 

Thank you for all your comments. Here are some further information which may help with the diagnosis.  

I am using the computer under window98 to write the replies under this thread. I have used Firefox, Thunder-Bird and MS-Word after the failed Xbuntu installs. So far I have not experienced any problem. So at least the hard disk spaces containing the Windows environment and its application softwares are OK.   

I can also see drives C: and D: under "My Computer". So I am puzzled why Gparted could not detect any of them. But then, it was the first time I used Gparted (or any disk partitioning program). After I booted with the Gparted live CD, I clicked on the Gparted icon when the X-window appeared. At the bottom left hand corner was a message saying that "no device detected". Have I missed some crucial steps here before Gparted would scan/rescan the hard-disk? As far as I could see, there was no obvious active "scan/rescan" button.  Any suggestion?

Hi hyper_ch, 

Good to hear from you again and thank you coming to my rescue once more. 

Would you please explain the purpose of using another hard-disk to set up a system? Are you worried that the existing hard-disk could die on me?  

Hi tjwoosta, 

Thank you for your suggestions. I too have a nagging suspicion that the GParted live CD is faulty (or I have missed an important step to activate the scan/rescan function) since it could not even detect drive C: which is quite clearly working properly. 

Hi NightwishFan, 

Thanks for the information. I wish I had known about this problem with Window98 before I even tried installing Xbuntu. 

Many thanks.

---

### Post by hyper_ch on 2008-05-06
As you have pointed out, there is/might be somthing wrong with your harddisk. So in order to save as much data as possible, you should not touch it anymore than necessary.

You know, everytime you access it, you could make things worse. Hence don't use it to make sure you can rescue most of the files on there.

---

### Post by ichbinesderelch on 2008-05-06
it looks to me like some troubles while partitioning the harddrives, if the hdd is really damaged there would be kinda troulbes when starting with win98, maybe you could try downloading and installing partition magic, or any other partitioning programm, under winxp there is, if you click the desktop icon and choose "mangement" or something like that in english, and in there should maybe be some tool named "disc management", i don't think it is tooo seriouse..

---

### Post by corowakid on 2008-05-06
> **ambercomm said:**
> Hi All, 

I am using the computer under window98 to write the replies under this thread. I have used Firefox, Thunder-Bird and MS-Word after the failed Xbuntu installs. So far I have not experienced any problem. So at least the hard disk spaces containing the Windows environment and its application softwares are OK.   

I can also see drives C: and D: under "My Computer". So I am puzzled why Gparted could not detect any of them. But then, it was the first time I used Gparted (or any disk partitioning program). After I booted with the Gparted live CD, I clicked on the Gparted icon when the X-window appeared. At the bottom left hand corner was a message saying that "no device detected". Have I missed some crucial steps here before Gparted would scan/rescan the hard-disk? As far as I could see, there was no obvious active "scan/rescan" button.  Any suggestion?

Many thanks.

If you can find someone else who is running Win98 you could ask them to make an Instal Disk, which will include utilities to get the machine running. One of the utilities is Fdisk, which is Windows 98's way of setting up partitions, both primary and logical. Using the floppy disk, start up the computer (you should check your BIOS settings to ensure the floppy disk is the 1st boot device). If you're not sure about the BIOS, find someone to help.

Using Fdisk will tell you how Windows sees your system, and is a way to delete partitions and establish new partitions - THE WINDOWS WAY!.

It might pay you to see if there's a support group that could help you - its not that hard, but it can be daunting for a first-time user. But this is the best way to see your Windows disk system, and make any changes you want.

---

### Post by ambercomm on 2008-05-06
Hi corowakid, ichbinesderelch and hyper_ch,

Wow, thank you so much for your very helpful advice and suggestions. I really appreciate it. 

I think I shall give corowakid's approach a try first. I shall report back on my progress. But please bear with me as this may take a while (a few days hopefully). Now, any suggestion on a good on-line support group for window98 OS? 

Cheers!

---

### Post by ambercomm on 2008-05-08
Hi All,

Here are further information on my progress so far.

I developed cold feet after I started reading about the Fdisk function under DOS ... it is a totally text based operation. So I booted the computer using a puppylinux 2.17 live CD and used the Gparted 0.3.3 included. 

After a minute or so of scanning, Gparted showed on that I had the following 7 items in my hard-disk. 

1) /dev/hda1; fat32; 4.01GB; used 3.98GB; unused 118.4M;falgs boot lba
2) /dev/hda2; extended;72.59GB; used -; unused -; flags: iba ;(There is a "lock" icon beside this item)
3) /dev/hda8; ext 3; 26.69G; used 2.08GB; unused 24.61GB
4) /dev/hda 9; linux swap; 721.64MB; used -;unused- ;(There is a "lock" icon beside this item)
5) /dev/hda5; fat32; 439.25MB;used 968.5K; unused 438.3MB;
6) /dev/hda6; unknown' 44.06G;used -; unused -; (there is an exclamation mark beside this item)
7) /dev/hda6; unknown' 721.64MB; used -; unused -; (there is an exclamation mark beside this item)

Clicking on items 1, 3 and 5, the "resize/move" button in the menu bar at the top of the screen was active. Clicking on 2,4,6 and 7, the "resize/move" button was inactive. 

However, the "Delete" button was active on all the items listed.

Now what is my best course of action to recover my hard-disk space? Should I delete items 2, 3, 4, 6 and 7 then expand the two remaining fat32 partitions?

Would appreciate your advice and comments.

Cheers!

---

