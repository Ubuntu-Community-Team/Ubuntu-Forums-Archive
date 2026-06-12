---
title: "Dual Boot with Windows"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by aravind4j on 2012-12-18
Hey,
I'm fairly *new to Linux*
I'm trying to install Windows in my Ubuntu 12.10 pc 
 but due to some problems, I'm not sure if the disc has errors or the system does not accept the installation . 
I've **tried booting and rebooting** after inserting the Windows 7 and Windows XP installation disc 
i don't know if its not **possible to install windows after installing linux** without formatting the data.
I'm clearly **not planning to erase the data in my HDD**
I've to partition the harddisk but i believe that comes after the booting , so i need help in these two processes 
I've **tried using wine** but it doesn't support many Windows games and i'm planning to play the latest ones and that is why i need to go through this hectic task 
kindly help !

- Thanks

---

### Post by fantab on 2012-12-18
First of all, you can install Windows after installing Ubuntu/Linux, but you will have to re-install GRUB [boot-loader] because Windows installation will wipe out Grub and install its own. Windows Boot-loader is inept to identify and boot Linux OS, AFAIK.

One more thing to keep in mind is that, Windows works best when installed on the first partition of the HDD... its my personal experience. There will be issues later if Windows is not installed on the first partition of the HDD. This first partition has to be PRIMARY only and it should have atleast 25% of free space after windows install.

With respect to WINE, not all Windows software/games work with it. Some do very well, some not so well and some just don't. Please see **[HERE]("http://appdb.winehq.org/")** for more details.

Lastly, You are not able to boot Windows probably because you don't have NTFS or Windows File system on your HDD. So, you may have to create NTFS partition on your HDD and preferably FIRST partition... 

Ideally I would recommend that you should re-partition your HDD accordingly using **[GPARTED LiveCD or LiveUSB]("http://gparted.sourceforge.net/livecd.php")**... and then re-install everything. Install Windows first and then Ubuntu. Remember to Back-Up all your important data first.

Hope that helps...
Good Luck...

---

### Post by audiomick on 2012-12-18
fantab is largely correct, but

It is not "works best". As far as I know, Windows *has* to be on the first partition. At least XP and Vista did. And it does have to be a primary partition.


You don't have to re-install ubuntu after re-installing Windows. Windows does overwrite the MBR, thus messing up your grub, but this can be fixed.

Read this, and follow the links on the page.
[https://help.ubuntu.com/community/DualBoot/WindowsLast]("https://help.ubuntu.com/community/DualBoot/WindowsLast")

Also
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I haven't read those exhaustively, but I think they are more or less saying the same thing in a slightly different way.

I believe it is correct that there has to be an existing partiton in a windows file format for the windows installer to see. I think that is also mentioned in one of those links.

A stand alone gparted cd or usb is good. If you have an Ubuntu CD or USB, gparted is on there too. You will need to do your partitioning from a live environment. You can't work on a partition that is mounted, so you can't change the partition that contains the system that the machine is booted to.


**BACK UP ANY IMPORTANT FILES YOU HAVE ON THE COMPUTER BEFORE YOU START DOING ANY PARTITIONING WORK**
The partition tools are good and reliable, the process is not hard, but you never know. Even if you do everything right and the tools work faultlessly, a power blackout during the process, for instance, can be disasterous.

If you don't have any routine for backing up, you should. Get an external drive, a large size USB stick, or some DVD's to burn the really important stuff to.

---

### Post by aravind4j on 2012-12-18
Thank you all for your support  =D> 

But i do not have a backup device as of now.
 In order to assign the **windows as primary** , does that mean to **reallocate & rearrange** the **data in my HDD** ? Is that why i have to back up ? Can i do this without backing up the data ? Is that a sure threat to the data ?
i understand the risk , though i'm not going to try I'm just curious so need to clarify  :-k
 
-Thanks :grin:

---

### Post by audiomick on 2012-12-18
> **aravind4j said:**
>  In order to assign the **windows as primary** , does that mean to **reallocate & rearrange** the **data in my HDD** ? 

Yes. Basically, you have to shrink the existing partition and create a new one in the resulting free space. That involves moving data from one part of the drive to another. I have done this a number of times without ever having had a problem, but there is a certain risk involved. As I mentioned, something unforseen like a power failure can cause havoc. I remember one thread from someone where the poster's younger sister turned off the machine whilst it was in the middle of re-partitioning...

You don't need to be scared of partitioning. It is not hard, really. The attendant risk is small, but it is there.

If you have nothing on the computer that you really can't afford to lose, then you might be prepared to just go ahead.

If, however, you have stuff on there that is really vital and only on that computer, you really should think about getting some way of backing it up. The hard drive on a computer is not a fail-safe place to have things stored. They all die eventually.

In one of those pages I linked to, I think there is mention of a virtual machine as an option. I don't know how well you can expect games to run in a virtual machine. It depends, amongst other things, on how powerful the computer is. The virtual machine shares the resources with the host system. If the computer is a bit older, and the games are resource intensive, it might be too slow. But if your are reluctant to attempt partitioning work, it might be an option. Installing a second OS in a virtual machine wont affect your current install.

---

### Post by verymadpip on 2012-12-18
I'm quite a fan of installing on separate HDDs personally.
Of course that can be problematic if using a laptop, or if finances are short etc.

---

### Post by Mark Phelps on 2012-12-18
Win7 does not HAVE to be the first partition on the drive, so to install it, you should boot from a LiveCD or LiveUSB of Ubuntu and use GParted to shrink down the Linux partition to leave room for Win7.  I would recommend a minimum of 40GB for Win7.

Also, you can use GParted to format the new partition as NTFS, but if you do that, use the option in Win7 to REFORMAT that same partition.  Win7 works best if it formats its partition.

After you install Win7, as mentioned, it will overwrite the MBR, so you will then have to reboot using the LiveCD or LiveUSB of Ubuntu and reinstall GRUB to the MBR.

---

### Post by audiomick on 2012-12-18
> **Mark Phelps said:**
> Win7 does not HAVE to be the first partition on the drive, 

Thanks Mark. I thought I might have heard that somewhere, but wasn't sure.

---

### Post by aravind4j on 2012-12-21
Thanks again friends :grin:

will do by partitioning ;-)

And i've tried the virtual machine too 

this is my system configuration :
  Core 2 Duo processor
  2GB DDR2 RAM
  500GB HDD
  1GB Nvidia 9400GT graphics card 

but , i don't think virtual machine will be capable of running games at a good rate :(

so , i'm trying PlayOnLinux now !! 

I haven't played any games using it but will try it and then will partition :P

Thanks a lot people :KS

---

