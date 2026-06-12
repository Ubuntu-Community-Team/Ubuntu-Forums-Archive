---
title: "Trying to run from USB stick."
date: 2013-04-04
forum: New to Ubuntu
---

### Post by rouletterun on 2013-04-04
I am brand new to Ubuntu, so please try to make answers as simple as possible. I have started with a formatted system, no OS, just the BIOS. I am trying to set up a sever version of Ubuntu 12.04.2 LTS. I have used UNetbootin to create a USB boot drive with the intent of running the OS permanently from the USB boot drive. When the system boots it gives me several options such as try without installing and installing. I have selected the try without installing option to run it off the USB stick. Next it will go through the Ubuntu start up dots page with a mouse pointer, this is where it flakes out on me; it next gives me a screen with multiple horizontal lines and the mouse pointer, but it's frozen and I can't do anything with it. I'm asking for suggestions.  THANKS IN ADVANCE!!

---

### Post by busagi on 2013-04-04
Try re-formatting the USB you're intending to boot from, and install a fresh copy of Ubuntu on it. I had a similar problem in the past where the image wasn't written to the USB properly, but it worked when I re-wrote the Ubuntu image to the USB. However, in my case I was just installing via USB, not attempting to use the USB as my system's primary HDD.

---

### Post by rouletterun on 2013-04-04
Thanks, I'll give it a try.

---

### Post by monkeybrain2012 on 2013-04-05
No you can't run it permanently from a usb created by unetbootin. It is only for testing, as a demo and for installation.

For one thing you will lose all your settings and data when you reboot if you have no persistence. Also a live usb doesn't support certain system upgrades (e.g kernel) and is limited to 4 G because of the FAT system. What you need is to install Ubuntu (a real install with ext4 file system) into the usb drive, or, to get better performance, an external hard drive. To to this you need two usbs (or a CD and a usb) one (or the CD) is to boot into the installer, the other (the target) is for installing Ubuntu into. 

So first boot from your unetbootin created live usb (or the live CD) and then connect the target (which can be a second usb flash drive or an external hard drive) then run the installer as you would a normal install, except when choosing the way of installation, pick "something else" and format the target drive (say sdc) as ext4 with mount point "/" , and VERY IMPORTANT, scroll to the bottom of the same page choose your target drive (say sdc)  from the drop down menu to install the boot loader. The rest is just answering the questions and clicking "continue"

---

### Post by C.S.Cameron on 2013-04-16
I have had similar experience trying to run Ubuntu on an old computer without enough power.
If this is the case try Lubuntu or Xubuntu.

If you only have a small flash drive, (4GB), a persistent install may be the best you can do.
You can make it a bit better by removing the Try/Install screen.

Edit syslinux.cfg by overwriting what is there with the following:

