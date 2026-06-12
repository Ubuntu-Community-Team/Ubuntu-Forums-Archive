---
title: "Corrupted GRUB Partition"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by jason8 on 2013-08-08
Hi,

I am dual booting Ubuntu 12.04 with Windows 8. I had some issues in the beginning loading Ubuntu, but I ran boot repair and it fixed them, so now I can boot into Ubuntu or Windows.

I want to increase the size of my Ubuntu partition, but I am encountering a problem, which you can understand from this screenshot from GParted.

[ATTACH=CONFIG]245186[/ATTACH]

There is an "Unknown" 1 MB partition between the free space, created by shrinking the Windows partition in dev/sda4, and the Ubuntu partition in dev/sda6. It is flagged as bios_grub, so I imagine it is a dedicated GRUB partition. However, it appears corrupted somehow. When I click for information, it says

Warning: Unable to detect file system!

and then gives a list of possible reasons.

I cannot resize or move this partition, so I cannot expand my unadjacent Ubuntu partition into the free space.

Is there a way to cleanly move this or create a new dedicated GRUB partition somewhere else and delete this one?

Thanks,

Jason

---

### Post by Bucky Ball on 2013-08-08
Welcome to the forums. Are you attempting this from a LiveCD? If you're not, then you should be. If you are wanting to resize the / partition, you can't be running it as it needs to be unmounted.

Boot from the install CD, get to a desktop and open Gparted there. All partitions should be unmounted (right click to check). Try again.

Apologies if you are working from the CD already and not a hard drive boot. ;)

PS: If it was a boot partition it would be formatted EXT* and marked as /boot. Did you create a separate /boot partition because that is the only way one would get there? When you say grub partition, do you mean the partition grub is installed on? It should be on the boot sector of the hard drive, sda. ;) and wouldn't be showing in your screen shot.

PPS: I actually have a 1.78mb mystery 'unallocated' block, but the system recognises it as 'unallocated' rather than 'unknown'.

PPPS: DO NOT resize the partition Win is installed on using Gparted. Things can get messy. Use Win tools for that and Linux tools for EXT* and other partition resizing (NTFS, FAT fine).

---

### Post by jason8 on 2013-08-08
Thanks.

I happened to take that screen shot from my Ubuntu install, but I have also observed the same thing from a LiveCD. I understand that I can't resize a mounted partition and that the actual manipulation of partitions must be done from the LiveCD. 

However, even from a LiveCD, I cannot move or resize the corrupted "Unknown" partition which is flagged as bios_grub, so I cannot resize the Ubuntu partition. It seems to be an issue with the partition itself.

Jason

---

### Post by Bucky Ball on 2013-08-08
I am starting to suspect this might be something to do with the EFI install, but unfortunately I have zero knowledge about them. I do know that it is not straightforward. At least, perhaps, a clue. I don't know what a 'bios-grub' is but there's a place to start digging.

Grab your spade and enjoy the learning curve ;):

