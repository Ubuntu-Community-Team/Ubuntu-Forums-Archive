---
title: "Fatal Failure Grub Cannot Write Boot Loader"
date: 2016-07-29
forum: New to Ubuntu
---

### Post by allandunn on 2016-07-29
As a new user to Ubuntu, I am trying to set up a dual boot with Win10 and Ubuntu 16.04 which I purchased on DVD.  This is on an HP laptop.
I have an external USB 3TB NTFS disk on which I made two partitions for Ubuntu prior to installation.  The swap is now sda5 with an ext4 sda6 of nearly 100GB.
I run the installation by booting the 16.04 installation DVD.  It runs smoothly until what I believe is the end where it gives a Fatal Error message that it cannot write (with Grub, I assume) a boot loader to sda.  It asks for another mount point.  I selected sda6 which does not work. Should I write it to sdc or sdc1 which are Windows 10 partitions?  I do not want to destroy Windows 10 in any way.  

I had many mis-steps along the way, but I did previously choose sda6 as the / mount point.  Since then the option I chose was to erase 16.04 and start a new installation.  That is where I ran into the above problem.  I tried both the 64 bit and 32 bit dvd's with the same result.

---

### Post by oldfred on 2016-07-29
If you have a newer system, only use the 64 bit version.

You have a 3TB drive, so must use gpt partitioning. Did you?

And is Windows 10 installed in UEFI or BIOS boot mode?
Ubuntu should be installed in the same boot mode.

But with gpt, you must have either an ESP - efi system partition on the drive seen as sda. But best to have an ESP on drive you install Ubuntu into also.
Or if system is BIOS, you must have a bios_grub partition on the gpt drive and install grub to that drive, not to a partition.

Post this:
sudo parted -l

---

### Post by allandunn on 2016-07-29
Fred,  Thanks for your reply. 

First I don not have Ubuntu properly loaded yet, so I am answering from my Windows partition.  You stated using gpt partitioning.  I partitioned using a Windows 10 command.

Second, I saw on a You=Tube video using an efi system, but that is the first I heard of it.  I am assuming I am using BIOS.  

Working from the Install on the 16.04 dvd, how do I install Grub to a drive and not to a partition?  Remember I am not yet using the Command Line as I don't have access to it.

---

### Post by oldfred on 2016-07-29
The live installer also has terminal mode.
You should use the live installer in live mode for at least a bit to see if it works ok with your system.
If you have issues with live installer then you surely will have issues once installed.

Grub's default install is always to a drive like sda, never to a partition like sda2.
And even using Something Else where you manually create or use existing partitions, the default choice of boot loader will be a drive.

I prefer to have swap at end of drive so it does not get in the way of future changes. But not critical if your first install.

---

### Post by allandunn on 2016-07-30
I  did use Live Installer 64 bit successfully to access web sites using the Firefox web browser.  I also tested my sound issues, but I needed to do more to get a video on a web site to play.  I saw references go gflash in a book, but ran out of time to try.  I assume Flash will load in the full installation.

Just how do I go about (using Live Installer if needed) creating a partition for Grub?  And how large should it be?

Will I do better instead to use a thumb drive installation on a 64 GB drive as opposed to my partitions on the external drive?

---

### Post by oldfred on 2016-07-30
If you want a full install in you r3TB external you need to convert it to gpt.
With your oddball configuration, I do not know if gdisk will convert correctly or not?

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

Normally creating a USB flash drive installer, erases the entire drive. But you only need 2GB for the installer. The install needs more, I normally suggest a 25 GB / (root) partition and then a large /home partition.

If using MBR partitioning on smaller drives.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu) 

If installing to your 3TB drive with gpt partitioning. For BIOS boot you need a 1 or 2MB unformatted partition with the bios_grub flag. If installing in UEFI boot mode you need a FAT32 formatted ESP - efi system partition. No matter what boot mode I plan to use I always add both the bios_grub and ESP to every new drive when partitioned as first partitions on drive. UEFI recommends ESP be first.
[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu

[/URL] GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 

[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]
[/URL]

---

### Post by grahammechanical on 2016-07-30
> I assume Flash will load in the full installation.

Not necessarily. Adobe Flash is proprietary software and it is not in the Ubuntu software repositories. But the repositories do contain a flash plugin installer. And there are two ways to get it.

During installation we tick the box "Install third party software." And now we will get a proprietary video driver and some proprietary audio & video codecs and the flash plugin installer which will install Adobe Flash for us.

The other way to do this is to install Ubuntu Restricted Extras after installation. It is also possible to install the flash plugin installer package on its own, if we know how, but the other audio & video codecs are also useful to have.

Regards.

---

### Post by allandunn on 2016-07-30
thanks for help.  I have a lot to learn here.  Just a reminder, While I have a 3TB external drive, I plan to use 100G for Ubuntu if that be possible.

---

### Post by oldfred on 2016-07-30
I like to have multiple installs of Ubuntu. One main working LTS version and others to experiment with. So I typically install / (root) in a 25GB partition, but then have other partitions for data. A large /mnt/data partition for my files that normally are in /home. I often add another for ISO as I normally directly boot the ISO with grub's loopmount and install from that to another drive. And then may have backup partitions on other drives that I mount also.

       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

