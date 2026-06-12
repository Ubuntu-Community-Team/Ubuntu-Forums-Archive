---
title: "Can't Boot Ubuntu 12.10 after software updates"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by E-Tramp on 2013-01-23
Alright, guys I have a major problem.  I was in my Ubuntu 12.10 program this morning trying to get my Deluge program to work right and the OS flagged me with some software updates.

I went ahead and let the installer install them and thought that maybe something might not be right with it because the night before the system wanted to update and I started to let them but because it was going to be longer than I had thought to do, I cancelled it early and did what I was doing and shut down.  I did notice that the installer showed a progress bar for all of the packages it did download last night, and this morning it wasn't showing the individual package download bars like it was suppose to.  I figured it might be a glitch in the program that wouldn't be a problem however once the software updates had finished, I went back to trying to get my torrent downloaders working in both Ubuntu and Knoppix and when I went to boot back into Ubuntu the boot screen showed the boot process seems to be locked in a loop of failed functions.

Am I going to have to reinsall this program to get it running again? It is just repeating the same process over and over again and failing at whatever it is trying to do.

These are the messages I am getting.  I get four lines of the following, 
"[10.9769]nouveau 0000:03:00.0 evoch1 mthd 0x0080 Data 0x00000000(0x00060x05)"
2 for ch1 and 2 for ch2, then unlimited lines of the following, each line a different number:

"[335.441791][drm] 0000:030:00.0 failed to idle channel 1"

one for each channel.

Anybody know what this is all about????

---

### Post by oldfred on 2013-01-24
It seems like you shutdown while it is working, that almost always corrupts file system and my may also have to do something with dpkg.

       #From liveCD so everything is unmounted,swap off if necessary, 

change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
If you can get to a terminal with recovery mode.

       # fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by E-Tramp on 2013-01-25
Well, first of all I didn't shut it down while it was working I canceled the download before all of the programming was done downloading, and the installer installed what it had downloaded and then canceled the rest until a later date.  There is nothing I did that should have damaged the program, it didn't start malfunctioning until the system had updated.  That doesn't mean there wasn't a glitch in the downloader/installer.

As for the rest, you will have to explain to me what dpkg is.  Is that the boot repair disk?  I have two of those I haven't tried yet. If not what is it?  

And my partition is sdb2 so your example isn't far off.  For some reason linux wants to identify my GPT drive as the 'a'drive, instead of my boot drive.

---

### Post by oldfred on 2013-01-25
You can post the link to the BootInfo report, but it will only show boot issues mostly with grub or changing some grub settings. It will hightlight if a partition cannot be mounted and may run fsck.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by E-Tramp on 2013-01-25
OK, Well I ran Boot Repair and here is the URL.
[http://paste.ubuntu.com/1570494](http://paste.ubuntu.com/1570494)

I looked at it and What I see is grubs on all three drives, and a couple of drives that may need to be repartitioned only one of which is a partition I am getting errors on in Knoppix.

I also ran the boot disk repair and it made no improvement in how well Ubuntu booted up. It doesn't seem to do any inspecting of the OS itself, which is where the problem is.

The grub seems to be fine, and booting into Knoppix is fine.  The only problem with Knoppix is a couple of partition errors on my GPT drive, only one of which is the same as a partition in the boot repair print out.

I will probably re-partition them later. I would also like to get rid of all of the extra grub installs.  I don't see why those are even there.  Maybe you can explain that.

I did manage to boot into Ubuntu on about the third or fourth try this morning.  If I persist, it will boot sometimes, but I also get errors and questions about whether I am willing to do some development aid.

So how am I going to repair this install, and if I update the software the software on a new install is it going to do the samething again?

---

### Post by oldfred on 2013-01-25
If you look at the typical grub2 boot stanza it uses both a set root & the search by UUID. Actually either one should work, but the UUID is more often used as drives can change order, my flash drive sometimes is sdc or sdf and then sdc & sde get reordered.

But you have a reiserfs and perhaps since grub has not loaded that driver has issues doing the search by UUID. You might try just comment that out to see if it works (as long as BIOS orders drives the same each time). Your set root line should then work.

---

### Post by E-Tramp on 2013-01-30
Actually my BIOS doesn't order the partitions the same each time.  In my first installation I had a lot of trouble with my drives changing and had to manually go into the Legacy Grub and physically change the drive designation when I installed Knoppix.  If I installed it with my secondary and terciary drives connected I couldn't get it to boot.  When I installed it with the drives disconnected and reconnected them the boot grub couldn't find the Knoppix install, and I had to alter the drive direction to the correct drive partition.  That is probably why there are more than one grub on the drives I have.  I don't even know which grub of the two grub2 installations is the one the system boots from, now.  The legacy grub is of course from the Knoppix install and isn't being used anymore.  Don't really know how to remove them so they are still there.

I don't suppose I could repair the errors in the Ubuntu partitions using the repair you describe above using #e2fsck in the Knoppix program?  Does it work the same in Debian? I kind of would like to get this boot problem resolved, so I can boot into Ubuntu whenever I want instead of just when the program wants to bypass the errors enough to boot it up and boot it up without errors when it does.

---

### Post by oldfred on 2013-01-30
I missed this the first time from your 3TB drive. 

I would see if gdisk will let you fix this or you may just have to delete sda4.

> /dev/sda1 overlaps with /dev/sda4 
/dev/sda2 overlaps with /dev/sda4      GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by E-Tramp on 2013-01-31
I tried using Gdisk to repartition some of the partitions on the GPT drive, but, am unable to get Knoppix to show it without errors.  The problem is that it says that the sda1 is 3072 bytes misaligned, and that partition sda3 is unreadable and connot be accessed.  Ubuntu doesn't seem to have any problem with it but, something is definitely wrong with it.  The problem is I have a lot of data on them and I really don't have any place else to put it for now.  If I did I would redo all of the partitions and see if that fixed it, if it doesn't then I think that Linux may just not like the GPT technology, and needs to work on the way it sees it.

For now it will just have to do for what I use it for, and that is data storage.  I don't really see how sda1 and sda2 can possibly overlap sda4 when sda3 is 700 plus gigs of space between them and it.  I don't think that is even possible, is it?

That really makes me think that Linux just doesn't like GPT technology yet. And just for the record I have repartitioned both sda1 and sda3 with Gdisk and Alinged them with the cylinders and it didn't help the errors in Knoppix at all.  No matter how small I make the sda1 partition, or how I align it, it still shows the partition as 3072 bytes misaligned.  If I could do the whole disk I would, but, until I move some data somewhere else I can't do that.  I don't have enough room on the 500 gig drive for it.

However this thread is about the sdb drive that has my OS's on it, and getting the Ubuntu program to work right.  The GPT drive will just have to wait for now.

---

### Post by oldfred on 2013-02-01
Did you try commenting out the search function when at the grub menu just as a test to see it that makes a difference? use e on grub menu.

I still think it is somehow related to reiser file system.

You cannot have sda4 start in the middle of sda1 and end in the middle of sda2. gdisk and now gparted all want the start of all partitions to be divisible by 8 for good alignment.

---

