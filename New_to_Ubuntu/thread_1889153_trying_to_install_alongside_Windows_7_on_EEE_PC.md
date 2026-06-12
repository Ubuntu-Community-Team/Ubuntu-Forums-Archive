---
title: "trying to install alongside Windows 7 on EEE PC"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by kongluke on 2011-11-30
Hello everyone,

I have a EEE PC with Windows 7 Starter that I'd like to transform into a dual-boot Windows/Ubuntu setup.  I have zero previous Ubuntu experience but am very enthusiastic.  When the computer boots from the USB installation drive, I have can run Ubuntu from the USB drive or install it on the hard drive.  If I try to install it, I have three options: have it WITHIN Windows, have it REPLACE Windows, or 'something else.'  I want to install it ALONGSIDE Windows, so I retreat.

Running Ubuntu off the USB drive, I see an install option on the Ubuntu desktop.  I try that, and a message advises that "/dev/sda has unmounted partitions" and would I like to "unmount partitions that are still in use?"  Scared and ignorant, I say no.  I then have two options, either REPLACE or "Something else".  I peak at "something else" and see there are four things (partitions?): sda1 (ntfs), sda2 (fat32), sda3 (ntfs), and sda4 (unknown).  No "Alongside" option in either case.  

Any advice would be much appreciated!  
Luke

---

### Post by farrinux on 2011-11-30
> **kongluke said:**
> Hello everyone,

I have a EEE PC with Windows 7 Starter that I'd like to transform into a dual-boot Windows/Ubuntu setup.  I have zero previous Ubuntu experience but am very enthusiastic.  When the computer boots from the USB installation drive, I have can run Ubuntu from the USB drive or install it on the hard drive.  If I try to install it, I have three options: have it WITHIN Windows, have it REPLACE Windows, or 'something else.'  I want to install it ALONGSIDE Windows, so I retreat.

Running Ubuntu off the USB drive, I see an install option on the Ubuntu desktop.  I try that, and a message advises that "/dev/sda has unmounted partitions" and would I like to "unmount partitions that are still in use?"  Scared and ignorant, I say no.  I then have two options, either REPLACE or "Something else".  I peak at "something else" and see there are four things (partitions?): sda1 (ntfs), sda2 (fat32), sda3 (ntfs), and sda4 (unknown).  No "Alongside" option in either case.  

Any advice would be much appreciated!  
Luke
Luke
you need to know where those partitions actually are. First and for most I would boot back into win7 and go to disk management and right down what partitions show up and there sizes.  My netbook only had two. The actually operating system partition and the recovery partition as I was not given a windows cd. Anyway when you start your install "chose something" else and look at the partitions it shows.  There sizes should match what win 7 said and will give you a clue as to what is where.  Typically sda1 is where win should be installed, but not always.  As for the sda2 (Fat32) listing that should be your thumb drive that you are booting off of. The other NTFS file partition could be just that or your "recovery partition" if you have one. The unknown I am not sure about but I think on my netbook it was my recovery partition. Anyway when you figure out what partition is what then you need to figure what where you want ubuntu. If you have a spare empty partition you could put it there or you could split your win partition and put it there.

Do make sure that if you have a recovery partition to A. leave it alone and B. if you have not done so burn your back up cd's before trying to install ubuntu.

---

### Post by I2k4 on 2011-11-30
I'm sure you'll get lots of good advice about how to dual boot, but as a netbook user, I experimented with Live USBs in different versions for several months before deciding which I liked.  The recent 11.x Ubuntu is noticeably harder on netbook performance than  the 10.x distros, and there are lightweights like Lubuntu and different interfaces like Mint - I'm not selling any of them just suggest trial and error before committing a casual flirtation to your hard drive. 

My approach was Live USB with about 2.5GB of Persistence on a 4GB USB drive.  "Persistence" permits installing new software and saving settings between boots. These Live installs work quite well for weeks at a time, and give a good impression of how different the available choices are for look, feel, performance and preinstalled software, without writing any changes to the netbook's drive.

