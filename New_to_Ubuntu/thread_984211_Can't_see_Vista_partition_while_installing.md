---
title: "Can't see Vista partition while installing"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Ubunfu on 2008-11-16
Hi!  This is my virgin post, although I've been a lurker on the forums for a while.  Thanks to everyone for contributing so much to the forums.  Here's an issue that I keep bumping up against, and I just can't figure it out.  

I'm trying to setup a dual-boot with Vista and Ubuntu, with Vista pre-installed.  The main problem is that during Ubuntu setup, the partition editor sees the hard drive (/dev/sda) but doesn't recognize the Vista partition and instead sees the entire hard drive as unallocated space.  Since it can't see the partition, it only offers the "Guided - Use entire disk" and "Manual" options, the latter of which does not let me partition the disk (the buttons are grayed out).

Here's what I've tried:
1.  running chkdsk /f, with and without defrag afterwards
2.  running bootrec /fixmbr from Vista cd
3.  running fixmbr from recovery console off XP cd
4.  Pre-partitioning using Vista resize tool.  I shrank the Vista volume to free up 20gigs of unallocated space.  In addition to trying with the unallocated space, also tried pre-formatting it as FAT32 and NTFS.  
5.  Pre-partitioning using gParted live cd and Ubuntu disk manager off live cd.  For both of these applications, they still see the disk as entirely unallocated, with no indication of the Vista partition.
6.  Switching hard drive to ATA instead of ACPI

None of these attempts seem to fix the issue.  Here are my specs:

Dell XPS 1330
160gb SATA Hard Drive 7200rpm
T8300 2.4Ghz
X3100 Intel Graphics
Vista Home Premium 32-bit
Dell Wireless 1395 Card

I would love to get Ubuntu working alongside Vista so I can make the switch smoothly.  Thanks in advance!

---

### Post by mapes12 on 2008-11-16
If you can run GParted off a Live CD it should allow you to take a screen shot. If you can do this and post the screen shot on this thread I'll have a look for you.

---

### Post by Ubunfu on 2008-11-16
Thanks for the quick reply, mapes12!

SS is attached.  This is the same SS whether Vista partition takes up the entire hd, or a 20gig unallocated space has been pre-partitioned in vista.

Interesting note: When i'm in Ubuntu's live cd, I can mount and read the Vista NTFS partition.  Seems like partition editors just can't read it.

---

### Post by Patrick793 on 2008-11-16
Does it list any other drives in the drop down menu to the top right of gParted?

---

### Post by Ubunfu on 2008-11-16
Nope, only /dev/sda is listed.

---

### Post by mapes12 on 2008-11-16
> Pre-partitioning using Vista resize tool. I shrank the Vista volume to free up 20gigs of unallocated space. In addition to trying with the unallocated space, also tried pre-formatting it as FAT32 and NTFS.

I think this may be the problem. Your GParted SS is showing just under 11 GB of space compared to the HDD capacity. But this does not represent the pre formatting you have carried out. Additionally, you mention the word "volume". This is normally associated with Extended Partitions into which one inserts "Logical Volumes".

We can continue to work on this but it will need some MS tools via System Administration to have a look at the MS partitions. I can't recall the "run" commands as this is an Ubuntu machine only.

Question: How important is it to you that you retain Vista on your machine. Backup your stuff first. I would recommend imaging your Vista stuff with this: [http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)   the Private Edition is free. I've used it and can recommend it.

Then zap the drive with GParted or if that doesn't work a low level formatting application (I have one if required...PM me) then start from scratch.

---

### Post by Ubunfu on 2008-11-16
Hey Mapes12, I must've used the terms in the wrong way -- pretty sure that I shrank the vista partition (as opposed to volume), but I'll double check to make sure.

Ideally I would like to keep the vista installation intact, since I've already done multiple optimizations and tweaks to the OS.  My understanding is that Vista likes to hoard the MBR and mess with Grub loader, so wouldn't it be best to install Vista before Ubuntu if I'm aiming for a dual-boot setup?

If it would help, I'd be glad to post any screenshots from MS tools inside Vista.

---

### Post by Ubunfu on 2008-11-16
Here is SS of Disk Management Section of Administrative tools in Vista:

---

### Post by kansasnoob on 2008-11-16
With Vista you always want to use Vista's own tools to resize Vista! This should give you a general idea of what to do:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by InfectedWithDrew on 2008-11-16
> **Ubunfu said:**
> Here is SS of Disk Management Section of Administrative tools in Vista:

I notice how the hard drive shows the same size in Windows and Ubuntu; though you said it's 160 GB it's really 150 o.o

That means that that thing about 11GB missing isn't a problem of the Vista partitioning.

