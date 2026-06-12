---
title: "DVD Boot problem after removing boot flag from SSD drive"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by chris253 on 2014-06-30
I am in the process of making my SSD drive into a dual boot. For a couple of months I have been using it only for Ubuntu 12.04, but now want to add Windows 7. I used Gparted to prepare the SSD by reducing and moving my data partition. (I also made a back up). I then deleted the swap and ubuntu partitions, including the removal of the boot flag from swap partition (probably a big mistake). From the unallocated space I created two new partitions for Windows and Ubuntu 14.04. I then closed down and tried booting a Windows 7 installation disk, but it only got to the BIOS startup screen with the Gigabyte logo and options to press Del/F9/F12/End. In fact pressing any key just caused brief blank screen, DVD access then the same re-display. I then tried booting from a DVD with my Ubuntu 14.04 image, but got the same result. I tried clearing the CMOS, but same result.

I then tried detaching the SATA and power cables from the SSD, did a reboot of Ubuntu, and behold it worked!

The question now, that I hope someone can answer, is how do I get my SSD sorted? Can I safely connect it to a live system? If so do I need to set the boot flag again?
Why did the boot process object to the state of the SSD when it was not loading from there anyway?

---

### Post by sandyd on 2014-06-30
> **chris253 said:**
> I then deleted the swap and ubuntu partitions

Which partitions did you delete - you may have deleted the root (or boot if you have a seperate boot partition) which would remove the bootloader files from disk.

---

### Post by chris253 on 2014-06-30
Hi Sandy

I removed /dev/sda1 which was a 9gb  linux-swap partition, but it had a boot flag, so yes I guess it could have had the bootloader files although Gparted did not say it had any used space. I'm new to linux, but I think the root was at sda5 as that had a mount point of /.

Chris

---

### Post by yancek on 2014-06-30
There really is no reason to have a swap partition of 9GB.  4GB is pretty good but I guess it depends upon how much RAM you have and what you do with the computer.  If you have a really large drive or drives, it doesn't really matter.  I've never heard of anyone marking a swap partition as bootable.  Pretty cool!  You do need to mark the windows system partition (the one with its boot files) as active/bootable.  This has never been necessary for any Linux that I am aware of.  It doesn't present any problem if you mark a Linux partition as active, it just isn't necessary but it is necessary for windows as it is necessary also to have windows boot files on a primary partition.  And no, there were no bootloader files on the swap partition.

So now you have a blank SSD onto which you want to install windows 7 and Ubuntu, is that correct?  You need to provide a little more info.  What live system do you want to connect to?  Do you have an internal hard drive on the machine with some operating system on it?  How were you planning to install Ubuntu, DVD or flash drive?  So you cannot boot either windows or Ubuntu from the DVD drive, are you sure it is set to first  boot priority.  I was going to suggest you run:  sudo fdisk -l command from Ubuntu to get more drive/partition information but I don't know if you have anything you can boot?

---

### Post by oldfred on 2014-06-30
Grub does not use boot flag with BIOS installs.
Windows has to have a boot flag to know which partition to boot from with BIOS installs.
A few BIOS have to have a boot flag on a primary partition to let you boot in BIOS mode, so we still suggest a boot flag on a primary partition.

gparted has confused things a bit as it uses the boot flag to indicated which partition is the efi partition for UEFI boot. But it really is a very long GUID that UEFI sees and the boot flag is just a way for us to flag the efi partition for UEFI booting. Not really the same as BIOS boot flag.

Is system newer UEFI based or older BIOS based? If newer do you want UEFI or BIOS/CSM?
UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by chris253 on 2014-07-02
Hi Yancek, thanks for your interest.

 I partitioned my 120gb SSD using Gparted from a Live Ubuntu 14.04 DVD. This is currently the only disk on my system, although I have a 500gb external drive for data backups. I am planning to install Windows 7 then Ubuntu from disks to make a dual boot on the SSD. 

My problem is that I cannot manage to boot up windows or ubuntu while the SSD remains connected to the SATA, it immediately hangs at the screen with the Gigabyte splash. With the SSD disconnected I can successfully load a system up from the DVD. I can also stop the load to fiddle with the BIOS settings, and have tried various things at that stage. The problem is that the BIOS only allows me to change the boot priority for devices that it knows about, and with the SSD disconnected the BIOS do not see the SSD as a peripheral so I can't set its priority. 

One other thing I tried with the SSD physically disconnected was to disable the SATA port in the BIOS settings, power off, connect the SSD to the disabled port, then power up and load Ubuntu from DVD. This worked OK but as I expected I was not able to access the SSD with Gparted or Files. I did also try a "sudo fdisk l" but it found nothing.

I am doing all this on my fairly new build PC which has a Gigabyte GA-B85M-D3H mobo. I have an old WIndows XP machine and am wondering next whether to try putting the SSD in that to see whether it is recognised. The other option I am contemplating is buying a second drive for my new PC, installing Ubuntu on that, then trying to salvage the SSD.

Any suggestions welcome.

---

### Post by chris253 on 2014-07-02
Hi oldfred

Thanks for this info. I have just reported some progress in repsonse to yancek.

The boot set up from my Gigabyte board is a dual mode UEFI/BIOS. The default sets it to UEFI. This is my first encounter with UEFI so I really don't know how it works. I found a long and comprehensive article from AdamW on [www.happyassassin.net](www.happyassassin.net) that I am trying to digest.

I don't think I have the option of changing CSM. The Gigabyte manual say that the default is to enable UEFI CSM, and it can only be disabled when OS type is WIndows 8. I will check this out when I next go to BIOS settings.

If you can suggest any way that I can actually 'see' my SSD I would be really grateful.

Regards, Chris

---

### Post by oldfred on 2014-07-02
Do not know if it applies to your model or not, but many Gigabyte boards need iommu setting.

 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset

Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.

turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

---

### Post by chris253 on 2014-07-03
I'm pleased to say that I have got round the problem and managed to load a system from which I can access the SSD.[IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

What I did was load from a Live DVD without the SSD physically connected, get to the BIOS menus and mark the SATA port for the SSD as HotPlug. I  continued the load until Ubuntu came up. I then physically connected the SSD and lo and behold when I loaded Gparted it saw the device!

On the SSD the first partition was unallocated, the second unknown, and the third still had my data. There was no boot flag. I reformatted the first two partitions as ntfs and ext4, and set a boot flag in the first partition.

I did a new Live DVD load and it now loads with no problems.

I don't really understand why it needed a 'valid' SSD, as a brand new unformatted SSD gave no problems when I first installed Ubuntu 12.04.

Now I can set up my dual boot.

---

