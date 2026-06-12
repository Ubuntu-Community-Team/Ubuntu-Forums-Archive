---
title: "Why partition options during 11.10 install make all the partitions NTFS &amp; no ext3?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by swarup on 2012-01-03
I just purchased the following netbook:

Samsung N150 Plus 1.66GHz 250GB 10.1-inch Netbook (Refurbished)

It comes with Win7 Starter, and I am in the middle of installing 11.10 as a dual boot. So at the window asking whether to replace Win7, I opted instead for the partition editor. And the default settings that then appear, divide the HDD into four partitions all of type NTFS, with respective sizes sda1 (Windows Recovery Environment loader) 16 GB, sda2 (Win7 loader) 104 MB, sda3 104 GB, sda4 128 GB. So which partition is it setting as the Ubuntu partition, and why isn't it designating it as type ext3 or ext4?

---

### Post by mcduck on 2012-01-03
You have to decide yourself which partition to use for what purpose, the manual partitioner asks you to set the mount point for partitions so the one with mount point set to "/" would be your system partition.

Same goes for the filesystem, just choose the one you want to use. I have no idea why it would default to NTFS on your system (unless it's an existing NTFS partition and you didn't check the box to format the partition...), it most certainly offered Ext4 as default for me.

edit: Unless you actually already edited the partition layout yourself, the partitions you see would be ones *already existing on your computer*. The manual partitioner doesn't give you any kind of suggested setup, it really is manual and the only changes it does are the ones you do yourself.

---

### Post by critin on 2012-01-03
Because Windows uses NTFS.  You need to choose which partition to put ubuntu on and choose to format it ext4.   Ubuntu will format it during installation process.  Be very sure of your partition or you will lose Windows.  Read some tutorials or wait for some partition experts to post.


> And the default settings that then appear, divide the HDD into four  partitions all of type NTFS, with respective sizes sda1 16 GB, sda2 104  MB, sda3 104 GB, sda4 128 GB. So which partition is it setting as the  Ubuntu partition, 

These are partitions that your current OS is using.  MBR, System, files, recovery?

---

### Post by Morbius1 on 2012-01-03
If you notice all the ntfs partitions are in order: sda1, 2, 3, and sda4. Looks to me that the current Win7 install has used up all of the primary partitions. No more partitions are possible unless one of them is removed and converted to an extended partition. Then Linux has a place to create a / and swap as logical partitions.

What's in sda3 and sda4?

---

### Post by swarup on 2012-01-03
> **mcduck said:**
> edit: Unless you actually already edited the partition layout yourself, the partitions you see would be ones *already existing on your computer*. The manual partitioner doesn't give you any kind of suggested setup, it really is manual and the only changes it does are the ones you do yourself.

I am quite surprised to hear this, as I have installed Ubuntu on my systems with pre-existing windows for dual boot, and when I select to install Ubuntu and Windows side by side, it always used to give me a suggested setup showing the existing Win partitions and an ext3 for Ubuntu--with the option to accept the default sizes or change the sizes as desired.

And indeed, the partition editor screen it shows me this time too, does look as if it had given such a suggestion with the option to accept and just click on "continue", or change as desired. The only strange thing is that all four partitions are of type NTFS. And I am guessing sda1, sda2, and sda3 are the three windows partitions with sda4 being set to be created as the Ubuntu partion. But currently, it the default setup designated it as type NTFS--which made me suspect that it might be offering to perhaps install Ubuntu on an NTFS partition?

---

### Post by swarup on 2012-01-03
> **Morbius1 said:**
> If you notice all the ntfs partitions are in order: sda1, 2, 3, and sda4. Looks to me that the current Win7 install has used up all of the primary partitions. No more partitions are possible unless one of them is removed and converted to an extended partition. Then Linux has a place to create a / and swap as logical partitions.

What's in sda3 and sda4?

sda1 and sda2 are labelled as I indicated in my first post:

> sda1 (Windows Recovery Environment loader) 16 GB, sda2 (Win7 loader) 104 MB, sda3 104 GB, sda4 128 GB

