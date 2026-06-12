---
title: "Vista and Ubuntu"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by KingNick88 on 2008-05-12
Hello, recently I have installed Ubuntu 8.04. Me, being inexperienced, accidentally installed Ubuntu over Vista. Now I am having trouble putting Vista back on. I followed steps in this [tutorial]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")
 However, I got stuck on the part where I am to press Shift+F10. I press it and do what it says until it says select partition 3. On my screen, there is not a partition 3, only 0,1, and 2. 
Personally, I really love Ubuntu, and prefer it over Vista, but I will need Vista for my classes for college. Any help would be very appreciated.

---

### Post by shifty_powers on 2008-05-12
heh, tbh, the easiest way is to probably wipe the hd, install vista leaving sufficinet free unpartitioned space for ubuntu and the reinstall ubuntu... ;)

---

### Post by ethoxyethaan on 2008-05-12
can you post the output of 

```
sudo fdisk -l
```

from your terminal please.

---

### Post by hellomoto on 2008-05-12
got to agree with shifty_powers there.

your best bet is to wipe  your HD then make 2 partitions (one for Ubuntu one for vista) then install each on one of those partitions. For setting up Ubuntu i would recommend using the manual installation option.

---

### Post by KingNick88 on 2008-05-12
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1289       13995   102068977+  83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

---

### Post by ethoxyethaan on 2008-05-12
KingNick88
It looks like you did not create the NTFS partition yet with Gparted live cd.

Unless you installed Vista on the 320 gb disk (formatted as fat32) that seems to be a external or secondary drive?

where exactly did you install vista on?

---

### Post by hellomoto on 2008-05-12
so with your 120gb HD what i surgest is 60GB vista and 60GB for ubuntu.

I have a 120gb HD dual booting with the exact same size of drive.They way i set mine up was to first use the windows re installation CD (on the Xp installation disk it allows you to edit your partitions for the installation page).

1- Backup any work your want to keep onto a flash drive/DVD/CD

2- Put in your vista installation CD.

3- IN the partition manager screen tell it to delete any existing partitions.

4- Make 2 new partitions. (I suggest 60gb each). 

5- Install vista on one of the partitions. 

6- After you have installed vista, Restart the PC with your ubuntu live CD in.

7- go to install icon on desktop,

8- run through your install pages till you get to the Partition manager page.

9- Click on the option for manual installation.

10- select to install ubuntu on your free partition (it should say that you have a 60gb free partition.)

11- Select 59gb for the first part of your ubuntu install making sure the location is set to / and the type is Primary.

12 - Select your last 1 GB to be used as swap (this is incase your RAM becomes full.

13- install ubuntu.

14- restart the comp and you will now be able to dual boot to vista or ubuntu.


NB: with your other 320gb HD i would surgest using this as a second HD. this will allow windows AND ubuntu to access it to keep your files on. Make sure when setting up the other drive you do so from vista and that you format it using the NTFS file type. if you use ubuntu to format the drive and you save the type to ext3 windows won't be able to use it...

---

### Post by KingNick88 on 2008-05-12
I installed it on my internal drive. 120 GB I think.

---

### Post by hellomoto on 2008-05-12
i looked at the tutorial that you followed.

I have heard bad things about resizing partitions it can sometimes work others not. However I have never tryed myself so can't comment on its stability.

I would suggest a fresh install as its alot safer than resizing partitions and trying to cram windows in.

---

### Post by ethoxyethaan on 2008-05-12
[http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Ubuntu_first__images/ubuntu_vista_06.jpg](http://apcmag.com/images/apcapc/howto/Dualboot_-_Vista___Ubuntu__Ubuntu_first__images/ubuntu_vista_06.jpg)

in this image ^ it says partition 3 but you need to select the partition you installed vista on. according to your output it is the second partition in the list

partition X primary linux
partition Y primary vista 
partition Z extended (extended linux)
partition A swap (swap memory)

select partition Y.

also make sure you have a backup of all your files before you attempt to work on partitions.

---

### Post by 0ni on 2008-05-12
You can always use wubi to install linux "inside" your windows partition.

---

