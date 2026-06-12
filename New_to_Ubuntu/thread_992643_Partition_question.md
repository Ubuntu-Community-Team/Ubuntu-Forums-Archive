---
title: "Partition question"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by SeePU on 2008-11-24
Hey, I have run into a partition/drive issue.

First of all, though, I have a question.

For those of you who have larger hard drives and dual/multi-boot, how large do you make your Windows partition and how large would you make Ubuntu?  

If you multi-boot with other versions/editions of Ubuntu and/or other distros, how large do you make those partitions?

I multi-boot and have most of my partitions around 20GB.  I also use a dedicated partition that is much smaller.  I have my main grub boot loader there with all the grub files.

The problem is that I forgot to create all the Primary partitions (i.e. four) first and I like to have my partitions listed (e.g. sda, sda2, sda3 etc.) in sequence.

If your HD is over 100GB (for e.g., between 250 and 500GB), how would you organize your disk?

I created three Primary partitions including one extended partition consisting of many logical partitions.  My Linux distros are in there.

The problem is that I only made two primary partitions for Windows and/or BSD operating systems so that when I try to add another partition, it gives the option of logical (if I use a Live CD with GParted) or primary.  Therefore, adding the last primary partition screws up my disk order.

I am assuming there's no way to add a partition where you want it?  That is, I would want it created before the extended partition (i.e. the Primary partition that I extended and created several logical partitions).  

I don't know how else to explain this.  Re-reading it now, I wonder if anyone is even going to reply/followup!!! LOL!

---

### Post by Olivier2371 on 2008-11-25
Don't worry there is always someone available.

Give me a minute to read it again.

---

