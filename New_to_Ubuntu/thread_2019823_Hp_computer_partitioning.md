---
title: "Hp computer partitioning"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by andrewnelson23 on 2012-07-07
Hi,
I'm coming from the Android scene, and I simply love Android. I thought I might try out Ubuntu! So I tried it out using the flash drive option and I LOVE IT. So, I decided, why not dual boot Ubuntu alongside my windows?

So I read up on it, found my partitions and such and found out that they're all used up. I have a compaq computer, and all of the drives are used up by C:, hptools, recovery, and system.

I read up and did some searching, and foudn what sounds like the best option to fix partitions.  I just need some help.

I'm using this quote:
_________________________________________
Re: Deleting HP-Tools window partition?
On my HP Mini 210 I:
1. Saved the folder in the HP-Tools partition
2. Used the Win 7 tools to delete the HP-Tools partition
3. Used the Win 7 tools to shrink the C: drive and create unallocated space (DO NOT use the Win 7 tools to create a new partition)
4. Used gparted to create an extended partition in the newly unallocated space and created an EXT 4 logical partition, a Linux Swap logical partition, and a 100mb Fat 32 logical partition.
5. Copied the folder saved from the HP-Tools partition to the new Fat32 logical partition.
6. Installed Ubuntu in the EXT 4 logical partition.
________________________________________

Here's my questions.

1. Where am I supposed to save the HPtools partition? A cd? If so, I'm kinda nooby, so can I get instructions on how to do that? :)
2. What is the Linux Swap logical partition for?
3. I've seen that it's possible to share data between windows and Ubuntu. I'm guessing it would take another logical partition.  What would that be?

I hope y'all can help.

---

### Post by Perfect Storm on 2012-07-07
Welcome to UF :)
If you're using Mint, you may try the Mint forum at [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


Moved to Other OS/Distro Talk.

---

### Post by andrewnelson23 on 2012-07-07
> **Artificial Intelligence said:**
> Welcome to UF :)
If you're using Mint, you may try the Mint forum at [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


Moved to Other OS/Distro Talk.

I'm not using linux mint. that was a quote. I'm have 12.04.

---

### Post by andrewnelson23 on 2012-07-07
how do I get rid of that linux mint tag? I don't need that.  That'll limit my help sources.

---

### Post by Perfect Storm on 2012-07-07
> **andrewnelson23 said:**
> I'm not using linux mint. that was a quote. I'm have 12.04.

I can see you have edited your original post, which stated it. If it was rephrased wrongly let me know, then I'll move your thread back.

---

### Post by andrewnelson23 on 2012-07-07
> **Artificial Intelligence said:**
> I can see you have edited your original post, which stated it. If it was rephrased wrongly let me know, then I'll move your thread back.

It was. I'm using Ubuntu.  I searched the forums and found a quote from @Jerry N and just copied it.  He was using Linux mint, but I'm using Ubuntu. Sorry about the confusion.

---

### Post by Perfect Storm on 2012-07-07
> **andrewnelson23 said:**
> It was. I'm using Ubuntu.  I searched the forums and found a quote from @Jerry N and just copied it.  He was using Linux mint, but I'm using Ubuntu. Sorry about the confusion.

Thread moved back.
No problem :popcorn:

---

### Post by OM55 on 2012-07-07
Hi,

You don't need any additional software in order to install Ubuntu 12.04 as a dual boot with any other OS. The Ubuntu 12.04 installer will do it all by itself. During installation it will ask you for your preference: replace existing OS, upgrade to 12.04 or install as dual boot. If you do not have sufficient unallocated partition space or if you want to control the partition set up manually, the Ubuntu Installer will give you that option as well.

However, if you prefer to custom set your hard-disk partitions before starting the Ubuntu 12.04 installation, you can use GParted Live ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)). GParted is a Linux based partition editor. However, since you don't yet have Ubuntu installed, you can use it's 'live' version (GParted Live) that is installed on a bootable USB stick or on a CD drive. Then you can resize/delete partitions on your hard drive to make room for the Ubuntu partition installation.

You mentioned that one of your partitions is the recovery partition. This partition is used to restore your drive to its factory setting (usually by booting from this partition). If you backup your drive regularly or if you have already created a CD/DVD copy of the recovery software, you will no longer need it. So if there is no other space available, you can remove this partition and this way have the additional space needed for the Ubuntu installation.

Hope that helps!

---

### Post by andrewnelson23 on 2012-07-07
I have no unallocated space.  

First, I think I want to copy the recovery to a cd/dvd or a usb flashdrive with at least 32 gigs.  What kinda disk would I need for this? Can I just go to walmart and get one and how much are they? Then, how do I copy the software onto the cd/dvd?

Second, I will want to shrink my C: drive in order to get unallocated space. I will do this in windows partition manager.

Third, I will delete the recovery partition from the windows partition manager.

Fourth, I will boot into Ubuntu live(on the usb stick) and use gparted to create an extended partition.

Within that partition I will create four logical partitions: a boot partition, a root partition, a home partition and and swap partition.