sda3 and sda4 are not labelled as to what they are. Since sda1 and sda2 are windows partitions, I am guessing sda3 is what gparted is making the actual windows partition for my data. And sda4 is what I am guessing gparted is suggesting to be the new partition to be created for installing Ubuntu on. What confuses me is why it is set as type NTFS.

---

### Post by Elfy on 2012-01-03
It'll not be suggesting that it installs to that partition. You can't install ubuntu on an ntfs partition - that is what you have already. 

There are many threads here about similar. 

At a guess the 16Gb partition is the one it would restore from, the second the bootloader partition. The other 2 would be ones you'll see from inside windows.

I would boot windows - check in it's disk management tool to see them.

You'll want to do the disk work inside w7 anyway - it can cause issues if you don't - there are many of those threads here too.

You could if you wanted use the bootinfo script to see what is there.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by critin on 2012-01-03
> So at the window asking whether to replace Win7, I opted instead for the partition editor. ----
-*-----(Previous installs)---* when I select to install Ubuntu and Windows side by side,

So this time it didn't give the option to install side-by-side?

---

### Post by Jerry N on 2012-01-03
forestpiske:  Just a thought but maybe there should be a "sticky" that explains the situation and the solutions for computers that already have all 4 partitions in use. This could include some details and precautions about using the Win 7 tools to shrink existing NTFS partitions.

Jerry

---

### Post by I_can_see_the_light on 2012-01-03
> **Jerry N said:**
> forestpiske:  Just a thought but maybe there should be a "sticky" that explains the situation and the solutions for computers that already have all 4 partitions in use. **This could include some details and precautions about using the Win 7 tools to shrink existing NTFS partitions.**

Jerry

I'll second that!

---

### Post by mcduck on 2012-01-03
> **swarup said:**
> I am quite surprised to hear this, as I have installed Ubuntu on my systems with pre-existing windows for dual boot, and when I select to install Ubuntu and Windows side by side, it always used to give me a suggested setup showing the existing Win partitions and an ext3 for Ubuntu--with the option to accept the default sizes or change the sizes as desired.

And indeed, the partition editor screen it shows me this time too, does look as if it had given such a suggestion with the option to accept and just click on "continue", or change as desired. The only strange thing is that all four partitions are of type NTFS. And I am guessing sda1, sda2, and sda3 are the three windows partitions with sda4 being set to be created as the Ubuntu partion. But currently, it the default setup designated it as type NTFS--which made me suspect that it might be offering to perhaps install Ubuntu on an NTFS partition?
Did you use one of the automatic install options or the manual partitioning option?

The automatic ones will give you suggestions and such, manual option is exactly what it says, manual. It's been this way as long as I've used Ubuntu...

If it's the manual partitioning you are using, then all the partitions you see when the partitioning screen opens are pre-existing ones. And it's quite unlikely the installer would ever suggest using NFTS partition for your Ubuntu install, considering that wouldn't actually even work since NTFS lacks support for POSIX permissions... ;)

Also since the manual partitioning option assumes you know what you are doing, it *will* allow you to continue at any point. It will however give you an error message if you try to continue without defining a root partition, but that's pretty much as far as it could possibly do to make sure you've set things up correctly, as it really is intended for custom setups and could not possibly know what kind of setup you want.

Anyway, it really sounds to me like you are just looking at the four partitions that already exist on your computer. In which case Morbius1 is correct and you'll have to delete one of the existing partitions and create an extended partition in it's place to be able to create the partitions for Ubuntu (due to the limitation of only four allowed primary partitions, or three primary ones plus an extended one)

---

### Post by Elfy on 2012-01-03
> **Jerry N said:**
> forestpiske:  Just a thought but maybe there should be a "sticky" that explains the situation and the solutions for computers that already have all 4 partitions in use. This could include some details and precautions about using the Win 7 tools to shrink existing NTFS partitions.

Jerry

Possibly.

It'd need to be written by someone other than me - last windows I installed was eventually replaced by XP, I just notice these "I can;t install - there are 4 partitions already" threads.

