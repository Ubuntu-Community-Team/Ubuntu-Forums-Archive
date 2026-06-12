---
title: "uninstalling grub2"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by degarb on 2012-04-12
I have a Ubuntu machine, formerly xp that I wiped and installed Ubuntu.  Now I cannot go back.

I gparted delete and linux live cd fdisk delete the ubuntu partion.   I cannot get the installer to load xp, it cannot boot the os.   Confirmed good xp cd. 

  [COLOR=DarkRed]**_Now, the only thing I can think of is to try again, but remember to delete the swap partition.    _**[/COLOR]Or am I wrong?

  Like I need to buy new drive just to install xp after Ubuntu.

   I like ubuntu, I need xp.  It is just easiest to install a small ubuntu partition later after wiping and installing xp.

---

### Post by wolfen69 on 2012-04-12
What partitions are on the hard drive should not make a difference in whether the xp cd will boot. Windows will see any linux partitions as "unkown".

---

### Post by roelforg on 2012-04-12
> **wolfen69 said:**
> What partitions are on the hard drive should not make a difference in whether the xp cd will boot. Windows will see any linux partitions as "unkown".

And is known for "accidentally"* corrupting them.

* i just think you can't accidentally overlap partitions

---

### Post by degarb on 2012-04-12
I simply deleted the partions with live gparted.  When xp wouldn't boot after initial file copy.  I tried live linux cd fdisk  m then d 1 2 3 4.     Hopefully that was right.

Then I tried an alternative xp cd.  Same thing.            

Now back to linux, for now.  But I cannot do what is needed with linux or xp in the vm.

---

### Post by roelforg on 2012-04-12
Just reinstall grub as bootloader, it'll detect windows just fine. But setvit to store stuff on a seperate partition or windows c:\

---

### Post by degarb on 2012-04-12
> **roelforg said:**
> Just reinstall grub as bootloader, it'll detect windows just fine. But setvit to store stuff on a seperate partition or windows c:\

I was thinking of this.   Just make separate partition for XP, try to install there.  It will probably not boot.  I will then need to reinstall grub (I know how to mount partion and install via command line with live cd.) 

Now, would this somehow help xp boot and finish the install, since grub is doing something?  

Grub is a monster to understand.

---

### Post by oldfred on 2012-04-13
XP needs either unallocated space with an available primary partition or a preformatted NTFS primary partition with the boot flag (active partition in Windows).

Most suggest making Windows sda1, as that is how most drives are configured, but it can be sda2,3 or 4.

Windows will automatically install its boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by anewguy on 2012-04-13
Boot off the LiveCD again and bring up disk-utility.  Have it display the partitions on your drive and post back what it shows - a screen shot would be nice.

I think we need to see exactly what your disk looks like before we can proceed.  

Also, when you say the Windows XP CD doesn't boot the OS, do you mean you've gone through the installation process AFTER you deleted ubuntu but it won't boot from the hard disk, or do you mean you can't get it to start installing to your hard disk?

Dave

---