Would I need to create another logical partition in order to share data between Ubuntu and Windows?  For instance, if I want all of my bookmarks on google chrome that I have in Windows to be on Ubuntu, would I need to put that data in another logical partition?

After this, I want to install Ubuntu 12.04 on the boot partition, correct?

Then I can use EasyBCD in order to be able to choose which OS to run every time I boot.

Is that all correct?

OR would it be better not to mess with the recovery?  Then I could just remove hptools. Would that be better?

---

### Post by andrewnelson23 on 2012-07-07
I actually just realized that maybe it would be easier to just remove hptools. It's a much smaller file size, so I could just put it on a flash drive that I already have here at home. How would I go about copying that to my flash drive?

Then I could just move remove the hptools partition, shrink the c: drive, create an extended partition, etc.

---

### Post by garyed on 2012-07-07
I have a compaq & had the same exact problem when I bought mine.
Since they use up all four primary partitions I had to delete one before I could partition my disk to install Ubuntu. What I did was make a complete set of recovery disks in case I screwed up so I could put everything back the way it was. If I remember it right I then shrunk the largest partition using Windows 7 & then deleted the HP Tools partition. Then I used a Gparted live disk to add an extended partition to the unallocated space.
Then add an ext4 partition for my new Ubuntu install. You always have to be careful working with partitions because its easy to overwrite one by mistake. The key word is "backup" first.
Good luck

---

### Post by andrewnelson23 on 2012-07-07
> **garyed said:**
> I have a compaq & had the same exact problem when I bought mine.
Since they use up all four primary partitions I had to delete one before I could partition my disk to install Ubuntu. What I did was make a complete set of recovery disks in case I screwed up so I could put everything back the way it was. If I remember it right I then shrunk the largest partition using Windows 7 & then deleted the HP Tools partition. Then I used a Gparted live disk to add an extended partition to the unallocated space.
Then add an ext4 partition for my new Ubuntu install. You always have to be careful working with partitions because its easy to overwrite one by mistake. The key word is "backup" first.
Good luck

Hey thanks for the reply.

I'm not really sure how to backup anything.  I don't have any backup cd's or anything like that. I have flash drives.  Would that work?

I'm sorry, I'm pretty new to the OS scene.

---

### Post by OM55 on 2012-07-07
If you have a "recover/restore" partition on your hard-drive, this is usually a vendor created partition that is intended for restoration of the hard-drive back to its original factory setup. This is usually done either by using a small software supplied by that vendor (on CD) or by booting directly from that partition instead of the regular one.
However, if you already have regular backups and/or can backup that partition (you can backup/restore a partition using Image for Linux: [http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm)) and/or do not need any longer the option of restoring the hard-drive to its original factory setup, than you can remove this partition and free up the space you need to for installing Ubuntu.

There are two ways to achieve that:

1. The Ubuntu 12.04 installer gives you an option to manually edit the partitions before installation. This will allow you to remove the partition you no longer need and than continue with the installation. However, this is not that straight forward and you need to know what you are doing. I would recommend to go with the second option below.

2. Use "GParted Live", which is the live version of GParted (installed on a bootable CD or a bootable USB key). GParted is a Linux based graphical partition editor (You can find GParted at: [http://gparted.sourceforge.net](http://gparted.sourceforge.net)).
Once you boot with GParted Live you will see all partitions on the hard drive. Just delete the one you want, save and reboot using the Ubuntu 12.04 live CD or USB. Then proceed with the automatic Ubuntu installation. The Ubuntu installer will automatically use the newly available space on the hard drive with no user intervention.

During installation you will be given several options to install - select "Side by side with the other OS" option. As a result, the installer will also create an initial menu (Grub) that will come up first showing the available operating systems on the hard-drive so you can select from them. The default setting will have the new Ubuntu 12.04 as option #1 and the other operating system(s) as option #2 (and more, of there are more OSs). If there is no user keyboard input, within 10 seconds it will automatically continue to boot to Ubuntu 12.04.

This Grub menu setup can be changed later on to your liking, but this is an issue for a post/reply :)

Hope that helps.

---

### Post by garyed on 2012-07-08
> **andrewnelson23 said:**
> Hey thanks for the reply.

I'm not really sure how to backup anything.  I don't have any backup cd's or anything like that. I have flash drives.  Would that work?

I'm sorry, I'm pretty new to the OS scene.

Flash drives should work just fine.
Open the recovery manager under all programs & look for something like Recovery media creation. Its always a good idea to have the physical backup media in case of an emergency. I would not depend on the recovery partition to restore your computer once you change the partitions.

---

### Post by jsthrower on 2012-07-08
So how big is your hard drive? The recovery partition normally isn't that large and I'd leave it unless you really have limited drive space. Is the HP Tools partition the same as your recovery partition or is it an additional partition. My hp computers normally had a recovery partition around 10 gig..and the windows partition...On larger hard drives sometimes they would make a second partition for whatever reason...I don't recall ever seeing four partitions on a new machine. 

My netbook has a recovery partition..the c (windows 7) partition on a 250 gig drive. I used windows to free up 60 gig of unallocated space then let ubuntu install itself with the usb drive installer. That seems to be plenty of room since I can access all my windows partition and files thru ubuntu.

---

