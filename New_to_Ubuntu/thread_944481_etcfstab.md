---
title: "/etc/fstab"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by i_have_a_sempron on 2008-10-11
My fstab was somehow deleted and I cant boot into any os. I only run Kubuntu 8.04 on my computer. I can not boot into any live cd, although I can get a limited busybox shell through my ubuntu live cd. Can I reconfigure my fstab through busybox? I know I can mkdir's but I need to know if I can input the files into the new directories that i am creating.

Thank you in advance.

---

### Post by ajgreeny on 2008-10-11
I suspect you must have done more than just delete your fstab file because I don't see why that would stop you booting to a live CD, fstab is not invoked as early as that in the boot-up procedure.  How did you manage to do it and what were you trying to do in any case?  Are you certain your live CD is a good one?  If it is, then I can't help you I'm afraid as I am out of my depth discussing busybox, never having seen it in my 3 years with Ubuntu.  But if you are not sure about the disk, try to get hold of another and boot to that if possible, then you can get an fstab file back again with some help from this forum.

---

### Post by i_have_a_sempron on 2008-10-11
I think my former roomate was having fun deleting directories until my laptop wouldn't boot anymore. My disk is good, I have 4 of them, one directly from ubuntu. What im trying to do is create a new fstab, which I can do, but I dont know how, or what, I need inside of the directory. I may also have a corrupted filesystem, but that shouldn't disable me booting from a disk. My computer is kinda old and replacing the hdd would potentially be a problem so I am trying to do everything I can without having to replace hardware. Without the liveCD I can't even get beyond grub. I get grub error 16, which consists of "Device string unrecognizable".

---

### Post by i_have_a_sempron on 2008-10-11
I have booted into Slax now, and it created an fstab for me, however it says i dont have a hard drive. what can i do?

---

### Post by Orange_and_Green on 2008-10-11
Hello. It's a bit hard to tell without having the machine in front of me, but if you suspect your computer has been the victim of foul play, you could try:

1) Have a look at the BIOS (especially the disk management part) and see if maybe the disk/controller has been disabled. If in doubt, most BIOSes give you the option to revert to factory settings.

2) Open it up and see if any connectors have been physically pulled or loosened.

I guess this is why I'm nearly maniacally jealous of my PC...

Good luck:KS

---

### Post by i_have_a_sempron on 2008-10-11
In bios, my harddrive is enabled and i have reset it to defaults, all connections in my machine are good, but could it be problems based on the jumper on my hd?

---

### Post by bobnutfield on 2008-10-11
I doubt that a system that has been that badly damaged is recoverable.  I would suggest using a live cd, mounting the partition with you data, and saving all your important files to a USB stick, then do a fresh reinstall.  Just my opinion.

---

### Post by i_have_a_sempron on 2008-10-11
> **bobnutfield said:**
> I doubt that a system that has been that badly damaged is recoverable.  I would suggest using a live cd, mounting the partition with you data, and saving all your important files to a USB stick, then do a fresh reinstall.  Just my opinion.

I have been trying to do a reinstall, but the livecd i have, cant find my hardrive.

---

### Post by bobnutfield on 2008-10-11
> **i_have_a_sempron said:**
> I have been trying to do a reinstall, but the livecd i have, cant find my hardrive.

OK, then I would use the Gparted contained on the live CD and format the entire drive, then set up new partitions.  If you still cannot install because of the same error, you may have a failing hard drive.

---

### Post by Orange_and_Green on 2008-10-11
Does the disk get detected in BIOS?

The jumper positions should be written on the disk's label. If you have another device on the same IDE channel, make sure one is set up to be the master and the other the slave, or that both use cable select. If the disk is alone on the channel, have it as a single drive / master.
I would recommend the boot hard drive is set up as the primary master though.

---

### Post by i_have_a_sempron on 2008-10-11
> **bobnutfield said:**
> OK, then I would use the Gparted contained on the live CD and format the entire drive, then set up new partitions.  If you still cannot install because of the same error, you may have a failing hard drive.