### Post by jimreynold2nd on 2008-11-25
Look at my multiboot configuration...
Top down:
1. 30GB NTFS - Vista, preinstalled
2. 25GB NTFS - XP, I installed
3. 20GB HFS+ - Mac OSX Leopard, Kalyway
4. The little freespace dunno why Qtparted still includes here
5. The extended partition (because you can only have max of 4 primary partitions)
6. 1GB Ext2 - GrUB (with recovery tools like sysresccd, Paragon partition manager, GParted Live and other small live distros)
7. 2GB FAT32 - Backtrack3 (live, persistence)
8. 2GB FAT32 - Helix (live)
9. 20GB Ext3 - Ubuntu hardy
10. 20GB Ext3 - Kubuntu Intrepid
11. 15GB Ext3 - openSuSE 11.0 (I know - I should have given more to openSuSE)
12. 1GB Ext3 - dunno what to do yet.
13. 1GB Ext2 - full installation of Damn Small Linux
14. 1.9GB FAT32 - ReactOS (live, the full version wouldn't run on a logical partition)
15. 45GB NTFS - Data partition, to be shared among OSes
16. 4GB - Linux swap. (same as amount of RAM)

Total = 190GB

I have a separate HDD so I put all my data on that one (to speed up processing too, to have 2 different HDD spindles doing diffferent things at the same time; especially helpful **not **to put the virtual machine disk images on the same spidle with the OS). The Common partition acts as a temporary shared space.

---

### Post by Olivier2371 on 2008-11-25
to give you an example, I am dual booting vista with Ubuntu 8.04.
I have 120Gb hdd

Vista partitions takes 80 Gb
The rest is for Ubuntu.
My swap partition as the amount as my main memory.

---

### Post by jimreynold2nd on 2008-11-25
What I want you to see is Linuces use very little space compared to Windows. My XP installation is basic, with the OpenOffice, Firefox and SVG and PSpice for my class, all and other basic stuffs are portable programs put on "Common" aready and it took up 10GB. Things are even worst with Vista: Nothing in it, really, except for Office and it took up 20GB. Btw, Im using the ThinkPad T61, it doesn't have crapwares and I opted out for all the installation options when doing the last recovery already.

Ubuntu has everything I need for everyday use like Office, pidgin, amarok, DEFCON demo, Stepmania with lots of songs, Eclipse, I even have Mathematica (trial-forever :P), Vmware player, and it took up 6GB. Mathematica itself took up 1GB (!)

EDIT: If you really wanna use Windows then you should give it at least twice the amount of disk space than for a linux distro

---

### Post by Olivier2371 on 2008-11-25
My primary vista partition is 30GB
Second partition is 50GB(to share between vista and Ubuntu)
Ubuntu occupied 30GB

---

### Post by jimreynold2nd on 2008-11-25
Okay NOW I was able to read your question buried in your post (sorry!).
Yes you CAN... I'm not 100% sure that it won't screw up all your data tho. I did resize/move/add partitions many times with Paragon's softwares and they never failed me (yes I did at resized the logical partitions, pushed them to the end of the drive, resized the extended, then created one more primary partition, like what you would like to do, with paragon Partition Manager and all went smoothly). I never tried to use -parted's on a drive with data I don't wanna spend time to recover on lol.
Just remember that you can have maximum of 3 primary's and 1 extended.

---

### Post by SeePU on 2008-11-25
Thanks for the replies!

What my system looks like in GParted, for e.g., is:

sda1 - 20GB - Windows XP - NTFS - primary partition
sda2 - 20GB - Windows 2000 - NTFS - primary partition (reserved for BSD or any other Windows OS other than XP
sda3 - 100GB - Extended partition (primary partition)
sda5 - 8MB - Grub partition - ext2 - my dedicated grub partition 
sda6 - 4GB - Linux swap
sda7 - 20GB - Mepis 7 - ext3
sda8 - 20GB - Debian Testing/Lenny - ext3 
sda9 - 20GB - Kubuntu Hardy Heron 8.04 - ext3
sda10 - 20GB - sidux - ext3 
sda11 - 20GB - Fedora 9 - ext3
Unallocated space - approx. 160GB or so (i.e. the rest of the disk)

The issue is if I try to add another partition, to the extended, I can add another logical partition but if I add another primary partition, the primary partition will be sda4 but it will add it 'out of sequence.'  In other words, it will show up at the end so if the previous (logical) partition is sda12 (according to the above), the last primary partition available will be sda4 but will be listed after sda12.  If I was paying attention (!), I would have added the 4th primary partition after sda3 and sda3 would be another NTFS partition or partition reserved for whatever.   Then the fourth primary partition would be sda4 and it would become the extended partition.   

Does my explanation make sense?  It's not earth-shattering or a major problem, but it's annoying and doesn't look very organized.  

I am contemplating re-doing my entire disk as I'd like to install some (slightly) different distros.  I thought I might install both Ubuntu 8.10 and Kubuntu 8.10.  

I have a 'data' drive on the same computer so I'm not really worried about losing data.  I can burn the data files I want on the main partitions onto CD or DVD until I put them on the 'data' drive. 

Anyway, I was wondering what my options are and whether there is any way to re-organize the structure of the partitions so they show up how I want in GParted.

---

### Post by Moop on 2008-11-25
I wouldn't try moving all those partitions without backing them up first. If your going to back them up you might as well start over and get things how you want them. 

Why not create one extended partition and the rest logical. Do you really need that many primary partitions?

---

### Post by SeePU on 2008-11-25
Well, since you only get four primary partitions, I just create them and then use one of them to break down into logical partitions.  I install Linux in the logical partitions.  I reserve the primary partitions for Windows and BSD.   I am not a regular Windows user but it's still handy to have.   Other than using it for a BIOS update, I thought it's good for comparisons and anything that absolutely requires Windows (for those rare cases).  

I meant to set my drive up with the four but I forgot to create them all in order.  

I've been through so many various boot sequence setups and multi-boot setups,  I do think this is one of the best ways even though I didn't quite do it how I want 100% but it does work.

I totally encourage this setup:  create your primary partitions first including one that is split up.  The logical partitions created include one swap partition x2 the amount of RAM you have (old guideline) and a small partition in which you add grub files for a dedicated grub partition.  I haven't had any boot problems since.   

But, I am not really experienced with moving partitions around or restructing them if I want such drastic modifications.  I try to set up the drive/partitions so I don't have that potential concern.

---

### Post by bodhi.zazen on 2008-11-25
> **SeePU said:**
> <clip> ... Therefore, adding the last primary partition screws up my disk order. ,clip> ...

I make Linux partitions 10 Gb as my standard if I am going to use the install for any length of time, 5 gb for testing.

You can easily fix your partition order by the way with fdisk (this drives me nuts too, don't ask why):

Boot a live CD, 

```
sudo fdisk /dev/sdx
```where "sdx" is the disk you wish to fix (sda)
 
at the (first) menu type x (for expert menu) ; m to list commands
            
fix -> exit -> write changes to disk -> exit fdisk

Reboot.

---

### Post by jimreynold2nd on 2008-11-26
> **SeePU said:**
> The issue is if I try to add another partition, to the extended, I can add another logical partition but if I add another primary partition, the primary partition will be sda4 but it will add it 'out of sequence.'  In other words, it will show up at the end so if the previous (logical) partition is sda12 (according to the above), the last primary partition available will be sda4 but will be listed after sda12.  If I was paying attention (!), I would have added the 4th primary partition after sda3 and sda3 would be another NTFS partition or partition reserved for whatever.   Then the fourth primary partition would be sda4 and it would become the extended partition.   

Does my explanation make sense?  It's not earth-shattering or a major problem, but it's annoying and doesn't look very organized.  

You explained it perfectly fine. Well, having the last of the pimary partitions at the end of the drive is no big deal :). It just doesn't look as pretty. Don't worry having one primary partition at the end of the drive.

If you still want to insert the last primary partition between the second and the extended, then yes, it involves some partition shuffling and I wouldn't do that without backing up all data first. I remember GParted does have an option to resize/move partitions. You just need to boot off another media (i.e. grab some live distro with gparted or the [GParted LiveCD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779")) and do the resize and/or moving of partitions from there.

---

