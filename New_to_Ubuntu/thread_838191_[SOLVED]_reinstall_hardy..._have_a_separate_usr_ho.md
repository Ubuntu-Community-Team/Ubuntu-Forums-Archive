---
title: "[SOLVED] reinstall hardy... have a separate /usr /home /boot partition"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by redtabulation on 2008-06-23
i want to reinstall ubuntu because i completely ****** the '/' partition i have /usr /home /boot on separate partitions from '/' .
When i tried the cd install when i say mount /home to the partition that is /home. the installer says it will format it. i mean the box is unchecked but when i click forward it says this msg. how do i save my data???

---

### Post by dracayr on 2008-06-23
are you sure you want an extra partition for /boot ??

---

### Post by bodhi.zazen on 2008-06-23
Depends on how exactly your partitions are set up.

Most distros will format and overwrite /boot and /var and justa about any partition but /home.

Just a guess , but are /boot , /home , and /var all on the same partition ?

FYI: IMO you do not need a /home, rather a /data partition. No need to back up all those . files in /home, just the improtant ones like .bashrdc and .vimrc :lolflag:

---

### Post by hyper_ch on 2008-06-23
if you use the alternate install cd and then go to manual partitioning you can select on each partition where it shold be mounted and also whether it shall be overwritten...

---

### Post by redtabulation on 2008-06-23
Alternate install cd???
and when i go through the normal cd, when i set the mount points on them it then click forward, it gives a warning message that all conflicting os data will be removed. clicked continue and it was remove. 
anyway i had the data backed up (used puppylinux 4.0) so i logged in as root and manually copied it to /usr  and /home , got the data back for the session i.e the games and everything but when i restarted the system crashed must have something to do with permissions because when i tried ctrl+alt+F1 and them did any sudo it said permission denied. I tried to change the ownership on all the folders and subfolders of usr but no luck.
I will format and reinstall but is there any way i can make this work. i mean i have the data and its frustrating not to be able to use it. 
You see i am on dial up and it will take a long time to get it all back.

PS if nothing comes of this i am going to download individual .deb packages and back em up.

@dracayr: i have a boot partition because if i mess up then grub is still safe and atleast i can boot into windows. the partition is small 40mb.

---

### Post by Rocket2DMn on 2008-06-23
If you copied the files to a disk that is NTFS or FAT32 (or something else that doesn't use linux filesystem permissions), then it is most likely breaking because the permissions on files were not preserved when you backed them up.

Using the Alternate CD as mentioned before will give you more flexibility with your partition management.

You don't need a separate /boot partition in case you screw up GRUB or need to boot into windows.  You can always reinstall GRUB or use a Windows install cd to enter the recovery console and run "fixmbr" to restore windows to the MBR (and kicking out GRUB).  That will disable your dual boot until you reinstall GRUB, see here - [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp]

---

### Post by redtabulation on 2008-06-23
yes you are right . i did it to a fat32 partition, when i had 37 gb free in an ext3 one. I sure feel like banging my head against the wall. so now i have useless data in a fat32 part. Next time i'll be more careful.
And i am beginner level so i cant really go fixing things if sumthing goes wrong with boot. Doesnt hurt to have a separate boot part does it...???

---

### Post by Duck2006 on 2008-06-23
> **redtabulation said:**
> yes you are right . i did it to a fat32 partition, when i had 37 gb free in an ext3 one. I sure feel like banging my head against the wall. so now i have useless data in a fat32 part. Next time i'll be more careful.
And i am beginner level so i cant really go fixing things if sumthing goes wrong with boot. Doesnt hurt to have a separate boot part does it...???

No it don't. It will be very small round 200Mb at the start of the disk. You will have to install grub to it and then install grub in to the mbr so it point to the boot partition. Edit your menu.lst in there so it will point to your OS's on your drive/s.

---

### Post by Rocket2DMn on 2008-06-23
You can use FAT32 partitions in Ubuntu if that is where you store data, you just have to have the correct mount options - this is easier to do after you install, though from the LiveCD, you CAN mount it with something like:
```
sudo mkdir /media/fat32
sudo mount -t vfat /dev/sda1 /meda/fat32 -o defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```
Then you can access the drive from /media/fat32

---

