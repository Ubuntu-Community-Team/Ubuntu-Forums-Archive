---
title: "Redo NTFS"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Palu on 2008-08-18
I totally nuked my NTFS partition to install Ubuntu. I wanted only the native Linux partition and no sign of Windows... Now I need to run a program that uses DirectX 9. It's purposefully invasive into memory spaces of other applications, so I doubt Wine would be able empower it in the hazardous way that Windows does, lol--at least not within my own ability level.

--I don't mind reformatting and starting from scratch with Ubuntu (I know Windows is a pain to install second).
--I'd like to reformat the whole drive (it's in 3 partitions at the moment) to NTFS and deal with Linux via Wubi. How do I do that? Do I need to delete the MBR too? If you send me to a keyword for what tool / command to use, let me know. All the utilities or commands I find are for changing NTFS into ext3...
--The Win XP install CD won't recognize the hard drive with ext3 (or maybe it's Grub), so it won't do any formatting or anything for me. It jsut goes to a blank screen and Microsoft.com tells me to ask my Linux friends how to get NTFS back. :( Evul Microsoft...

Caveat: I'm sure there are a million threads on this, but looking for "NTFS" is too broad to find them. :)

Thanks so much!

---

### Post by OldGrey on 2008-08-18
You should be able to reformat your disc using the partition tool on the live CD.

---

### Post by Palu on 2008-08-18
I have a live CD. I don't remember that in the boot menu or anything. Do I boot up the cd and use fdisk plus some commands or something? :) I know big words sometimes, but that's all I know...

---

### Post by Gone fishing on 2008-08-18
Options include:

1 Boot up on the XP start up disk - XP will give you the option to delete the existing partitions, you could asign X amount of you drive to XP and leave a space for a new ubuntu install. XP will overwrite the mbr and grub.

2 You could delete one of you existing partitions using gparted and install XP into the new free space. Then fix mbr and grub (this is not difficult).

3 You could resize your Ubuntu partitions to make space for XP install XP and the fix the mbr and grub.

---

### Post by Palu on 2008-08-18
> **Gone fishing said:**
> Options include:

1 Boot up on the XP start up disk - XP will give you the option to delete the existing partitions, you could asign X amount of you drive to XP and leave a space for a new ubuntu install. XP will overwrite the mbr and grub.

2 You could delete one of you existing partitions using gparted and install XP into the new free space. Then fix mbr and grub (this is not difficult).

3 You could resize your Ubuntu partitions to make space for XP install XP and the fix the mbr and grub.

1: Booting from the XP disk results in a blank screen right after it says it's checking my hardware config. A Google search reveals that it's choking on the MBR, file system, or Grub. No workaround is available with only using the XP cd.

2: I think I'm comfortable trying this. Gparted looks pretty intuitive. Hopefully if I simply delete the partitions then the XP CD will work...

3: This might not be much harder than 2, if at all, but I think fixing the MBR and grub will be a challenge... though maybe that's OK. People here reply so fast and I might be able to Google that. :)

---

### Post by kansasnoob on 2008-08-18
> --I don't mind reformatting and starting from scratch with Ubuntu (I know Windows is a pain to install second).

Dual booting with Linux installed first is NOT that hard. In fact that's how I did my very first dual boot! It only requires a bit of work with GRUB. This tutorial is very simple and straight forward:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

But, if you really just want to dump Ubuntu altogether page 2 of that tutorial shows you basically how to use Gparted (aka, partition editor), of course you'd just want to delete everything and leave everything unformatted, then you can tell the windows installer whether to use FAT32 or NTFS.

---

### Post by Gone fishing on 2008-08-18
> 1: Booting from the XP disk results in a blank screen right after it says it's checking my hardware config. A Google search reveals that it's choking on the MBR, file system, or Grub. No workaround is available with only using the XP cd.

Mmm I'm surprised on my XP disk this works (is yours a very old XP disk that doesn't recognize big disks? or an iffy copy?) any way you can easily delete all the partitions using gparted.

---

### Post by Palu on 2008-08-18
> **Gone fishing said:**
> Mmm I'm surprised on my XP disk this works (is yours a very old XP disk that doesn't recognize big disks? or an iffy copy?) any way you can easily delete all the partitions using gparted.

