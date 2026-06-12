---
title: "[SOLVED] Multiboot problem - Ubuntu and Xp"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by melrokz on 2008-08-04
Hi! I'm Melvin from India.
I've formatted my Xp NTFS partition and tried to reinstall xp using the Xp CD. the CD did boot, it only gave 1 message 'Inspecting ur hardware configuration...' and then the screen went blank. could it be a problem of the overwritten MBR by ubuntu? In this case, how to restore xp mbr without the xp CD? Or, what else could be the problem?

---

### Post by prshah on 2008-08-04
> **melrokz said:**
> 
 tried to reinstall xp using the Xp CD. the CD did boot, it only gave 1 message 'Inspecting ur hardware configuration...' and then the screen went blank. could it be a problem of the overwritten MBR by ubuntu? In this case, how to restore xp mbr without the xp CD? Or, what else could be the problem?

No it's not related to Ubuntu's taking over the MBR. However, if you're convinced it is...

If you want to restore the XP MBR, you _need_ (and, according to your post, you have) the XP CD. If the XP CD doesn't boot I'd suggest you check your media and/or your drive.

For a (dirty) solution, try this: Get to a machine with a working XP, boot with the live CD, then give the command ```
sudo dd if=/dev/sda of=~/Desktop/mbrbackup bs=446 count=1
```

The file which is created in the live CD desktop is a backup copy of the MBR. Save this to a usb key or external drive.

Now take both the key and the live CD to your non-XP machine. Boot using the live CD, ensure all partitions are unmounted and swap turned off, then copy the mbrbackup file onto the Desktop and give the command ```
sudo dd if=~/Desktop/mbrbackup of=/dev/sda bs=446 count=1
```

Make sure the "boot sector write protect" / "Virus protection" option in the BIOS is turned off, if you have either. Be very careful with the "dd" command, a single mistype will instantly wipe out data.

You should also be aware that this procedure will remove ubuntu's grub, leaving your ubuntu inaccessible until you reinstall grub.

Finally, you do this at your own risk. I take no responsibility for this advice. I do not think this is a solution to the original problem (screen goes blank after "inspecting hardware configuration", but it's something for you to try failing all else.

Once again, note that you will lose access to ubuntu if you do this.

---

### Post by Funk Phenomena on 2008-08-04
Not sure fixmbr will work since you formatted the ntfs partition, but that is one way to fix the mbr.  Even if it messes up grub, there is a way to restore that too without much effort.  For fixmbr, it goes something like boot off the xp cd, select install till it gives a repair console option, choose that, then type fixmbr and acknowledge the disaster warnings.  It clears grub, but the fix is relatively easy.  Google fixmbr grub.

---

### Post by melrokz on 2008-08-04
could the problem be due to the dual RAM - one 256 MB and one 512 MB?

---

### Post by LowSky on 2008-08-04
XP is annoying, does the Hard drive have any free space that is either formatted to NTFS, or FAT32. if not Ubuntu, using gparted can create FAT32 partitions

---

### Post by knightcoder on 2008-08-04
I would always install Windows software first and then Ubuntu/any other Linux. Cos Windows wants to be the only OS on your computer.

---

### Post by melrokz on 2008-08-04
i installed the same way! this is not an install issue, but an issue that popped up when my windows installation got corrupt. then, i had to format the drive using Acronis disk director's boot cd, since the win Xp disk wouldn't run and it still doesn't.

---

### Post by mupto on 2008-08-04
i agree installing windows first is the easiest way. although while trying vista i did come across a very easy bootloader program to add linux to it easily. but it doesnt work with xp.

---

### Post by snarley25 on 2008-08-20
I have had problems in the past with Linux overwriting a windows boot partition when multi-booting.  In fact I got so fed up with using software boot loaders that I began researching ways to use a physical switch to boot different operating systems.  If you have at least two SATA drives, you can can build a low-cost switch yourself! See [www.thesataswitch.com](www.thesataswitch.com) for detailed instructions on how to build one!

---