[https://duckduckgo.com/?q=bios-grub](https://duckduckgo.com/?q=bios-grub)

This might be of some interest.

[http://ubuntuforums.org/showthread.php?p=12515676](http://ubuntuforums.org/showthread.php?p=12515676)

Oldfred is a font of knowledge regarding all things boot and grub around here, including EFI installs ...

---

### Post by Bucky Ball on 2013-08-08
Hmm. This looks like it might explain it. 

[QUOTE=joey22]Now I got the message that it will probably not work and that I need the bios-grub partition instead of the /boot partition.[/QUOTE]

From the first post of the second link I gave. You don't need a /boot partition (generally, not just in this situation). You don't get one by default at install and you would need to create one manually, which you didn't. Unecessary. So your issue is not a /boot partition. That is totally different as this looks like it is EFI related and EFI has created that bios_grub section and it is supposed to be there. What a pain. Is everything working fine apart from having an inconvenient blob?

Now you know what it is, and assuming it is there by right and not by stealth, you might begin looking at how to move a bios_grub/inconvenient blob, and if it's possible. Having a sniff myself and it doesn't look simple. Perhaps there are some EFI pages that might explain what is going on and what has happened which might give a few clues as to what it is possible to do. I would suggest, though, that if you *were* able to delete it your Ubuntu wouldn't boot, if that is when it appeared. 

Boot Repair can run a script which gives output on the setup of your machine. Could you run that, create the info file and post back a link here, please?

---

### Post by jason8 on 2013-08-08
> **Bucky Ball said:**
> If it were I, I might begin looking at how to move that inconvenient blob somehow, and if that is possible.

Hi,

Moving the inconvenient blob is exactly the issue, since it is preventing me from expanding my Ubuntu partition. I can think of two possible ways to do this.

(1) Figure out a way to move the blob directly, presumably by uncorrupting this partition and getting GParted to recognize it.
(2) Figure out how to create an identical bios_grub partition somewhere else, use that one, and delete this one.

However, after doing a bunch of research, I am still not sure how to do either, because I am not exactly sure what this bios_grub thing is.

Jason

---

### Post by jason8 on 2013-08-08
> **Bucky Ball said:**
>  Boot Repair can run a script which gives output on the setup of your machine. Could you run that, create the info file and post back a link here, please? 

Already have that, here it is:

[http://paste.ubuntu.com/5963158/](http://paste.ubuntu.com/5963158/)

---

### Post by Bucky Ball on 2013-08-08
Reread my last post. I don't think it is corrupted and I do think it is supposed to be there. It is a Win thing related to EFI and therefore unknown I would assume.

I would probably work around it. Would help if you outlined what you are wanting to do. I notice you have a lot of space and no /home partition. Ubuntu itself will happily fit on 15Gb (and that's generous) if you keep your personal data elsewhere (a separate /home partition or symlinks to a data partition). This lets you kill the install on the / partition if you want/need to and reinstall whilst your data is (hopefully) safe on another partition.

Also, you have no shared partition. Ubuntu will read/write NTFS/FAT partitions without issue, but in Win, you are going to get exactly what you have here for the EXT* partitions, 'unknown'. Win does not read/write EXT* filesystem. If you are intending to share data when on the Win side, you can't access anything on the EXT* partition, which means any personal data you may have on there.

Just a couple of thoughts to ponder ...

PS:

> sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

Yep, present and correct. Doubt that it's corrupted. That is supposed to be there. Try researching BIOS Boot partition. Good luck. Time for sleep here. ;)

* Notice you have the 128mb sda3 mysteriously labelled also. Obviously a Microsoft somthing. What software did you use to do the resizing (apologies if you already mentioned)?

---

### Post by jason8 on 2013-08-08
> **Bucky Ball said:**
> I would probably work around it. Would help if you outlined what you are wanting to do. I notice you have a lot of space and no /home partition. Ubuntu itself will happily fit on 15Gb (and that's generous) if you keep your personal data elsewhere (a separate /home partition or symlinks to a data partition). This lets you kill the install on the / partition if you want/need to and reinstall whilst your data is (hopefully) safe on another partition. 

What I want to do is increase the space I have available to me on Ubuntu.

So are you suggesting that I:

(1) Create a new partition taking up the currently unallocated space.
(2) Move my data from the current Ubuntu partition /dev/sda6 to this new partition.
(3) Delete /dev/sda6 to free up that space.

Do I have to do something else to avoid damaging the Ubuntu install if I follow these steps?

Also, then won't I still have a big chunk of unallocated space cut off from the rest of my hard drive by this irritating blob?

Thanks for all the help.

Jason

---

### Post by jason8 on 2013-08-08
> **Bucky Ball said:**
> * Notice you have the 128mb sda3 mysteriously labelled also. Obviously a Microsoft somthing. What software did you use to do the resizing (apologies if you already mentioned)?

The only resizing I have done so far is to shrink the Windows partition, which I did using the Disk Manager inside Windows 8.

Jason

---

### Post by Bucky Ball on 2013-08-08
If it's a fresh install I'd reinstall on the unallocated space, choose 'Something Else' when you get to the partitioning section of the install, install the OS on a 15Gb / partition (it is a default mount point in there) then do what you like, make a plan and repartition or symlink as required. Delete the other install, keep it to play with, whatever.

Unless you are going to keep digging for a way to move the bios_grub, learn a heap about EFI to try and explain why things are how they are, or do a complete reinstall which would delete sda6 but would, by sheer guesswork, create another bios_grub, and you'd be none the wiser, and assuming you want to keep the current install, you might copy your data to another partition, shrink the /, create symlinks in the /home directory to the directories that were there but are now on the other partition.

There are a mulitude of options so it is about what suits you. I generally sit down with a pen, paper, beverage of choice and work out a solid plan of exactly how it's going to end up when it comes to partitioning. It can often be difficult, and sometimes impossible, to rectify things later. 

A clean, fresh install would clear the way from what is not the unallocated right through to /swap, and if you can figure out what you are doing with the bios_grub and how to put it where you want it, you're sailing. ;)

Bed. Good luck.

PS: Good-o with the Win resize software.

---

### Post by Bucky Ball on 2013-08-08
I haven't made it to bed yet, but I did notice this in your info for sda6:

> 

**WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.**

It does appear to be a /boot partition and the WARNING at the bottom I'm guessing leads to your problem. The grub on the sda MBR is going to boot first. Grub is on sda already and looks to be booting first. 

> ============================= Boot Info Summary: ===============================

 => **Grub2 (v1.99) is installed in the MBR of /dev/sda** and [B]looks at sector 
    1566625792[/B] of the same hard drive** for core.img**. core.img is at this 
    location and looks for (,gpt8)/boot/grub on this drive.

Possibly why sda5 is showing up as 'unknown'. The grub has been fixed and is booting from the MBR, doesn't recognise sda5 at boot, reports as unknown. Just a theory. The boot on sda looks sda6 for the rest of the info. All seems good to there, although no idea why that info is on sda6 in the first place.

This is about how it is set in the BIOS at install, EFI or Gpt (I think). There is no changing it later (don't quote me, no expert), and the show is run by one or the other. I'm guessing sda5 is somehow EFI whilst the MBR in sda has been setup using Gpt. They don't mix. 

Best bet might be to get across EFI and Gpt installs, how to do them, and have another go. Guesswork otherwise and might be attempting something that is impossible in this install/config.

---

### Post by Bucky Ball on 2013-08-08
One final thing. Your Win partitions are EFI:

> Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /mnt/boot-sav/sda1/EFI/Boot/bkpbootx64.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi

Then comes a hiccough:

> /boot/efi detected in the fstab of sda6: UUID=2672-D428	 (sda1)

=================== [B]sda6recordfail=1/grub/grubenv :
recordfail=1[/B]

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
***SecureBoot maybe enabled.***

The last line could be the issue. Also, blkid gives this:

> WARNING: GPT **(GUID Partition Table)** detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

I could be off the mark with this but hope its giving you some clues.

---

### Post by Bucky Ball on 2013-08-08
One final thing. Your Win partitions are EFI:

> Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /mnt/boot-sav/sda1/EFI/Boot/bkpbootx64.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi

Then comes a hiccough:

> /boot/efi detected in the fstab of sda6: UUID=2672-D428	 (sda1)

=================== [B]sda6recordfail=1/grub/grubenv :
recordfail=1[/B]

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
***SecureBoot maybe enabled.***

The last line could point to a clue, even though a LiveSession. Also, blkid gives this:

> WARNING: GPT **(GUID Partition Table)** detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

I could be well off the mark with all this but hope its giving you some clues. Install Boot Repair to your hard drive install and run the script again. Repost. (Think you need to add PPA but you might already have that.)

---

### Post by jason8 on 2013-08-08
Great, thanks for all the clues.

I decided to create a separate /home partition in order to make things cleaner.

Now I have a small partition for the Linux installation, and a separate large partition for all my data.

However, there is still a bunch of unallocated space which is cut off from the large partition because the bios_grub partition is in the way.

I believe that if I can format the 'Unknown' bios_grub partition, I will be able to move it and my problem will be solved for good.

Is there a particular format that would be safe to use?

Jason

---

### Post by oldfred on 2013-08-08
Gparted will show one unformatted unknown partition for Windows system reserved.
       Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you encrypt /home it will show swap as unknown (as it is encrypted and gparted cannot read it).

And if you install Ubuntu in BIOS mode, you have to have a bios_grub partition which is unformatted.

 However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. So  when booting in BIOS mode you have the bios_grub partition for core.img.

But if booting in UEFI mode, you do not install grub to the MBR, but to the efi partition and then you do not need the bios_grub partition, but do have to have the efi partition. Only one efi partition per hard drive.

If you want  to easily dual boot both systems must be installed in UEFI mode or both BIOS. And since Window is UEFI, you need Ubuntu in UEFI mode. 

You could boot Ubuntu if in BIOS mode by going into UEFI can changing to BIOS/cSM/Legacy mode and boot Ubuntu. Then to boot Windows you would have to go back into UEFI turn on UEFI or turn off CSM. Not the easiest way to dual boot.

---

### Post by jason8 on 2013-08-08
I determined that I am booting off EFI by doing

dmesg | grep "EFI v"

which returned

[      0.000000] efi: EFI v2.31 by American Megatrends

Does this mean I can delete the bios_grub partition without an issue? Perhaps there is a way I could temporarily hide this partition just to test?

Note that I needed to run boot repair to get my dual boot to work in the first place.

Thanks for the help.

Jason

---

### Post by oldfred on 2013-08-08
If you are booting with UEFI thru the efi partition, then you do not need the bios_grub partition and can delete it.
Boot-Repair does convert a BIOS install to UEFI if you want.

---

### Post by jason8 on 2013-08-08
Perfect, it looks like all I had to do was delete the bios_grub partition in the first place. But now I have a separate /home partition as well, all of the unallocated harddrive space is being used, and everything is clean.

Thanks for the help everyone.

Jason

---

### Post by Bucky Ball on 2013-08-08
Great news. I told you oldfred was the man! ;)

---

