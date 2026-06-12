---
title: "Ubuntu is tough! Ext HD screwed up, OS was not booting, difficuit to troubleshoot!"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by Pabloshoney on 2013-05-02
Hey all

I'm new to Ubuntu, have wanted to give it a go for a while . . .so I did.

Followed all instructions to the letter and yet . . .

> Lappy wouldn't boot to Ubuntu, went to Windows 7 (although I said I didn't want Windows 7 anymore when installing Ubuntu). I searched for a solution, founds loads which were incomprehensible to me (I tried a few thought).  I reinstalled Ubuntu and it worked (yay).

> Ext HD - Then, wanting to watch a film, I plugged in my Ext HD.  When looking at its contents I saw exactly the same folders that I see when I click on 'Computer' . . . weird huh? (and yes i was definitely looking at the external HD, I can tell by its name and that it appear when teh device is plugged in and disappears when unplugged etc).  After this the Ext HD was no longer readable by any other computer in the house (OSX, Windows 7) or the TV! So I lost that !

What a pain ! in the space of a few hours I have lost the use of a lappy and 490GB of files on an HD.

Crazy how this could happen, especially as I followed all instructions.

Any advice on getting access to the files on the HD (when looked at on Disk Utility, there is now an icon called Linux Swap which was not there before, it is this I suspect Ubuntu has written and reads to).

Bonkers and maddening !

---

### Post by grahammechanical on 2013-05-02
May I ask where is Ubuntu installed to? On the internal hard disk? Or the External hard disk? If Windows 7 is still on the internal hard disk and the internal hard disk has first boot priority, then Windows will load.

When we install Ubuntu it creates two partitions. One will be where Ubuntu is installed. The other will be a swap partition. It is usual for Ubuntu to be installed in a primary partition with swap being installed into a logical partition inside an extended partition.

An installation of Ubuntu will make use of an existing swap partition rather than create additional swap partitions. I recently put in a second hard disk and installed Raring Ringtail on to it and it was using the swap partition that was on my original hard disk. This meant that if I ever removed the original hard disk, then Raring would not have a swap partition to use. No good at all. So, I had to disconnect the first hard disk and re-install Raring Ringtail so that it had its own swap file on the disk that it was installed on.

So, did this external hard disk have a swap partition already? If not then I am guessing that you allowed the installer to install Ubuntu on the external hard disk and not on the internal hard disk.

No, not weird. Just a consequence of actions that we the user choose to take.

Regards

---

### Post by Pabloshoney on 2013-05-02
Hey, thanks for your email.

'May I ask where is Ubuntu installed to?' - onto the internal HD

