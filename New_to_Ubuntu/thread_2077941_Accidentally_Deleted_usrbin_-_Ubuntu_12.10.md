---
title: "Accidentally Deleted /usr/bin - Ubuntu 12.10"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by AustenG on 2012-10-29
Hey, I made a huge mistake when I ran the command:
```
rm -r *
```in /usr/bin 
I've found a decent post ([http://askubuntu.com/questions/191942/deleted-all-the-files-in-usr-bin-typing-in-rm-rf](http://askubuntu.com/questions/191942/deleted-all-the-files-in-usr-bin-typing-in-rm-rf)) with a recovery strategy, but it requires dpkg to be installed. I downloaded the .deb file for dpkg, but this seems to be a recursive problem...I need dpkg to run .deb files. 

Does anyone have a solution to my problem?

Thanks!

---

### Post by Crafty Kisses on 2012-10-29
Grab a LiveCD, chroot into your install and reinstall all your (well most of your important packages) again. I think it would be faster to be honest.

---

### Post by Bashing-om on 2012-10-29
AustenG; Hi !

+1 to change root.
 Copy any important  files, and re-install.
Trying to rebuild a system directory would be a nightmare and time intensive. Even if I were to copy the entire directory from a working system ---many concerns would remain(sym links and hard links for one).

As an exercise for learning ...great opportunity! 

I can think of no course of action that I am sure would result in a trustworthy /bin/ directory.

In this instance I do endorse a re-install  

[INDENT]just in my opinion <==BDQ

[/INDENT]

---

### Post by twipley on 2012-10-29
> **AustenG said:**
> Does anyone have a solution to my problem?
Stop using the terminal. :P

---

### Post by AustenG on 2012-10-29
Thanks for the response guys! Alright, I'll give reinstallation from a live cd a go. Love all of the new stuff I'm learning, but sometimes it gets frustrating having to set up everything over and over again. 

Does anybody know if all of my stuff on my Ubuntu partition will be there? If I reinstall will I lose anything?

---

### Post by AustenG on 2012-10-29
No way I'll ever stop using the terminal - I'm both a scientist and a curious guy! That's no solution at all. Plus, I'm sure even the best of the best have done silly things like this before.

---

### Post by twipley on 2012-10-29
> **AustenG said:**
> Does anybody know if all of my stuff on my Ubuntu partition will be there? If I reinstall will I lose anything?

Personally, liking fresh installs, if I were you I would backup the stuff, and proceed with disk formatting. Here are some guidelines, which will perhaps orient some of your actions:

Extraneous file systems are not automatically mounted. An intuitive, graphical-interface method of mounting one is simply to press the folder icon in the launcher at the left, then left-click once on the device (e.g., 128 GB Volume).

Then, you can see it has been mounted by navigating to / (click on "file system" on the left bar of the file browser, which in fact is the LiveCD file system), then to /media. An "ubuntu" folder should now be present, which contains the mounted volume. This (/media/ubuntu) is the folder you might want to chown, chmod, or, for good measure, both.

```
chmod -R 777 /media/volume
```

Then, backup to desired device, and reinstall 12.10 afresh. Alternatively, do it like you are seeing or feeling it, by all means. ;)

> **AustenG said:**
> No way I'll ever stop using the terminal - I'm both a scientist and[QUOTE=AustenG;12325711]No way I'll ever stop using the terminal - I'm both a scientist and a curious guy! That's no solution at all. Plus, I'm sure even the best of the best have done silly things like this before.

 a curious guy! That's no solution at all. Plus, I'm sure even the best of the best have done silly things like this before.[/QUOTE]
Nothing beats the time I have locked myself out of the administrator account through the GUI. :)

EDIT: yeah you're right though... nice attitude of yours. ;)

---

### Post by Bashing-om on 2012-10-29
As to re-installing and not loosing anything ...not advising this course of action...but, I have re-installed on occasion and If I re-installed using the same username and password, and did NOT re-partition ; All my data and configs remained intact. [ I have been pleasantly surprised !]

I too am guilty of playing with it till it breaks, Try and try to fix it ...run out of time (need my system for a purpose)..or just my frustration level gets exceeded -->>re-install ! Yes I am guilty ( I learned to keep good backups, isolated from my operating system, nice safe and secure !) ...now, I have progressed to the point that with a live cd and my backup I can fix what ever I may have broke. And believe me, the more I learn about this system, the more I realize how little I actually do know. And I keep learning !