---

### Post by swarup on 2012-01-03
> **mcduck said:**
> Did you use one of the automatic install options or the manual partitioning option?

There were only two options:
1) Replace Win7 with Ubuntu. That is, delete Win7 and make Ubuntu the only OS.

2) What from reading your and others' posts now seems like the manual opton.

So there was no option to install Win7 and Ubuntu side-by-side and receive a suggested setup for that. Perhaps this did not appear because Win7 is already utilizing the four available partitions?

> **mcduck said:**
> ...

Anyway, it really sounds to me like you are just looking at the four partitions that already exist on your computer. In which case Morbius1 is correct and you'll have to delete one of the existing partitions and create an extended partition in it's place to be able to create the partitions for Ubuntu (due to the limitation of only four allowed primary partitions, or three primary ones plus an extended one)

Ok-- sounds perfect. So which partition do I delete? Does it matter whether I delete sda3 or sda4? 

And as forestpiskie suggested, does this work need to by booting into Win7? If so, how much of that needs to be done there i.e. deleting a partition, downsizing the other one if I want, and then creating another partition for Ubuntu. I guess this very last step of creating the Ubuntu extended partition needs to be done using the Ubuntu installer. But up to that point all prior steps should be done in Win7?

---

### Post by Elfy on 2012-01-03
I would do all of the partition work in w7 - but just leave whatever space you gain unallocated and then let ubuntu find that unallocated space.

---

### Post by swarup on 2012-01-03
> **forestpiskie said:**
> I would do all of the partition work in w7 - but just leave whatever space you gain unallocated and then let ubuntu find that unallocated space.

Ok, great. I see. So, last question: Does it matter whether I delete sda3 or sda4?

---

### Post by mcduck on 2012-01-03
> **swarup said:**
> There were only two options:
1) Replace Win7 with Ubuntu. That is, delete Win7 and make Ubuntu the only OS.

2) What from reading your and others' posts now seems like the manual opton.

So there was no option to install Win7 and Ubuntu side-by-side and receive a suggested setup for that. Perhaps this did not appear because Win7 is already utilizing the four available partitions?



Ok-- sounds perfect. So which partition do I delete? Does it matter whether I delete sda3 or sda4? 

And as forestpiskie suggested, does this work need to by booting into Win7? If so, how much of that needs to be done there i.e. deleting a partition, downsizing the other one if I want, and then creating another partition for Ubuntu. I guess this very last step of creating the Ubuntu extended partition needs to be done using the Ubuntu installer. But up to that point all prior steps should be done in Win7?

Sure, if the allowed four partitions already exist the installer can't offer you any automatic install options since it can't create the required two partitions even if it resizes one of the existing ones.

Which one you should delete depends on what each partition is used for. You'll really have to check that yourself. Try mounting them and checking what's contained on each one, or do a Google search for the computer model to see if somebody already has an answer. (and yes, of course it does matter which one you delete. Removing wrong one can either break your windows install, result in loosing some of your previous data, or any other type of nasty result depending on what the partitions are used for.)

---

### Post by oldfred on 2012-01-03
It depends on what data you have in sda3 & sda4. Often a vendor recovery partition which will let you create a set of DVDs to restore system to as purchase. Only delete if you have made the set of DVDs. The other is ofter a vendor utilities partitions. Usually smaller and easily backed up.
  Like Microsoft wanted to use 2 partitions and suggested to Vendor to use 2 partitions, so then you cannot install any other system. Both Microsoft and Vendor do not have to answer service calls on something they do not know about, but a way to reduce the use of Linux. Use Windows to shrink the Windows partition but do not create partitions in Windows as that will convert to dynamic partitions which does not work with Linux.


May be on HP but seems to be all or most Windows 7 installs.
Good advice on how to handle all four primary partitions used. - srs5694 May be on MP but similar for most vendors.
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.