---

### Post by Mark Phelps on 2011-12-01
If it doesn't provide the Alongside option, that most generally means that the drive already has the maximum of 4 primary partitions assigned -- and the installer then can not create any more.

If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

---

### Post by corncob on 2011-12-01
My eee netbook is probably different from yours but it has 2 solid state drives.  Xandros Linux was installed on sda (8 gig) and nothing on sdb (32 gig).  I installed Ubuntu on sdb which I could select from a dropdown menu on the partitioning screen and left Xandros alone.  However, you won't have that drop down menu if you only have one drive.
More recently I bought an eeebox running win7 and had the same problem you're experiencing. Although win7 only requires 2 partitions the OEM had put on 4, all primary.  I saw that the one labled 'storage' had nothing in it and deleted it.  I deleted another one too which appeared to be boot info since I was going to install grub anyway.  I created an extended partition in the resulting unallocated space and installed Ubuntu in it.

---

### Post by Mark Phelps on 2011-12-01
> **corncob said:**
> I deleted another one too which appeared to be boot info since I was going to install grub anyway.

And, if the OP does this, they will NOT be able to boot Win7 anymore!  Why? Because this "boot" partition contains the boot loader directory and files for Win7.

There is a way to "migrate" these files into the Win7 OS partition, but if the boot partition is removed and the PC rebooted before this "migration" takes place, the PC will no longer be able to boot into Win7.

---

### Post by corncob on 2011-12-01
Hmmm... whatever I did I can still boot Win from grub.  Gparted shows a Recovery, Win7, and an extended partition containing 10.04, 11.10, and a swap partition.  Good advice for the OP though-- I have wiped out drives floundering around.

---

### Post by roger_1960 on 2011-12-01
Hi

I suspect that you have a system with 4 primary partitions, 4 is the maximum that you can have. I think that sdb3 is a partition created to save W7 data.

I suggest the following:

Follow the asus user manual and use an external drive to save/create a recovery image of your laptop.

Separately backup any valuable data you have on your netbook.