I say again..there is no substitute for a good backup !
[INDENT]imho ==> BDQ

[/INDENT]

---

### Post by AustenG on 2012-11-01
Okay, I've booted from a live cd. I'm currently backing everything up, but the next step I want to try before I have to re-install is to copy and paste the /usr/bin from the live cd to my partition. I know I won't get everything back that I had before, but I'll at least get apt, sudo, dpkg, and other important things that the os will definitely need.

Does anyone know how to do this? When I boot from a live cd, I can access the /usr/bin directory from a terminal. But, how do I copy and paste this to my /usr/bin on my Ubuntu partition? I'm guessing I have to mount the drive as rw.

---

### Post by AustenG on 2012-11-02
@CraftyKisses  -  Your original suggestion about chroot into my install: could you maybe give some specific instructions? This is my first time doing something like this.

If it helps, my ```
sudo fdisk -l
``` returns:

```

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99b3a87f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1048782847   524288000    7  HPFS/NTFS/exFAT
/dev/sda3      1048782848  1953523711   452370432    5  Extended
/dev/sda5      1048784896  1350365183   150790144   83  Linux
/dev/sda6      1350367232  1352464383     1048576   82  Linux swap / Solaris
/dev/sda7      1352466432  1953523711   300528640   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004571a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    c  W95 FAT32 (LBA)


```

---

### Post by oldfred on 2012-11-02
Chroot commands:

To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
This is for reinstalling grub2 but once chrooted you can run anything.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Have you tried copying files from liveCD. Not sure if anything will work except full reinstall. 
Do you have separate /home, if so then reinstall is a lot easier.

---

### Post by NikTh on 2012-11-02
Hi , 
I will suggest to re-install Ubuntu from a Live-CD. I saw (from the results of fdisk -l) that you have separate /home and /root partition . Am I correct ? I think your root partition is /dev/sda5 (judging by the size). 

A re-installation would be the easiest way (especially if I guessed correctly and you have separate /home and /root partitions) , but if you want to learn chroot , then proceed with above suggestions. 

Only thing you have to do is to select "something else" and mount the existing root partition to root. 

If you want to copy the /usr/bin from liveCD to your corrupted system then mount the system first 
I assume now that / root is /dev/sda5 
```
sudo mount /dev/sda5 /mnt
```and then use rsync (I think is the best command you can use) 
```
sudo rsync -avS /usr/bin /mnt/usr/
```Thanks

---

### Post by Bashing-om on 2012-11-02
Copying the /bin directory ..may work out just fine, nothing wrong in trying it..
gui method from the file manager nautilus might prove easier for you.
 Nautilus will mount the partition automatically. in nautilus open a second window, navigate to where you want to copy the directory to, and simply drag and drop the directory.

Alternate terminal method:
from the live cd->  terminal code:
```
 sudo mount /dev/sdXY /mnt
``` Where X is the hard drive and Y is the partition containing "/"
then use absolute paths and recursive copy to copy the /bin directory of the live cd to the /bin directory of your install..

```
cp -R /bin /sda5/bin
``` or sda7 as the case may be.
then unmount prior to rebooting
```
 sudo umount /mnt 
``` ???

let me reboot and verify my directions are correct. Back in a bit.[INDENT]try'n to help <== BDQ

NikTh beat me to it// pleas to advise the outcome !  -- rsync will be more dependable !

[/INDENT]

---

### Post by AustenG on 2012-11-17
I do have home and root as two separate partitions. I think I'm going to go with the re-install from live cd option. I'm not confident that I can get the other method to work. The only question I have now is how do I mount my home directory as read-write so I can copy my home folder over to an external harddrive before I re-install? 

Also, my home directory is sda7, and I believe it's located in /dev.

---

### Post by oldfred on 2012-11-18
This has all the commands spelled out as it is copy from an internal /home to a new partition.


It should be mount the new external location. Is it formatted and mounted already by nautilus?

You can use cp -a old new or rsync

       #Format new partition - only format if not already formated, sdXY is drive X partition Y like sdb2:
sudo mkfs -t ext4 /dev/sdXY
sudo mkdir /mnt/newhome
sudo mount /dev/sdXY /mnt/newhome
sudo cd /home
#copy everything in /fred (.) to newhome -a preserves ownership & permissions
sudo rsync -rauvP . /mnt/newhome


Full instructions on moving a  /home.


 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