Well Im using Slax, I can't boot into my ubuntu disk, or well I havent been able to before. When I booted from this Slax disk, there was a prompt saying that it made my fstab, which was missing.

Do you know I could re-format my harddrive in a konsole?

Through KInfoCenter, I can see all my partitions and mount points, if that means anything to you.

---

### Post by i_have_a_sempron on 2008-10-11
> **Orange_and_Green said:**
> Does the disk get detected in BIOS?

The jumper positions should be written on the disk's label. If you have another device on the same IDE channel, make sure one is set up to be the master and the other the slave, or that both use cable select. If the disk is alone on the channel, have it as a single drive / master.
I would recommend the boot hard drive is set up as the primary master though.

Alright ill see if that does anything for me.

---

### Post by Orange_and_Green on 2008-10-11
When you say it does not see the disk, there actually are 2 possibilities:

1) The disk is detected, but it cannot be mounted, or
2) The disk is not detected.

From the slax live cd, you could try running

```
su root
fdisk -l
```

If it lists anything, it means it sees the disk (but maybe has problems with mounting. fsck can help you check disk integrity. fsck -a will try autocorrecting the filesystem, but be warned that it might not be able to recover all the data... provided your roommate didn't delete it first.). If it doesn't list anything, then the disk is not being detected. Jumper settings and hardware failure are the main candidates in this case in my opinion.

Good luck:KS

---

### Post by bobnutfield on 2008-10-11
If the instructions above do not work for you, you can format from the command line using a live cd, using the cfdisk utility.  While using the live cd, open a command line and type

> info cfdisk

and have a look at the instructions for using it.  You can format the entire drive then set up new partitions with this utility.  It may be a little daunting for someone just learning the command line, but it is fairly straightforware.  Post back if you need help with the commands.

---

### Post by i_have_a_sempron on 2008-10-11
Thank you both, ill give it a try!

---

### Post by bobnutfield on 2008-10-11
If you do elect to go ahead and format the drive to reinstall, here is a good guide for using the command line to do it:

[http://www.ehow.com/how_1000631_hard-drive-linux.html]("http://www.ehow.com/how_1000631_hard-drive-linux.html")

---

### Post by i_have_a_sempron on 2008-10-11
> **bobnutfield said:**
> If you do elect to go ahead and format the drive to reinstall, here is a good guide for using the command line to do it:

[http://www.ehow.com/how_1000631_hard-drive-linux.html]("http://www.ehow.com/how_1000631_hard-drive-linux.html")

Awesome thank you. And just throwing this out there to see if it means more to any of you than it does me.

When I use the command. fsck -A

I get this back.

fsck 1.40.8 (13-MAR-2008)

And that is all im getting, does that indicate any problems?

---

### Post by i_have_a_sempron on 2008-10-11
> **Orange_and_Green said:**
> 



From the slax live cd, you could try running

```
su root
fdisk -l
```




The out put i get us 

Unable to read /dev/hda

---

### Post by bobnutfield on 2008-10-11
No, the response you are getting is just telling you the version of fsck that you have.  If you want to run fsck on the driver, you would issue it this way:

> fsck /dev/sdx1 where "x" is the partition you want to check.

---

### Post by i_have_a_sempron on 2008-10-11
> **bobnutfield said:**
> If the instructions above do not work for you, you can format from the command line using a live cd, using the cfdisk utility.  While using the live cd, open a command line and type



and have a look at the instructions for using it.  You can format the entire drive then set up new partitions with this utility.  It may be a little daunting for someone just learning the command line, but it is fairly straightforware.  Post back if you need help with the commands.

For cfdisk i get this output.

FATAL ERROR: Cannot read disk drive

---

### Post by bobnutfield on 2008-10-11
Well, I would be concerned that my first suspicion may be correct and you hard drive is failing.  There are some testing tools you can use, the most likely candidate would be at the web site of your drive manufacturer.  Someone more familiar with the problem may chime in and offer some further suggestions.

---

### Post by i_have_a_sempron on 2008-10-11
With fdisk /dev/hda

its say the number of cylinders is set to 7296. There is nothing wrong with this but this is larger thatn 1024, and in certain setups could cause problems with: software that runs at boot time (older versions of lilo) and booting and partioning on other os's

now with fsck /dev/hda i get 

Superblock invalid, trying backup blocks. Bad magic number in super-block while trying to open /dev/hda

The super block could not be read or does not describe a correct ext2 filesystem. If device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superbock:
      e2fsck -b 8193 <device>





this does not mean much to me.

---

### Post by bobnutfield on 2008-10-11
Well, looks like your partition table is messed up.  Try running the command it suggests:

> e2fsck -b 8193 /dev/hda

That will try to recover the corrupted superblock, but I caution you that this is successful only in few occassions.  There are some experts here on the forum in hard drive recovery.  Hopefully, someone will chime in.

---

### Post by i_have_a_sempron on 2008-10-11
> **bobnutfield said:**
> Well, looks like your partition table is messed up.  Try running the command it suggests:



That will try to recover the corrupted superblock, but I caution you that this is successful only in few occassions.  There are some experts here on the forum in hard drive recovery.  Hopefully, someone will chime in.

Device or resource busy while trying to open /dev/hda Filesystem mounted or open exclusively by another program?

Should I reboot? Rebooting takes about 15mins so I dont want to unless it would help.

---

### Post by bobnutfield on 2008-10-11
No, if you have the partition mounted, you must unmount it before running that command.

> umount /dev/hda

Then try it again.

---

### Post by bumanie on 2008-10-11
The most common causes of no hard drive being recognized is 
1) There is no filesystem present - which in your case doesn't seem to be the issue or
2) The partition table has been corrupted.
Suggest using testdisk off the live ubuntu cd and attempting to recover and re-write the partition table. > sudo apt-get install testdiskTo run the program > sudo testdiskLook [here]("http://www.cgsecurity.org/wiki/TestDisk") and [here]("http://www.users.bigpond.net.au/hermanzone/p21.html") for tutorials/instructions. You can of course download the stand-alone testdisk .iso from the first link.

---

### Post by i_have_a_sempron on 2008-10-11
> **bobnutfield said:**
> No, if you have the partition mounted, you must unmount it before running that command.



Then try it again.

says it isnt mounted, so i rebooted the computer and got the same message, and its not mounted now either.

---

### Post by i_have_a_sempron on 2008-10-11
> **bumanie said:**
> The most common causes of no hard drive being recognized is 
1) There is no filesystem present - which in your case doesn't seem to be the issue or
2) The partition table has been corrupted.
Suggest using testdisk off the live ubuntu cd and attempting to recover and re-write the partition table. To run the program Look [here]("http://www.cgsecurity.org/wiki/TestDisk") and [here]("http://www.users.bigpond.net.au/hermanzone/p21.html") for tutorials/instructions. You can of course download the stand-alone testdisk .iso from the first link.

I dont know why, but my slax disk is the only disk I can boot into. I have 4 ubuntu disks, 2 knoppix disks, and my slax one. I know at least one of the ubuntu disks is good, I just got it in the mail from canonical

---

### Post by bobnutfield on 2008-10-11
The only thing I can suggest at this point is to take bumanie's suggestion and download the .iso of testdisk, burn it to cd and run it.  I'm sorry, wish I could have solved it for you, but I am out of ideas, other than you might try to use the instructions on the page I previously post for fdisk and try to delete the partitions rather than trying to format them.  But, if fdisk will not read the disk, that may not work.

---

### Post by i_have_a_sempron on 2008-10-11
Sounds like a plan, I burned Gparted live, and am trying it right now, doesnt look like it is going to boot.

---

### Post by i_have_a_sempron on 2008-10-11
Failed to boot because there was no live filesystem found.

---

