---
title: "How to partition a fresh HDD?"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by hilchev on 2012-11-03
Hi guys, I'm a recent convert and although I have a lot of experience with linux OS's I've never installed one as a standalone OS. Yesterday when I tried to install Ubuntu 12.10 and partition it manually with the built-in tools I failed miserably. I've searched and read about this but I couldn't seem to find something to enlighten me about the process.

So please, partitioning with the built in tool, for technically knowledgeable dummies.

---

### Post by oldfred on 2012-11-03
I prefer gparted. If it is only going to be Linux never Windows you may want to consider gpt partitioning as that is the new partitioning method. Or you can stay with the standard MBR(msdos) which everyone knows and understands.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

I now use gpt for all new drives. I even used it for a 16GB flash drive without issue.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

Lots to review, if you have specific questions come back. Others may have different partitioning suggestions.

---

### Post by critin on 2012-11-03
> **hilchev said:**
> Hi guys, I'm a recent convert and although I have a lot of experience with linux OS's I've never installed one as a standalone OS. Yesterday when I tried to install Ubuntu 12.10 and partition it manually with the built-in tools I failed miserably. I've searched and read about this but I couldn't seem to find something to enlighten me about the process.

So please, partitioning with the built in tool, for technically knowledgeable dummies.

In 'standalone', do you mean unbuntu will be the only OS on the disk?
If you know absolutely nothing about partitioning and instructions don't seem to help, just let it install on the entire disk.  (If it's the only os)

The option is something like 'use entire disk'.  It will make a swap partition itself,  you do nothing.

If the disk is large and you only want ubuntu on a portion of it, you will need to learn something about partitioning.  Sorry.  There are some good graphic tutorials on the web.

---

### Post by SeijiSensei on 2012-11-03
Is there some reason why the default partitioning doesn't work for you?  Are you asking what a good partitioning scheme might be?

I always choose "manual" partitioning because I have some partitions that I do not want the installer to touch like one with Windows and another that contains my /home.

If you want total control over the partitioning I recommend not doing it through the installer but rather using the "Try Ubuntu" option when you boot from the installation disc.  Then open a Terminal and use "fdisk /dev/sda" to partition the hard drive as you'd like it.  My standard arrangement consists of a small primary partition for /boot and a large extended partition for everything else.

fdisk uses single-letter commands.  So to create the boot partition, I'd use "n(ew), p(rimary), then enter a "1" to create the first partition.  Accept the starting block it offers, then use +512M for the ending block.  It will create a primary partition approximately 512 megabytes in size.  Then enter (t)ype, 1, and 83 to create a Linux partition.  Now use "n(ew)" and "e(xtended)" and accept the default start and end points.  A single extended partition will be created that fills the remainder of the disk.

Now we're going to create three partitions in the extended area.  Use "n(ew), l(ogical)", accept the default starting block and enter +10G to create a 10 gigabyte partition to hold the operating system.  Now mark it for Linux by setting the type to 83 as before.  Follow the same procedure to create another partition to be used for swap.  In this case the type is 82.  If this is a laptop, swap needs to be at least as large as physical memory to enable hibernation.  Usually the standard is twice the size of physical memory, though if you have >4 GB, you can probably avoid using a swap partition entirely.

If Linux is the only OS that you will be using, I'd create one more partition that encompasses the rest of the disk accepting the defaults for start and end.  If you then type "l(ist)" to list the partitions, you should see five entries (if you created a boot partition):

/dev/sda1  - 512 MB  - Linux
/dev/sda2  - large   - extended
/dev/sda5  - 10 GB   - Linux
/dev/sda6  - 2xMem   - Linux swap
/dev/sda7  - rest of /dev/sda2 - Linux

When you're done, type "w" to write the partition table to the drive, then "q" to quit.  Now reboot and run the installer.  When you get to the partitioning scheme choose "manual".  

On the page that follows, pick /dev/sda1, then Edit.  In the dialog that follows choose ext2 for the filesystem (it is too small to need journalling systems like ext3 or ext4), then /boot from the drop-down box that determines the mount point.  Follow the same procedure for /dev/sda6 except you should now choose the ext4 file system.  Assign that to the mount point /.  Finally, have it use ext4 again on /dev/sda7 and pick /home from the drop down.  You're done; move to the next step.

You can create the same partitions using the manual installer, but if that doesn't work for you, partitioning in advance of installation with fdisk is another option.

If you would prefer a graphic partitioner, you can run "gparted" from the installation disk in the "Try Ubuntu" mode and use that to partition the drive.

---

### Post by hilchev on 2012-11-03
Thank you for the quick and useful replies gentlemen! My idea is basically this - I acquired a laptop which had windows 7 64 bit  installed ( because of the 4gb ram). You can guess my horror just by reading the last sentence. It was slow, it was SLOW, and it was buggy. Since this is mostly a work laptop I decided that I can freely use a Linux distribution since I won't be doing hardcore gaming on it.
I've installed several distributions before but always using a 3rd party software(partitioners ), either from a flash drive or disk right before i installed.
For personal reasons I didn't want to use the method explained above, so I decided that i can use the built-in tool.The problem is, that I do not understand a thing the manual partitioner shows me(because of me trying to rush the installation i accidentally wiped the whole HDD, not just the Windows partition). I have no knowledge of the filesystem that the linux drives use (ext2, ext4 and the others like that), they just don't mean anything to me.

What i'm trying to do is simple -> Wipe the HDD, make it into a (root), a (home)  and one swap. What's the best way to do that?


I will read what you gentlemen posted and try to comprehend it, but in the meantime, asking another question hurt nobody :)

EDIT: I did what i wanted, THANK YOU so very much for the quick assistance!

---

### Post by Peripheral Visionary on 2012-11-04
Hi!  Maybe I can help, being an equally non-technically-inclined "ordinary" user.  I too used the built-in partitioner (choose "manually") when I installed Xubuntu 12.04 on this old hand-me-down hardware (and on another computer recently).  I chose **ext4** for the filing system because it's been completely reliable on this computer since it was converted from Windows XP to Linux.

I use three partitions on mine. The first partition is [COLOR=Purple]**Linux Swap**[/COLOR], and it is 1 GB in size (because that's twice my computer's RAM, which is what is recommended).  

The second partition is [COLOR=Purple]**/**[/COLOR] (root) which is 20 GB in size. That's a lot more room than Xubuntu needs (my current install is only using 5 GB!), but I wanted it to have plenty of room since I only use the LTS releases for 3 to 5 years at a time.  Maybe 20 GB is way too much, but it's an 80 GB hard drive anyway.

Taking the rest of the drive is [COLOR=Purple]**/home**[/COLOR]. That's where all my settings, e-mail settings, bookmarks, pictures, music, school stuff, documents, and everything else goes. 

If there's nothing on my HDD at the time, I have the partitioner format all those partitions. If I am re-installing and want to save all that stuff in [COLOR=Purple]**/home**[/COLOR], I simply un-check the "Format this partition" box and all that stuff is preserved!  Of course it's never wise to repartition a drive if you haven't backed all that stuff up to external media. But so far whenever I have installed a new Linux on my HDD and preserved the /home partition I have never lost any data.

The only time that may be a problem is when old settings (preserved in [COLOR=Purple]**/home**[/COLOR]) are not compatible with newer software.  I found this out when my friend's old Xubuntu 10.04 settings wouldn't work properly when I installed Xubuntu 12.04.  That's when you have to delete old settings for new ones, etc., but that was no big deal, even for me.  I hope this helps you a little, from a non-technical user's point of view.

---