Using gparted available on the live ubuntu CD delete the sdb3 partition (it should be empty apart from a couple of files - if not, don't proceed)

Using the live cd select install and when it asks, install alongside existing installation (can't remember the exact words).  It will use the empty space you have created to create a ubuntu partition and a ubuntu swap partition.  After install, reboot and you should be OK.  You should get a "grub" screen asking you whether to boot to ubuntu or windows.

---

### Post by Non-Sequitur on 2011-12-02
I don't know but, when I was curious about Ubuntu and wanted to dual boot to discover whether or not I liked it and acttually wanted a permanent install, I used 'Wubi'.  That allowed me to install Ubuntu as though it were just another Windows program.  I used it in that manner until I decided I wanted it to become my primary OS.  At that point I uninstalled it from Windows and did a full install of Ubuntu.

No need to make things more complex than they need to be.  Wubi works fine and you don't have to fiddle with disk partitions and all the other stuff that can lead to extreme frustration for a new user.  So many people never give Linux a chance because of initial bad experiences.

Just a thought.

---

### Post by kongluke on 2011-12-05
Many thanks for all the wisdom!  It turns out that it's one hard drive that came already with four partitions (one apparently has some special EEE operating system designed to let you hop online without booting windows?).  So I backed up all my data, said a prayer, removed one of the partitions (the D: drive that I had been using for data), and was able to install Ubuntu "alongside Windows" successfully.  

The bad news is that after I shut down for the first time I haven't been able to get back into Ubuntu.  The computer boots straight into windows.  I F2 my way to BIOS, but see no obvious way to direct its booting towards the new partition.  Any suggestions?

(It's great to have Ubuntu installed, finally, even if I can't use it...)

Thanks!
Luke

---

### Post by pierreyy on 2011-12-05
boot from a live cd or usb  open the terminal and type in 
```
 sudo apt-get install grub 
```
 
the grub is what lets you choose which OS to go into.... hope fully this would fix your problem... good luck.

---

### Post by roger_1960 on 2011-12-05
Hi

Go into the BIOS at boot and disable "fast boot"

---

### Post by corncob on 2011-12-05
> **kongluke said:**
> Many thanks for all the wisdom!  It turns out that it's one hard drive that came already with four partitions (one apparently has some special EEE operating system designed to let you hop online without booting windows?).  So I backed up all my data, said a prayer, removed one of the partitions (the D: drive that I had been using for data), and was able to install Ubuntu "alongside Windows" successfully.  

The bad news is that after I shut down for the first time I haven't been able to get back into Ubuntu.  The computer boots straight into windows.  I F2 my way to BIOS, but see no obvious way to direct its booting towards the new partition.  Any suggestions?

(It's great to have Ubuntu installed, finally, even if I can't use it...)

Thanks!
Luke

Are you sure you deleted that partition?  Did you create an extended partition and format the resulting space, make / the mount point?  I'm just thinking of an experience I had many distributions ago when I thought I had installed Ubuntu but it wasn't there -- just some unallocated space.  You can check on that using geparted from the live CD.

---

### Post by cuberts on 2011-12-05
> **pierreyy said:**
> boot from a live cd or usb  open the terminal and type in 
```
 sudo apt-get install grub 
```the grub is what lets you choose which OS to go into.... hope fully this would fix your problem... good luck.
^
Another common issue is when the Windows partition gets unaccessible, because Grub didn't install properly. It's easy to access the windows files from linux, because it's mounted under /windows usually. 

So I wondered if it could work the other way around. That may be a faster alternate solution.

---

### Post by Mark Phelps on 2011-12-05
You said you installed Ubuntu "alongside Windows" -- but that could mean several very different things.  So, do NOT force an installation on GRUB until we know HOW Ubuntu is installed on your PC.

Did you install Ubuntu into its own partition? IF so, what did you do about shrinking the Win7 partition to make room?

Did you install Ubuntu from "inside" Win7 -- something known as Wubi?

If you're not sure, you can open the Disk Management utility in Win7 and look at the partitions.  If all of them are NTFS, then you most probably installed Ubuntu from inside MS Windows -- since Ubuntu can't be installed natively to an NTFS partition.

You can also boot from an Ubuntu desktop CD, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one). That will list out the partitions on your drive.  Post the results back here so we can see what you have.

---

### Post by kongluke on 2011-12-05
Thanks for all the suggestions!

I disabled "boot booster" and "express gate" in BIOS, and did "sudo apt-get install grub" (before I saw the suggestion to postpone) but neither worked.  

I'm not sure that I deleted the partition, but in Windows where "My Computer" once had a C: and a D: drive, there's only the C: drive now.  I don't _think_ I did "create an extended partition and format the resulting space, make / the mount point," unless that can be done inadvertently.  I also did not knowingly shrink the Win7 partition to make room.  I just deleted the partition labelled "D:" in the Windows Disk Manager, and then when I tried to install Ubuntu off the USB there was (for the first time) an option for "alongside" Windows.  That seemed to work, so I thought that since I had reduced the partitions from 4 to 3, the installation process just did the rest.  (So I definitely didn't use Wubi to install it from inside Win7.)

I tried sudo fdisk -lu:
/dev/sdb1 	*	2048	209818247	104857600	7	HPFS/NTFS/exFAT

/dev/sbd2		209717248	241174527	15728649	1b	Hidden W95 FAT32

/dev/sbd3		488353792	488395119	26664		ef	EFI (FAT-12/16/32)

/dev/sdb4		241176574	488353791	123588689	5	Extended

/dev/sdb5		241176576	486275071	122549248	83	Linux

/dev/sdb6		486277120	488353791	1038336	82	Linux swap / solaris

