---
title: "Can't install OS"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by socca12 on 2008-04-21
Hi,

I've gotten Ubuntu 7.10 installed and everything works wonderfully, the only problem is that I now want to dual boot with windows purely for BF2.  When I put in the windows install disk, it loads up and looks for a hard drive but it cant find any even though I had windows previously before I decided to switch to linux.  How do I get windows to recognize my hard drive?  I really want to play BF2!

Thanks for any help you can give!
Cam

---

### Post by ace007 on 2008-04-21
You are much better off installing Windows first and then resizing partitions to install Ubuntu.  If you dont have too much work already in Ubuntu, that would be a suggestion.

I dont know for sure, but the issue may be that the drive is in a non-compatible Windows format.  This format is ext3.  I do not know if the Windows installer has any issues with that.  I've never tried.

---

### Post by NightwishFan on 2008-04-21
I do not know much about installing windows, I wonder though do you have a partition free? Perhaps use the ubuntu live cd to create a small partition for windows before hand. (also note that windows will erase grub and ignore linux so you will need to reinstall grub)

---

### Post by socca12 on 2008-04-21
I definitely have a blank, 20gb partition that is just free space with no file type.  When I installed ubuntu I left the space there in case I decided later that I needed Windows for something.  I also tried once removing linux and completely wiping the drive using partition magic and I still could not install windows.

I've no clue what to do #-o

---

### Post by tango_ninja on 2008-04-21
try using a tool such as **gparted** to reformat the blank partition (ntfs or fat32). It doesn't make much sense logically (XP should detect it) but its worth a try.

---

### Post by ace007 on 2008-04-21
I'm not sure either.  But if you eventually get it to work, Windows will overwrite the boot loader (Grub) and erase all knowledge of Ubuntu.  It may even erase Ubuntu altogether.  The windows installer wasn't really designed with people like us in mind.  I wonder if this is an common issue.

---

### Post by alpdo on 2008-04-21
install windws first then install ubuntu:guitar:

---

### Post by alpdo on 2008-04-21
make partitions for windows and for ubuntu...it work for me... i installed windows first... during installation time i created a partition just for windows then leave the rest of the drive in raw partition
intallation ubuntu use manaul partition  :guitar:
:popcorn:

---

### Post by crav on 2008-04-22
Don't know if this will help your problem, but this link helped me install XP with ubuntu already there.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by kansasnoob on 2008-04-22
I've used the following tutorial and it works perfectly:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

If you can't burn the GParted Live CD, the Ubuntu Live CD works just fine (you'll just choose to run the live CD when it boots rather than install) to partition the drive, using GParted (System>Administration>Partition Editor). The "fiddly" thing they mention is that after each change GParted has a tendency to close and you must reopen GParted repeatedly until all changes are completed.

So, if you can burn the GParted Live CD, do so, it's just easier to work with.

Also, pay very close attention to the necessary changes to GRUB or you'll end up with an un-bootable system. I'd say this is the primary reason to perform a dual-boot with Windows installed first. Ubuntu is very intuitive when being installed second so you can avoid all of the fiddling with the grub menu unless you want to assign Windows as your primary boot.

The other reason to install Windows first is that some software programs only want to install to Drive C, and installing Windows second will result in a different drive assignment (mine was G). The one that really snagged me was my scanner driver but I got help with that from a pro @ $40.00/hr! Luckily it was simple and he only charged me $25.00!

---

### Post by Helios38 on 2008-04-22
Kansasnoob, as far as i know Partition Editor was removed after 6.10


just wipe the drive, install windows first, its ok to use the entire drive for this.


then pop in the ubuntu disk, and reboot.


install it, and select the partitioning option that has a small slider and adjust the partitions as you see fit. then when you start up again, you will be greeted with a text based OS loader, giving you about 10 seconds to decide what OS to load, with the primary being ubuntu.

---

### Post by kansasnoob on 2008-04-22
I just had a DUH moment! If Windows is not even recognizing the hard drive I'm wondering if you have a SATA drive? Maybe need a boot disc for SATA/RAID drivers?

This is one of the reasons for me wanting to just kick windows to the curb!

My primary reason is the ever worsening battle over reinstalling Windows to the same computer after even the slightest hardware upgrade!

There are actually a number of scenarios. What version of Windows? Is the disc system specific OEM, retail, system builders OEM, or an upgrade version? Upgrade versions won't install unless there's some version of a prior windows system to "see".

System specific (HP, Dell, etc.) discs can be very much "hit-n-miss".

---

### Post by kansasnoob on 2008-04-22
"Kansasnoob, as far as i know Partition Editor was removed after 6.10"

I just used it this morning off of the 8.04 RC Live CD to delete the 7.10 partition on a 8.04 RC/7.10 dual boot. Now, I know it's not "installed" in the normal installation, but it's there ready to use.

You can install GParted with synaptic but it's almost worthless because you can't work on active partitions.

But, it's there.

---

### Post by corowakid on 2008-04-22
> **socca12 said:**
> I definitely have a blank, 20gb partition that is just free space with no file type.  When I installed ubuntu I left the space there in case I decided later that I needed Windows for something.  I also tried once removing linux and completely wiping the drive using partition magic and I still could not install windows.

I've no clue what to do #-o

Windows will only instal on the primary partition, usually C:. All instructions say to instal Windows first, so it is on the primary partition, and then instal Linux.

I'd use GParted to delete all partitions, instal Windows using the instal disk (which will format the drive as FAT during the instal process) and then use GParted to partition in the normal way. Then instal Linux.

---