### Post by degarb on 2012-04-13
[QUOTE=anewguy;11841315

Also, when you say the Windows XP CD doesn't boot the OS, do you mean you've gone through the installation process AFTER you deleted ubuntu but it won't boot from the hard disk, or do you mean you can't get it to start installing to your hard disk?

Dave[/QUOTE]


After deleting the linux partition and creating an ntfs,  I ran the xp cd, which did its full ntfs format and copied the install files to the hard drive, then rebooted.   I then get "cannot load the OS" message.  It doesn't install.    With the other xp cd, same except no message just blank screen.

Maybe, if I try again.  I can fix mbr with the xp installation cd.  However, once those install files are copied over to the HD,  I haven't been able to load the cd with just hitting the "anykey", until I wipe out the partition again.   I an not 100% sure if this is always, though.   My other option is to reinstall grub and hope this cures the mbr of xp.   I tried this once, but the grub2 didn't detect the windows xp mbr, only gave me linux boot options, which didn't work anyway to boot ubuntu since 10 linux was installed and I only have 11 iso. I now am working with 11.

It will take 2-3 hours to resize the linux partion, about an hour to mess around  reinstalling grub and xp and tests. If I cannot sucessfully bring back the linux with grub reinstall, this time, I will have another hour reinstalling linux. I need the shares off this computer too much to have much down time.  So, I cannot now post this, since I .

---

### Post by anewguy on 2012-04-13
I don't really understand this at all - a Windows install should have overwritten the MBR - the grub loader wouldn't be there.  I think something else is going on.

A thread that can address the MBR issue follows.  Oldfred gave a simple way to that in the thread:

[http://ubuntuforums.org/showthread.php?t=1956674]("http://ubuntuforums.org/showthread.php?t=1956674")

I also have heard somewhere that Windows prefers to be the first partition on the disk.  I don't have any idea if that is true or not, but if your swap partition is still there, be sure to delete it.  If you use the LiveCD and follow oldfred's post in the link you will reset the MBR to boot your Windows installation.  If it doesn't work after that, something more is wrong.

Also, as oldfred mentioned above, when you removed the Ubuntu partition(s), if you created a Windows partition but didn't mark it as bootable, Windows won't boot when you install to it.  Your best bet is to completely remove all non-recovery partitions, then create a primary partition, be sure it is bootable, but don't format it.  Let Windows install to that partition.  As I mentioned, installing Windows should have overwritten the MBR.

But......you mention needing shares off the computer.  Where are those shares - in another partition?  If they were in an ubuntu partition and you deleted the Windows partition they are gone.  If they are on a separate disk from the OS disk, why not just use the LiveCD and back them up first?  If they were in a Windows partition, and you are reinstalling Windows from the CD into that partition, they are probably gone as well.  That's why I needed a true picture of how the disk is partitioned, as something sounds a little different from what it appears here.



Dave ;)

---

### Post by degarb on 2012-04-13
> **anewguy said:**
> I don't really understand this at all - a Windows install should have overwritten the MBR - the grub loader wouldn't be there.  I think something else is going on.

A thread that can address the MBR issue follows.  Oldfred gave a simple way to that in the thread:

[http://ubuntuforums.org/showthread.php?t=1956674](http://ubuntuforums.org/showthread.php?t=1956674)

I also have heard somewhere that Windows prefers to be the first partition on the disk.  I don't have any idea if that is true or not, but if your swap partition is still there, be sure to delete it.  If you use the LiveCD and follow oldfred's post in the link you will reset the MBR to boot your Windows installation.  If it doesn't work after that, something more is wrong.

Also, as oldfred mentioned above, when you removed the Ubuntu partition(s), if you created a Windows partition but didn't mark it as bootable, Windows won't boot when you install to it.  Your best bet is to completely remove all non-recovery partitions, then create a primary partition, be sure it is bootable, but don't format it.  Let Windows install to that partition.  As I mentioned, installing Windows should have overwritten the MBR.

But......you mention needing shares off the computer.  Where are those shares - in another partition?  If they were in an ubuntu partition and you deleted the Windows partition they are gone.  If they are on a separate disk from the OS disk, why not just use the LiveCD and back them up first?  If they were in a Windows partition, and you are reinstalling Windows from the CD into that partition, they are probably gone as well.  That's why I needed a true picture of how the disk is partitioned, as something sounds a little different from what it appears here.



Dave ;)

I have a second drive, slave, that is 500 gig ntfs.  There is about 6 gigs of wife's docs that I copied over to ext4 and share.

I forget/confused, how do I flag the partition as bootable?   fix mbr with xp?

I agree, something else could be going on.  However, no problem installing Ubuntu, and xp was installed on machine before ubuntu ever was.

... Come to think of it, Dave, I think the ntfs drive does have one 30 gig linux partition.  I don't recall what I used it for.  It was attached to my xp/mint dual boot machine (only use the xp, mint as an os backup).  I don't recall if I ever installed linux there, but I see no os on it, only backup data.   I also did take precaution to unplug the second drive to ensure I didn't accidentally wipe out the drive during gpart, fdisk, or install.

---

### Post by anewguy on 2012-04-13
I know for sure you can run off the ubuntu livecd, run disk-utility and change partitions, and there is an option when you create a partition to say "boot" or "bootable".  So, on the disk that you are blowing everything away on (btw - disconnecting the 2nd disk with all your shares on it is a good idea), just boot the livecd, start disk-utility, delete all partitions (except a recovery partition, if present).  This should result in disk-utility showing a very large chunk (if not all) that says "Not Allocated".  Click on that, then click on the add or new and select partition.  Be sure you select "primary" and click the "boot" (it might say "bootable").  The end result should be a new primary partition marked as "boot". If you need to tell it what type of filesystem, be sure to select NTFS.

Now you should have the equivalent of a "new" drive.

Try reinstalling Windows again (again with the 2nd drive disconnected).  Installing Windows should overwrite the MBR - that's why people lose the ability to boot Linux when they install Windows after installing Linux. 

If you get any error message, please write them down.  If it doesn't boot, then use the livecd and disk-utilty and post back the map of the partitions on the drive.

Dave ;)

---

### Post by Scott Baker on 2012-04-13
Quick question. You say you "need" Win XP. What are you doing that warrants having XP as a separate installation? I ask, because I too use XP Pro on occasion, but run it installed through virtual box. I don't need it often (it's actually because some of my work requires internet explorer, firefox not an option). Is a virtual install possibly an option?  :-k

---

### Post by degarb on 2012-04-15
> **Scott Baker said:**
> Quick question. You say you "need" Win XP. What are you doing that warrants having XP as a separate installation? I ask, because I too use XP Pro on occasion, but run it installed through virtual box. I don't need it often (it's actually because some of my work requires internet explorer, firefox not an option). Is a virtual install possibly an option?  :-k


When I saw the hit of video transcoding, and most my video encoding is like PlayOn, windows only.  Also, many ahk scripts get flakey in vbox.  I have about a half dozen scripts that I wrote that have no linux alternatives, like an alternative to the poorly designed handbrake gui, ripping stacks of cds with lookup and human interaction at end of rip session, etc. etc.  With this kinda hit, I didn't even try running voice recognition.

I use a single core hyperthreading cpu.  I don't have latest greatest, nor will I until the hardware wears out.

Anyway,  I doubted it fixmbr from xp cd would work.   But I  did think, I may have forgot to manage the flags in gparted to flag it  as the boot partition. 
 
So, Off, to try again, with flag for boot.... Didn't work.   Then I  noticed xp install cd had utility to delete and create the partion.  I  theorized that gparted is a linux tool, and probably creating proper xp  partitions isn't thoroughly tested.  So, I deleted the gparted ntfs and  created it with the xp cd.   It worked! 
 
So, basically gparted could not create a proper bootable xp partition.

I have several gparted isos, but only could get .7 to boot.  Probably a year old.

---