Since  the auto install routine cannot create new partitions when all 4 primaries are used, you have to do it manually.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by swarup on 2012-01-03
> **mcduck said:**
> Sure, if the allowed four partitions already exist the installer can't offer you any automatic install options since it can't create the required two partitions even if it resizes one of the existing ones.

Which one you should delete depends on what each partition is used for. You'll really have to check that yourself. Try mounting them and checking what's contained on each one, or do a Google search for the computer model to see if somebody already has an answer. (and yes, of course it does matter which one you delete. Removing wrong one can either break your windows install, result in loosing some of your previous data, or any other type of nasty result depending on what the partitions are used for.)


Ok, I see. I'll try mounting them and see. And I can google it too. But obviously, one of the two--sda3 and sda4--has to be safely deletable...

---

### Post by swarup on 2012-01-03
> **oldfred said:**
> It depends on what data you have in sda3 & sda4. Often a vendor recovery partition which will let you create a set of DVDs to restore system to as purchase. Only delete if you have made the set of DVDs. The other is ofter a vendor utilities partitions. Usually smaller and easily backed up.

I have not done anything with the computer, nor put any data on it. Just started it up and put in the Ubuntu USB for installation.

> **oldfred said:**
> May be on HP but seems to be all or most Windows 7 installs.
Good advice on how to handle all four primary partitions used. - srs5694 May be on MP but similar for most vendors.
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

Just read this. I am shocked and dismayed at the amount of work that is going to be involved for safely clearing space for the Ubuntu partition. 

(It is going to take me quite some time to figure out how to create the DVDs and the CD, then make sure which partition I can delete etc.)

---

### Post by mcduck on 2012-01-03
> **swarup said:**
> Ok, I see. I'll try mounting them and see. And I can google it too. But obviously, one of the two--sda3 and sda4--has to be safely deletable...

Like oldfred said one is most likely a recovery partition, which you can safely delete once you have created the recovery discs (or if you were lucky like me and got a full set of recovery discs with the computer).

And the other one is probably some tools and other vendor-specific stuff in which case it's your decision how useful those tools are to you.

(my current system is a HP laptop which came with four primary partitions by default, and since the tools partition actually contains some stuff I find quite useful (+ a stupid quick-boot OS which is actually slower to boot than Ubuntu :D) and I have the recovery discs I decided to remove the recovery partition. But it really depends on which one isn't any use to you, and what the actual setup on *your* computer is...)

---

### Post by swarup on 2012-01-03
> **mcduck said:**
> Like oldfred said one is most likely a recovery partition, which you can safely delete once you have created the recovery discs (or if you were lucky like me and got a full set of recovery discs with the computer).

And the other one is probably some tools and other vendor-specific stuff in which case it's your decision how useful those tools are to you.

from gparted:

sda1 (Windows Recovery Environment loader) 16 GB
sda2 (Win7 loader) 104 MB
sda3 97 GB of which 9.2 GB are used 
sda4 120 GB of which 3 GB are used

Does this give the information needed to determine what is on sda3 and sda4, or would I need to boot in Win7 to find that out?

---

### Post by mcduck on 2012-01-03
> **oldfred said:**
> 
  Like Microsoft wanted to use 2 partitions and suggested to Vendor to use 2 partitions, so then you cannot install any other system. Both Microsoft and Vendor do not have to answer service calls on something they do not know about, but a way to reduce the use of Linux.

Exactly what I've been thinking about. And especially strange considering I'm using a mobile workstation laptop which is even certified for Linux...

---

### Post by mcduck on 2012-01-03
> **swarup said:**
> from gparted:

sda1 (Windows Recovery Environment loader) 16 GB
sda2 (Win7 loader) 104 MB
sda3 97 GB of which 9.2 GB are used 
sda4 120 GB of which 3 GB are used

Does this give the information needed to determine what is on sda3 and sda4, or would I need to boot in Win7 to find that out?

nope, you'll really have to look at the actual contents of each partition...

Anyway, based on a quick google search on the laptop model it would seem that the first one is a recovery partition, the second one is a boot partition for Windows 7, and the third and fourth ones are set as C: and D: drives in Windows. In which case the fourth one would be safe to remove *after* you've copied all your personal data from there to the third partition (C: in Windows).

---

### Post by I_can_see_the_light on 2012-01-03
> **swarup said:**
> from gparted:

sda1 (Windows Recovery Environment loader) 16 GB
sda2 (Win7 loader) 104 MB
sda3 97 GB of which 9.2 GB are used 
sda4 120 GB of which 3 GB are used

Does this give the information needed to determine what is on sda3 and sda4, or would I need to boot in Win7 to find that out?

I suggest you boot into Win 7 and check what's on sda4. Sda3 is most likely your C: drive. If the data on sda4 isn't worth keeping then I suggest you delete that partition from within windows and let it be unallocated just like someone else suggested. Then you can restart and boot from your USB stick :)