```
default live
label live
  say Booting an Ubuntu Live session...
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

If the drive is 8GB or larger you can do a Full install or just use a persistent casper-rw partition rather than the casper-rw file.

---

### Post by Mooney6959 on 2013-04-16
> **monkeybrain2012 said:**
> No you can't run it permanently from a usb created by unetbootin. It is only for testing, as a demo and for installation.

For one thing you will lose all your settings and data when you reboot if you have no persistence. Also a live usb doesn't support certain system upgrades (e.g kernel) and is limited to 4 G because of the FAT system. What you need is to install Ubuntu (a real install with ext4 file system) into the usb drive, or, to get better performance, an external hard drive. To to this you need two usbs (or a CD and a usb) one (or the CD) is to boot into the installer, the other (the target) is for installing Ubuntu into. 

So first boot from your unetbootin created live usb (or the live CD) and then connect the target (which can be a second usb flash drive or an external hard drive) then run the installer as you would a normal install, except when choosing the way of installation, pick "something else" and format the target drive (say sdc) as ext4 with mount point "/" , and VERY IMPORTANT, scroll to the bottom of the same page choose your target drive (say sdc)  from the drop down menu to install the boot loader. The rest is just answering the questions and clicking "continue"

x

I have a very similar issue to which I have tried the above, but to no avail.  Here's my deal.
1U server chassis w\ Mini-ITX MB and 2.5gb Intel processor, 16gb RAM, and two x 2tb hard drives in a hardware raid 0.

My ultimate goal is to boot from 16gb USB, but I have also tried loading Ubuntu to the raid.  No matter what I do, it seems as though the boot loader isn't installing properly.  I've tried 11.10, 12.04, and 12.10, all 32bit.  

I've had numerous times where the Ubuntu installation would fail or lock up, regardless of version.  I can't tell you how many times it's hung up.

The last time I was successful installing from LiveCD to the 16gb USB with the above mentioned method, it just hangs on a flashing cursor on startup.  I partitioned the USB as such; 8.5gb / (ext4), 500mb /boot (ext 4), and 7gb swap.

My ideal scenario would be to be able to run the server on Ubuntu 12.04 direct from USB and have the 4tb Raid as Fat32 storage.

Any thoughts or immediate things that stand out as to why this could be failing?

Thanks!

---

### Post by dandroid13 on 2013-04-16
If it's a server you won't have a GUI. Why don'tt you try Lubuntu since it's supposed to be light on resources.

---

### Post by Mooney6959 on 2013-04-16
> **dandroid13 said:**
> If it's a server you won't have a GUI. Why don'tt you try Lubuntu since it's supposed to be light on resources.

While it is physically in a server case, it's theoretically all laptop parts.  I prefer to keep the GUI.  Going to load Plex on it and, being a pretty much full force winblows guy, I prefer a gui.

---

### Post by zemega on 2013-04-16
You can perfectly run Ubuntu from a USB. Use one USB to load UnetBootin and the ISO. Use that one to get into the live session, and install it on **another **USB. Preferbly at least 16GB, better 32GB. Try to use a fast port like USB 3.0, i394 or external SATA.

Edit: Well, There might be video/graphic card issues. Intel should work fine. Others like Nvidea, have some issues sometimes.

---

### Post by dandroid13 on 2013-04-16
> **zemega said:**
> You can perfectly run Ubuntu from a USB. Use one USB to load UnetBootin and the ISO. Use that one to get into the live session, and install it on **another **USB. Preferbly at least 16GB, better 32GB. Try to use a fast port like USB 3.0, i394 or external SATA.

I tried doing this in the past and had issues, couldn't install at all... But the OP's issue is that he doesn't have a GUI so he doesn't know how to do it.

---

### Post by Mooney6959 on 2013-04-16
I tried running it from LiveUSB (PenDriveLinux) to USB, but found it was faster (in speed) going from Live CD to 16gb USB.  I may go back for a 32gb USB, but I see people running Ubuntu on next to nothing.
As for the GUI.  If you're referencing my situation, I'm not running Ubuntu Server, so I do have a GUI.  From what I understand, 11.10 and higher will see the amount of RAM I have without a problem, so I really see no advantage to having server version.

---

### Post by dandroid13 on 2013-04-16
> **Mooney6959 said:**
> I tried running it from LiveUSB (PenDriveLinux) to USB, but found it was faster (in speed) going from Live CD to 16gb USB.  I may go back for a 32gb USB, but I see people running Ubuntu on next to nothing.
As for the GUI.  If you're referencing my situation, I'm not running Ubuntu Server, so I do have a GUI.  From what I understand, 11.10 and higher will see the amount of RAM I have without a problem, so I really see no advantage to having server version.

CD takes ages here, and you config is great. But why are trying to boot from USB? I use dualboot (Win7/Kubuntu 12.10). Using persistance with USB 2.0 would be slow too.

---

### Post by Mooney6959 on 2013-04-17
> **dandroid13 said:**
> CD takes ages here, and you config is great. But why are trying to boot from USB? I use dualboot (Win7/Kubuntu 12.10). Using persistance with USB 2.0 would be slow too.

I'm deploying these servers to various areas of my company throughout the country.  My thought is, should there be an update I want to implement across all of them, or in case of an OS failure (though unlikely), I can just send out a new USB rather than have somebody on the far end who doesn't know what they're doing try to replace the hard drive.

If I can't get boot from USB to work, I'm going to probably just buy a very small hard drive to use strictly for the OS, keeping my raid for Fat32 storage.
My MB does support USB3.  Would it really be that much more beneficial for me to seek out a USB3 thumb drive? 

Any thoughts on why the boot loader doesn't seem to be coming up?

---

### Post by oldfred on 2013-04-17
@Mooney6959

The desktop installer does not have RAID drivers. It used to be you had to use server installer or if you want desktop type install use alternative installer. But they have eliminated the alternative installer, but not yet added all of the RAID drivers & grub install to RAID configuration to the Desktop installer. You can do a server install and add the desktop if you want.

Do not use FAT for any larger file system unless you have to have compatibility with a Mac or x-box. FAT32 has no journal and cannot store files over 4GB. So any larger file system with corruption may not be repairable with chkdsk and/or will take a very long time to repair. Better to use NTFS if you need Windows compatibility, but you need a Windows install or repair CD/Flash to run chkdsk as you cannot do that from Linux.

Are you sure you want RAID 0? You need to have really good backups as that is for speed not reliability. Most use SSDs for speed now.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

If you have more than 3GB of RAM, you really need the 64bit version to fully use the RAM. While PAE will access the RAM it is a hack.
      
 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)


 [http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
max - 4GB minus 2 Bytes, NTFS has journal
Just about all file systems compare
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by Mooney6959 on 2013-04-17
OldFred,

Thanks for the advice!

The reason I am going w\ Raid 0 is strictly for space.  I have 2 x 2TB drives, of which I want the most amount of space, and still it seem as though it's one drive.  Mind you, I agree w\ the lack of failsafe in this scenario.  I'll have to think about this and if I wish to move forward this way, split the drives, get one 4tb drive, or go with another Raid config.

I understand that desktop install doesn't have Raid drivers.  But being that this is a hardware Raid (done at the bios level), I was hoping to fool the OS.  I'm guessing this isn't the case?  

I downloaded the 12.04 32bit Alternate install but have not yet tried it, as I wish to keep the drives in the hardware raid vs messing w\ creating the same exact partitions on each drive just to use the Linux Raid.  Additionally, my main goal is to boot from a USB anyway, rather than the drives.

I will also do some reading up on what you sent about the drives.  I suppose I don't need FAT32 or even NTFS.  I just went with that since it's a format I'm familiar with (being fairly new to Linux).  What format would be best strictly for media storage and streaming (via Plex)?

Thanks again for all of your help!  I greatly appreciate it!

---

### Post by oldfred on 2013-04-17
IF you have any sort of newer computer you should use the 64bit.

I have seen specific recommendations for different formats, but some of those may be obsolete. Ext4 is good for most things.
       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

I have a 16GB flash drive with an install in 8GB and 8GB for data. It has 64bit with gpt partitioning (as a test of gpt). I just bought a new 32GB USB3 even though I do not have any USB3 ports. May be just a bit faster even with my USB2 ports.

---

### Post by Mooney6959 on 2013-04-18
Great News!  I finally got it to load w\ Ubuntu 12.04 64bit Alternate.
Not so great news... It's slow as heck!  Is this typical when running on a 16gb USB 2.0 flash drive?
It's  slow to the point that it fades the screen every time I try to click on  something new, then finally opens it after about 7 seconds.  Also,  nothing appears at all in my Dash Home.
Happy to have it running.   Was hoping for better performance.  May buy a 32gb USB 3.0 Flash to try  tomorrow, if somebody doesn't completely talk me out of it first.

---

### Post by oldfred on 2013-04-18
I have a full install in a 16GB flash drive. It is a bit slower booting, but once things are in RAM then it still is fast as most regular activity is cached in RAM anyway.

Did you change settings to reduce writes?

       With SSD or Flash drives, Use ext4 without journal, trim does not apply to flash drives:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

   [http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)

---

### Post by C.S.Cameron on 2013-04-18
> **Mooney6959 said:**
>  if somebody doesn't completely talk me out of it first.

I have 12.04.2 running on a **16GB** SanDisk Cruser Fit and it is quite fast, Like OldFred says, feels like it is running from RAM.
The first time I open Firefox it takes ten seconds, the next time under a second.
I have 12.10 running on a **32GB** Kingston DataTraveler 100 G2 and it is like you describe, slow as molasses, with dimming windows, etc.
I'm not sure if the problem is 12.10, the DataTraveler or something else.
This weekend I may experiment to try and find out.

---

### Post by zemega on 2013-04-18
Well, even though they are labeled USB 2.0, that doesn't mean that they have the maximum speed of 10MB/s, probably barely 2.0MB/s. If you have the resources, you might want to benchmark them, and see what their real write/read speed are. Little of them are very fast, these devices are what you need to find, the cheap ones are probably slow.

Although this is old, I remember people load and run Linux from RAM itself. I'm not sure how or does Ubuntu support this.

Beside USB, SSD seems like a logical choice as well, of course not the big size ones. Maybe the 16GB or 32GB would be enough for your requirement. Coupled with eSATA (you definitely cannot find this one laptop), but desktops might have eSATA.

---