(There's also a second listing for the USB drive, sda1 (Boot *, Id = b, System = W95 FAT32))

My newbie eyes see six partitions (thought four was the max?--feel like Chevy Chase jumping the family truckster 50 yards) and Linux.  A part of me wants to uninstall and reinstall, but I don't even know how to do that.

Happily awaiting new suggestions!
Luke

---

### Post by kio_http on 2011-12-06
Boot an Ubuntu live cd and open terminal

then

```
sudo grub-install /devX
```
Replace X with the actual device that is used to boot example "a" not "a1"

```
ls -l /dev/disk/by-label/
``` can help you find which device it is.

Then mount your Ubuntu partition e.g say you mounted it to /media/mnt

do 

```
sudo chroot /media/mnt
```
```
sudo update-grub
```

---

### Post by kongluke on 2011-12-06
Thanks!  How do I determine what my "/media/mnt" should be?  I guess that's where I mounted my Ubuntu partition, but I don't know what that means or if I did it.  ?

---

### Post by Ms. Daisy on 2011-12-06
> **kongluke said:**
> 
/dev/sdb1     *    2048    209818247    104857600    7    HPFS/NTFS/exFAT

/dev/sbd2        209717248    241174527    15728649    1b    Hidden W95 FAT32

/dev/sbd3        488353792    488395119    26664        ef    EFI (FAT-12/16/32)

/dev/sdb4        241176574    488353791    123588689    5    Extended

/dev/sdb5        241176576    486275071    122549248    83    Linux

/dev/sdb6        486277120    488353791    1038336    82    Linux swap / solaris

(There's also a second listing for the USB drive, sda1 (Boot *, Id = b, System = W95 FAT32))

My newbie eyes see six partitions (thought four was the max?)
I can answer the partition question. Yes, 4 is the max. The partitions /sdb1, /sdb2, and /sdb3 were previously existing.  Then Ubuntu created an extended partition  /sdb4.  Inside of that extended partition, you have /sdb5 which is Ubuntu, and /sdb6 which is the Ubuntu swap space.

---

### Post by Mark Phelps on 2011-12-07
> I just deleted the partition labelled "D:" in the Windows Disk Manager,

Well ... that's certainly ONE way to make room and allow for adding another partition!

Don't supposed you knew what was in the "D" partition before you removed it?

Suggest you go back into Win7 Disk Management utility and look at the partitions now. If your PC came preinstalled with Win7, and there is no Recovery partition -- that's what you removed.  And in that case, you most probably have no way of ever restoring your PC to it's original state.

A good thing to do now that you have dual-booting, is to go into the Win7 Backup feature and use the option to create and burn a Win7 Repair CD.  This will allow you to repair the Win7 boot loader -- should you ever need to do that in the future.

Also, if you have an external drive (or are willing to get one), you should also do the following in Win7:
1) Download and install the free version of Macrium Reflect
2) Use the MR option to create and burn a Linux Boot CD
3) Hook up an external drive and image off the Win7 install.

With this done, you NOW have a way of restoring your Win7 install in the future.

---

### Post by corncob on 2011-12-08
> **Mark Phelps said:**
> And, if the OP does this, they will NOT be able to boot Win7 anymore!  Why? Because this "boot" partition contains the boot loader directory and files for Win7.

There is a way to "migrate" these files into the Win7 OS partition, but if the boot partition is removed and the PC rebooted before this "migration" takes place, the PC will no longer be able to boot into Win7.

> It turns out that it's one hard drive that came already with four partitions (one apparently has some special EEE operating system designed to let you hop online without booting windows?).
This sounds like what I deleted.  I didn't miss it because I never used it.  I leave the computer on 24/7 because of distributed computing, bit torrent, and it does provide a little heat in the winter lol.

---

### Post by kongluke on 2011-12-09
Big thanks to Ms. Daisy for the partition explanation, which makes great sense, and to Mr. Phelps for the instructions on getting the repair and boot cds, which'll be my weekend project.  (The D: drive seemed only to have my data, so I was after hoping nothing else got lost when I junked it....)  I still don't have my dual-boot, though; I'm hesitating to do kio_http's solution just because I'm not sure what to put after 'sudo chroot'--it sounds like "/media/mnt" might not be the magic argument in every case?  Suggestions appreciated!

Luke

---