I replicated the process on a nearly identical laptop of the same make (Dell, but a model 1 year newer) and same Ubuntu install. The CD was fine. The weird part is that the CD was the same Windows CD tried on both. My only guess is a variance in the harddrive?? :) No clue what else it could be...

---

### Post by Gone fishing on 2008-08-18
The other thing that comes to mind is the XP disk is not recognizing a SATA drive, on some PCs you nave to load SATA drivers onto a floppy and load these drivers during the XP CD boot up it asks you to press a key to load custom SCSI drivers.

The other possibility is running XP inside Ubuntu using virtualbox. Personally I wouldn't run Ubuntu from Wubi but give it its own partition - incidentally you can get XP to read Linux partitions using Ext2IFS (this works very well)

---

### Post by markjensen on 2008-08-18
XP not being able to see SATA is a good guess.

Additionally, the problem could have something to do with requiring an OEM 'restore' partition.   Or if it is that the MBR is causing the problem with the Windows CD (I have seen this only once, it was weird), you can boot the Ubuntu CD live and do a **sudo dd if=/dev/zero of=/dev/sda bs=512 count=1** to completely zero the MBR.

I would save the MBR wipe as the very last item. ;)

---

### Post by Palu on 2008-08-18
Dell.com won't list any SATA drivers for my model. I double checked my original product specs (which I have in digital format in Google docs, but I have no recovery CD). It seems I do indeed have a SATA hard drive. Did Dell omit the driver so I'd need their specific type of XP install CD? I've seen some posts with negative opinions on the success of SATA drives when you use the wrong driver. I have no info on who manufactured my specific drive.

---

### Post by markjensen on 2008-08-18
If you have SATA, standard XP will not recognize it (without the add-in drivers on floppy).

However, many BIOSes offer a compatibility mode for their SATA to make it look like PATA IDE.   Did you look for that in your BIOS settings?

---

### Post by Gone fishing on 2008-08-18
OK Ubuntu runs so it knows what hardware you have - have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=891268&highlight=hardware+listing](http://ubuntuforums.org/showthread.php?t=891268&highlight=hardware+listing)

the key commands seem to be sudo lshw and dmesg


Hopefully you can then find the mother board and therefore the driver.

---

### Post by Palu on 2008-08-19
> **markjensen said:**
> If you have SATA, standard XP will not recognize it (without the add-in drivers on floppy).

However, many BIOSes offer a compatibility mode for their SATA to make it look like PATA IDE.   Did you look for that in your BIOS settings?

I'm not buying a floppy drive. I haven't used one in about 8 to 10 years. Can I do it with a USB drive? And how do I find the drivers if Dell wont' list them? Perhaps I can find it using the advice by Gone Fishing, but I forgot to try last night. I'll have to wait another 8 hours now. :) Thanks guys. You're awesome!

My BIOS are pretty pathetic. It's almost entirely informational. Nothing about hard drives is configurable.

---

### Post by markjensen on 2008-08-19
To be honest, the part about installing XP onto SATA drives might not be best suited for a Linux forum (though there are probably lots of people who have done so).   I, however, am not. :(   Been 100% Linux (no Windows) for approaching 6 years now.

I have heard of something called 'slipstreaming' drivers into a customized XP CD.   I googled and found a procedure that seems to do so without needing a floppy drive: [http://www.msfn.org/board/Unattended-install-SATA-drivers-and-NO-t13173.html&hl=Si3112r](http://www.msfn.org/board/Unattended-install-SATA-drivers-and-NO-t13173.html&hl=Si3112r)

Once you have XP installed into a partition of the size you want, this installing Linux thing is gonna be a BREEZE!:)

---

### Post by Gone fishing on 2008-08-19
> How do I find the drivers if Dell wont' list them?

If you run the commands shown above it will give you lots of info about your system (you could run them from the live CD).

> I'm not buying a floppy drive. I haven't used one in about 8 to 10 years

Well it's sad but true XP is that old and crap. I suppose you could try cloning the HD from another similar system that uses IDE drivers.
 
But how about running XP in Virtual Box?

---