Edit:
McDuck beat me to it (kind of). Need to learn to type (or think) faster :P

---

### Post by swarup on 2012-01-03
Ok, great! Thanks everyone--I don't have any data at all on the comoputer, so it sounds like sda4 should be deletable. I'll boot into Win7 and see what those 3GB are. If it is anything of any use, I'll move it to sda3 and then delete sda4, shrink sda3 and I should be good to go!

Add: I just went into Win7. There is a C drive and a D drive. The D drive is 120 GB size, and in "My Computer" it shows up as completely empty, with nothing at all in it. It shows up as 120 GB of 120 GB free.

The C drive contains the usual folders-- Windows, Program Files, etc.

So, sounds like the D drive should be safe to delete, doesn't it? Although in the Ubuntu installer it showed there was 3 GB of stuff on it, but in Win7 "My Computer", it shows up as completely empty. Shall I delete it?

---

### Post by mcduck on 2012-01-03
> **swarup said:**
> Ok, great! Thanks everyone--I don't have any data at all on the comoputer, so it sounds like sda4 should be deletable. I'll boot into Win7 and see what those 3GB are. If it is anything of any use, I'll move it to sda3 and then delete sda4, shrink sda3 and I should be good to go!

Add: I just went into Win7. There is a C drive and a D drive. The D drive is 120 GB size, and in "My Computer" it shows up as completely empty, with nothing at all in it. It shows up as 120 GB of 120 GB free.

The C drive contains the usual folders-- Windows, Program Files, etc.

So, sounds like the D drive should be safe to delete, doesn't it? Although in the Ubuntu installer it showed there was 3 GB of stuff on it, but in Win7 "My Computer", it shows up as completely empty. Shall I delete it?
Yes, that sounds like the drive is empty and intended just for your personal storage so it's safe to delete it.

(the 3GB in partition editor versus empty in windows would be because one is reporting partition editor would be reporting the used space on the partition, while windows reports used space on the file system. The file system itself takes some space even if there aren't any files in it. )

---

### Post by swarup on 2012-01-03
> **mcduck said:**
> Yes, that sounds like the drive is empty and intended just for your personal storage so it's safe to delete it.

(the 3GB in partition editor versus empty in windows would be because one is reporting partition editor would be reporting the used space on the partition, while windows reports used space on the file system. The file system itself takes some space even if there aren't any files in it. )

Yes, it looks indeed like this is the case. I changed the setting in My Computer to show hidden files, and still there is nothing there. So it is indeed empty!

---

### Post by jvcastle on 2012-01-03
Not that I'm any expert, but I run 4 machines dual booting with Win 7 and have never seen this.  Win7 will show how big its partition is.  Perhaps there are already 2 used win7 ntfs partitions?  If so, move win 7 stuff to only the main win7.  Then defragement it. The ubuntu install should then use about half on a side by side install - but the linux partition should be extSomething

---

### Post by swarup on 2012-01-03
Everything worked beautifully-- deleted the D drive, downsized the C drive, rebooted to the Ubuntu install USB, and, seeing the unallocated space, it gave the option to install side-by-side which is what I chose. I presume the installer will not do any further partition resizing and just install to the unallocated space. So I selected the side-by-side option, and now install is under way.

Thank you everyone!

---