'If Windows 7 is still on the internal hard disk and the internal hard disk has first boot priority, then Windows will load.' - when installing Ubuntu it asked me what I wanted to do; keep Windows 7 etc (I can't remember that actual syntax now but I'm sure you'll know) - I chose options that installed Ubuntu, didn't require any post installation access to Windows 7 and didn't need any back up.  To my amazement, it then booted to Windows 7, why ?.  Then I followed instructions to do with Grub, still couldn't get it to work.  Until I installed Ubuntu again.  I think I m tryign to say that its not as easy to use, install as it seems.

'Swap partition' - not sure what that is, 

Ext HD - It had no partitioning at all.  A clean 500GB Ext HD full of 490 GB of files.  Now when I look at it in OSX (after having plugged it into teh Ubuntu lappy) there is a 'Linux Swap' icon (swap partition).  Why has that be written there? why does it prevent the drive being used on any other platform? . . . pretty dangerous.  Note - Ubuntu 

'am guessing that you allowed the installer to install Ubuntu on the external hard disk' - no, it is installed on the internal HD.  The Ext HD wasn;t plugged in when installing the OS, I only plugged it in once.

I presume I have done something wrong, however, if its this easy to screw it up, something isn't right.  I am a careful and experienced user, I read instructions and don't rush.  Not good.

I'd like to persevere with Ubuntu but am now wondering whether as a capable but not specialist user it would be unwise given the last few hours.

Any thoughts? especially on Ext HD recovery

---

### Post by Mark Phelps on 2013-05-02
> **Pabloshoney said:**
> ... Ext HD - It had no partitioning at all.  A clean 500GB Ext HD full of 490 GB of files.  
That's a contradiction -- a clean drive would have NO files and NO partitions; one with files must already have at least one partitioning.  Maybe what you meant to say was that you performed no partitioning on this drive.

IF there is a swap partition there, that is confusing because that's created during Ubuntu installation, and since you said the drive was NOT connected during the install, do not know how that happened.

> Any thoughts? especially on Ext HD recovery
If the partition on the external drive was for a Windows filesystem, and was NTFS,  then there are some things you can do to recover the files -- but, you will need to be able to connect the drive to a Windows PC and be willing to spend some money ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by Pabloshoney on 2013-05-02
"That's a contradiction --" - yes, I here what you say.  As you have said what i meant was there no other partitions (until I plugged the HD into the lappy, after that Disk Utility on OSX showed a 'Linux Swap' partition.  Now when reading the drive (on a variety of platforms) I can see no files.  To be clear, the Ext HD was NOT plugged into the lappy during installation.

'IF there is a swap partition there, that is confusing because that's created during Ubuntu installation' - very strange.  

Thanks for the Windows instructions, veyr useful.  I will also continue to look for OSX methods of recovery.


Thanks

---

### Post by Mopar1973Man on 2013-05-02
Another way to see the drive visibly. Is to use you Live CD and boot up to Ubuntu. Then got to Disk Utility from there it should show all your hard drive and the partition layout. Then you can figure out what happen a bit easier.

---

### Post by Pabloshoney on 2013-05-02
Thanks, at this stage I want to find a way to recover the files on the HD, probably from OSX.

---

### Post by 3rdalbum on 2013-05-02
> **Pabloshoney said:**
> 
> Lappy wouldn't boot to Ubuntu, went to Windows 7 (although I said I didn't want Windows 7 anymore when installing Ubuntu). I searched for a solution, founds loads which were incomprehensible to me (I tried a few thought).  I reinstalled Ubuntu and it worked (yay).

> Ext HD - Then, wanting to watch a film, I plugged in my Ext HD.  When looking at its contents I saw exactly the same folders that I see when I click on 'Computer' . . . weird huh? (and yes i was definitely looking at the external HD, I can tell by its name and that it appear when teh device is plugged in and disappears when unplugged etc).  After this the Ext HD was no longer readable by any other computer in the house (OSX, Windows 7) or the TV! So I lost that !

It sounds like your first attempt at installing Ubuntu, you actually installed it to the external hard drive. Of course, as it wasn't selected in your BIOS as a boot device, that's why your computer kept booting Windows 7 from the internal drive. It also explains why after the second installation, your external hard disk shows the same folder structure as your actual installation of Ubuntu, and the reason why your videos aren't on there and the drive can't be read in any Windows or OS X computers. It also explains why there's a Linux Swap partition on the external hard disk.

To put it bluntly, I don't think you were careful enough about selecting which disk to "Erase and Install" onto. Sorry, you've probably lost your videos.

---

### Post by Pabloshoney on 2013-05-02
Thanks for your thoughts. I completely understand your logic and follow your argument and I must admit it looks that was except . . . my Ext HD wasn't connected, and I wasn't prompted to choose a HD/partition.

Strange

---

### Post by oldfred on 2013-05-02
If you did install to external drive, only use live flash drive you used to install. Then add Boot-Repair to the installer and run the Boot-Info report. Do not do any repairs as that may not be what you want.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

We have seen a few users not partition external drives, just format them. They then are like very large floppy drives with data but no partitions. But even Windows wants to see partitions, not sure if a Mac would read it or not. Have not seen anyone recover data just copied to a drive. If you find a solution it would be good to know.

---

### Post by Mark Phelps on 2013-05-02
IF your external drive was formatted NTFS, then read through my post -- as that recovery app does not read partitions, but instead, looks for old file headers -- which are likely to still be there.

---

