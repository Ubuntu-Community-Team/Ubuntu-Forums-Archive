---
title: "Manual partitioning; told it to use windows ntfs as &quot;BIOS reserved boot area&quot;"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by diablo75 on 2012-11-17
So I've done something rather stupid, apparently.  I was trying to setup a dual boot configuration along side a Windows 7 partition and in the process got an alert that told me I needed to specify a partition to be used as "BIOS reserved boot area".  I took this to mean "tell me which of these partitions is normally booted into by default so I can put grub there".  I guess what I was supposed to do was create a totally separate partition for this to be and then designate that as the BIOS reserved boot area.  I've never seen this alert message come up before during a dual-boot setup.

So basically it's just booting strait into Ubuntu now with no grub menu appearing to let me select between Ubuntu or Windows.  Gparted shows the partition to still be present but no longer an NTFS partition, and instead a "unknown" type of partition.  I never told it to format so my hope is that, in a worse case scenario, I can access and pull the data from the Windows partition out of there and start over (if that's what it takes).  My hope is that this didn't inadvertently format/delete the data, but I have a feeling that's what happened.  PLEASE HELP!

Edit to add:  

After shrinking the NTFS partition down by about 50GB and then creating a partition for root, a partition for /home and for swap, I clicked install.  Then this message appeared:

> The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as "Reserved BIOS boot area" and should be at least 1 MB in size. Note that this is not the same as a partition mounted on /boot.

If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition.

Oh I wish I could track down who ever wrote this message and tell them to be a tiny bit more verbose because it borders on being a riddle.  It would be SO nice if, after telling it to use an NTFS partition for this reserved space it said, "Are you sure?".  Sorry, I have to vent a little because I'm walking on egg shells right now.

---

### Post by Mark Phelps on 2012-11-17
First thing I would try is booting into Ubuntu, opening a terminal, and doing "sudo update-grub".  This will launch the os-prober which will search for OS installs on your drive.  If it works, you will see it return something like "Windows 7 (loader) found on sdax".

If it doesn't work (which is likely), that means your Windows boot loader files, and maybe your OS install as well, are gone.

If you can attach the drive to a Windows PC, there are data recovery products you can run that do a good job of locating and recovering files and directories from NTFS partitions.  I would recommend doing that instead of trying to use Linux utilities.

---