Now, in my experience of dual-booting, although Windows will make GRUB disappear, you can get GRUB back quite easily.  On the flip side, you already have Vista on there...

I don't want to chime in, but I must... just get rid of Vista (unless you're a gamer).

---

### Post by kansasnoob on 2008-11-16
I must also ask though, have you been able to run the Live CD?

---

### Post by caljohnsmith on 2008-11-16
Sometimes the Ubuntu installer doesn't recognize your partitions if your HDD's partition table is corrupt; it is possible to have a partially corrupt partition table and still boot Vista OK, so I would recommend checking your partition table to see if that is the problem. 

How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -l
```
Then make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen, and I can check it with your fdisk output to see if you have any partition table problems if you would like me to.

---

### Post by Ubunfu on 2008-11-16
InfectedWithDrew - Yes, I'm a gamer ;), but that's by chance -- I use my laptop for work and casual surfing.  Thing is, much of what I do at work relies on Windows, so I need that as a always-ready option.  I would like to migrate my daily life over to Ubuntu more as I learn more about linux, however.

Kansasnoob - yes, I've tried resizing with the Vista partitioner, and I can boot off the livecd.  No luck yet

caljohnsmith -- I'll run the tests and report back asap.

thanks so much for the replies, guys -- love these forums!

---

### Post by kansasnoob on 2008-11-16
> **Ubunfu said:**
> InfectedWithDrew - Yes, I'm a gamer ;), but that's by chance -- I use my laptop for work and casual surfing.  Thing is, much of what I do at work relies on Windows, so I need that as a always-ready option.  I would like to migrate my daily life over to Ubuntu more as I learn more about linux, however.

Kansasnoob - yes, I've tried resizing with the Vista partitioner, and I can boot off the livecd.  No luck yet

caljohnsmith -- I'll run the tests and report back asap.

thanks so much for the replies, guys -- love these forums!

You'll find no better help than that of Caljohnsmith! Seriously! Guaranteed!

---

### Post by Ubunfu on 2008-11-16
Here are fdisk results, and a couple testdisk screens.  I wasn't sure which testdisk screen result to look for, so I posted a couple:

---

### Post by Ubunfu on 2008-11-16
Did a deep search of the disk and came up with more results:

---

### Post by caljohnsmith on 2008-11-17
OK, I think I see what could be the problem; your Dell uses the newer GUID Partition Table (GPT) scheme on the drive instead of the older PC BIOS partition method that most computers have. From what I've read, Ubuntu's partition editor "gparted" is supposed to support GPT disk labels, so you might try running gparted directly:
```
gksudo gparted &
```
And see if gparted recognizes your Vista partition. Let me know what the results are. :)

---

### Post by Ubunfu on 2008-11-17
Interesting result with the terminal output when I start up gparted:

---

### Post by caljohnsmith on 2008-11-17
Yes, looks like you are having partition table problems, that error from gparted definitely gives a big clue; how about running testdisk again, but this time choose "No log", "Proceed", then "EFI GPT". Please post the output of the screen that follows.

---

### Post by Ubunfu on 2008-11-17
Will do.  Again, thanks a lot for all the help, caljohnsmith!

---

### Post by egalvan on 2008-11-17
> **kansasnoob said:**
> You'll find no better help than that of Caljohnsmith! Seriously! Guaranteed!

+1
+2
+3

Seriously!

He's helped me out of many a boot problem....

Definitely "The Man"

ErnestG

---

### Post by Ubunfu on 2008-11-17
Eeek!  Some serious errors in the partition table, looks like.  Isn't Mac HFS the partition system for OS X?

---

### Post by caljohnsmith on 2008-11-17
So you're sure you chose "EFI GPT" and not "MAC" in testdisk? If you did choose EFI GPT, it looks like you may have some serious partition problems; the GPT feature was just added to testdisk in the most recent version that you have, so there is a chance that it is buggy and the results you got aren't quite right. How about also posting:
```
sudo parted /dev/sda print
```
I should mention that I'm not very experienced with the new GPT scheme because my computer still uses the older PC BIOS partition method, but I'll do my best to help you if I can. :)

---

### Post by Ubunfu on 2008-11-17
Positive that I picked EFI -- ran it twice to make sure since I got suspicious about the Mac reference too :)

Attached are results of running the print command.  At this point, I'm seriously considering wiping the hard drive and starting from a clean slate.  I'm concerned that the reformat doesn't touch the GPT though -- is there a sure-fire way to restore the hard drive to a pristine state?

---

### Post by caljohnsmith on 2008-11-17
Do you have your Vista OEM CDs? Or a Vista Install CD? If you do, then I agree with your idea, probably reformatting the HDD would fix the problem. Do you have all your important files in Vista backed up? I think that would be a good thing to do if you haven't all ready done that. :)

But if you are going to reformat anyway, I think we should go ahead and give testdisk try to see if it can fix the partition table since you have nothing to lose by trying at this point. And the fact that you have only one partition should make the process easy; so how about in that last testdisk screen you posted where it says "use up/down arrow keys to select partition", go through and select each partition and press "P" to list the files. Once you find the partition that shows your Vista root directory, then mark that partition as "P" for primary partition and mark the rest of the partitions as deleted. Press "enter" to continue, and the next screen should give the choice to write the new partition table. Once you've written the partition table, reboot, run the "parted" command on the drive again and also testdisk; please let me know the results. :)

[COLOR="Red"]EDIT:[/COLOR] I think I agree with meierfra's post below that most likely your HDD didn't use GPT to begin with; that seems the most likely reason for your problem at this point. Please disregard the above suggestions for now.

---

### Post by meierfra. on 2008-11-17
I disagree with the latest suggestion from caljohnsmith. I believe that the partition table is essentially correct, only that is incorrectly labeled as EFI GPT , rather than MS-DOS.   All the programs which read the partition table as "MS-DOS" produce the exact same result: On partition of size 129.5GB. And  the programs trying to read it as an EFI GPT  produce useless output.

So I  suggest to not take any actions right now, until  somebody figures out how to change the wrong label.

---

### Post by caljohnsmith on 2008-11-17
We hope you haven't done anything drastic yet, Ubunfu; meierfra and I talked about it and thought it would be a good idea to first take a look at the sectors on your HDD that have the GPT information to try and get a better idea of what is going on. How about doing:
```
sudo dd if=/dev/sda count=60 | gzip -c > ~/Desktop/sda.bin.gz
```
And please attach the "sda.bin.gz" file from your desktop to your next post. I think at this point there no reason at all that you would need to reformat and reinstall, because I'm almost sure we can help you straighten out the problem with the help of testdisk and maybe some other tools. :)

---

### Post by Ubunfu on 2008-11-17
Hey guys!  Sorry for the late reply, been swamped with work all throughout the day.  I'll run the tests when I get home (hopefully in a couple hours) and report back.  Thanks again!

---

### Post by Ubunfu on 2008-11-17
Attached file.  Hope it helps!

---

### Post by Keen101 on 2008-11-17
I don't know if anyone has mentioned this, but gparted seems to be having a lot of trouble for many people when trying to change the partition. Most people recommend using vista's partitioner tool to empty some space, and then continuing the Ubuntu install.

---

### Post by meierfra. on 2008-11-17
The first sector of the file you posted looks like the regular Windows  MBR. After that comes some EFI-GPT stuff  which seem to cause your problems.   So caljohnsmith and I have agreed what it would be best to  just write zeroes over the EFU-GPT part.
We  did find another case, which looks very similar to yours,  where this approach  was used succesfully:[http://ubuntuforums.org/archive/index.php/t-562543.html]("http://ubuntuforums.org/archive/index.php/t-562543.html")

So try this:


```
sudo dd if=/dev/zero of=/dev/sda seek=1 count=59
```

(Be very careful with this command, use copy and paste)

Hopefully this is all it takes to fix your problem.

---

### Post by Ubunfu on 2008-11-18
Success!  Currently installing Ubuntu on the computer, have my fingers crossed that the rest of the installation goes smoothly.  Thank you so much, especially caljohnsmith for all your help!  I plan to continue lurking on the forums and hopefully one day helping other new linux adopters as well.  Again, thank you!

---

### Post by caljohnsmith on 2008-11-18
> **Ubunfu said:**
> Success!  Currently installing Ubuntu on the computer, have my fingers crossed that the rest of the installation goes smoothly.  Thank you so much, especially caljohnsmith for all your help!  I plan to continue lurking on the forums and hopefully one day helping other new linux adopters as well.  Again, thank you!
That's great news, Ubunfu; really all the credit goes to meierfra for having the stroke of insight that your HDD should probably not be using GPT in the first place. We're glad it turned out to be a simple solution.

Anyway, cheers and have fun with your new Ubuntu install; hopefully you won't run into any other major problems. :)

---

### Post by TheCl@ssic on 2009-02-20
I found this post while I was trying to figure out why I can't use GParted on my nearly new drive partitioned with vista. I was dinking around with the partitioning in vista and was switching between the different types (including GPT). Right now I'm using MBR, however GParted seems to think its GPT, probably because there are remnants of the GPT info. I'm using Gparted livecd 0.4.1-2. Since I don't have any data to lose, I'm just going to clean the partitioning information ([http://forums.techguy.org/hardware/786198-gpt-hard-drive-problems.html](http://forums.techguy.org/hardware/786198-gpt-hard-drive-problems.html)) and repartition.

---

