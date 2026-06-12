---
title: "Problem installing Ubuntu 14.04 in my new HP Laptop"
date: 2015-01-17
forum: New to Ubuntu
---

### Post by Alfredo_Salinas_Ma on 2015-01-17
Hi guys, I have a new HP Laptop Model f7v04lt#abm.
I'm trying to make a dual boot Windows 8.1 and Ubuntu, however, when I try to install ubuntu it says that there is no other Operative system installed. 

Any idea how can I solve this problem?

Thank you very much

---

### Post by Bucky Ball on 2015-01-17
Welcome. You probably have secure boot on. I think there is also fast start. I don't use Win so you'll have to look. You need to [switch secure boot off.]("http://www.maketecheasier.com/disable-secure-boot-in-windows-8/") Windows hibernates so the installer doesn't see it or it's partition.

---

### Post by Sef on 2015-01-18
[Ubuntu Secure Boot]("https://help.ubuntu.com/community/UEFI")

---

### Post by Gordonbp531 on 2015-01-19
> **Bucky Ball said:**
> Welcome. You probably have secure boot on.

Secure boot doesn't affect this - it's a bug in Ubiquity - although nothing seems to have been done about it,
See this bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1249564) which I reported in 2013......

---

### Post by Gordonbp531 on 2015-01-19
> **Sef said:**
> [Ubuntu Secure Boot]("https://help.ubuntu.com/community/UEFI")
That article makes a complete mountain out of a molehill.
no need to turn either Secure Boot or fast Boot off at all.

1. Create free space on HDD in windows.
2. Boot from live CD/DVD/USB
3. Choose "Something else"
4. Create two partitions for / and Home plus a swap area
4. Install GRUP on the EFI partition. (Computers with pre-installed Windows 8 have a EFI partition already)

It's as easy as that....

PS - I've done this successfully on two totally different makes of computer with Windows 8 pre-installed...

---

### Post by oldfred on 2015-01-20
Use Windows own partitioning tools to shrink the NTFS partition and reboot immediately so it can run chkdsk and make repairs for its new size. Then use gparted or installer to create new partitions using Something Else.
HP's also have modified UEFI to only boot the UEFI entry that says "Windows", so we have to do work arounds.
       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

Most with HP find that making the hard drive boot entry in the efi partition /EFI/Boot/bootx64.efi really be grubx64.efi (non-secure boot) or shimx64.efi (secure boot). Then in HP's UEFI the hard drive boot entry should work.
        HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

            HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)

            Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

---

### Post by Jonathan Precise on 2015-01-20
HP isn't really dual-boot friendly. I'm in fact writing from an HP 2000 NoteBook PC, and it cost me a ton to set a menu to choose whether I want to use Windows or Ubuntu. From what I'm experiencing, HP is set to only boot from EFI/Microsoft/Boot/bootmgfw.efi. You can either use the "Something Else" option (after previously having shrunk the partition from Windows, found in Control Panel -> System -> Admin Tools ("Create and delete disk partitions" right under Admin Tools) or something like that, just look for it there), in the "Free space", make an ext4 partition, size all of the free space MINUS the amount of RAM (memory) you have on your laptop, mount point as / , then another partition with the remaining space, a "swap" partition to be exact. Then apply changes, open a terminal, type in "sudo -i nautilus" (no quotes), go to /boot/efi/EFI/Microsoft/Boot/, rename bootmgfw.efi to bootmgfw-win.efi. Then go two directories up, then [download rEFInd]("http://sourceforge.net/projects/refind/files/0.8.4/refind-bin-0.8.4.zip/download"), extract the files from the zip file (the 64-bit, x86_64, x86-64, or x64) into a folder called rEFInd, then copy its contents to EFI/Microsoft/Boot/, then copy/paste refind_x64.efi, with the new name of bootmgfw.efi, and FINALLY, give yourself a great pat on the back. YOUR DONE! You have just completed Dual-boot on an HP Laptop!

If all of this does not work, then rename EFI/Boot/bootx64.efi to EFI/Boot/bootx64-win.efi, copy the contents of EFI/rEFInd/ to EFI/Boot/, then copy/paste refind_x64.efi, with the new name of bootx64.efi, and FINALLY, give yourself a great pat on the back..., again. YOUR DONE! You have just completed Dual-boot on an HP Laptop!

If none of this works, post back, and tell us what happened.

---

### Post by verymadpip on 2015-01-21
Hello all.
Jonathon Precise, is this all done from a Live environment?
I'm guessing that the rEFInd install is done from the installed OS...?

I'm jumping in on this because I eventually gave up with my HP 11x360, but only because Ubuntu would neither shutdown nor reboot correctly.  I may tray one more time with the info you've provided here.  (There were also issues with getting it to boot into a live environment consistently, but that's another story).

---

### Post by Jonathan Precise on 2015-01-21
Hello verymadpip.

Yes, Everything should be done from the live environment (the install is obviously using the installer in the Live environment), including the rEFInd install, so that the OP can actually boot the installed Ubuntu in the first place. I don't think that's going to fix the shutdown/reboot problem. I shall make a Google search to see what I find.

Regards.

EDIT: Sorry, didn't find anything.

---

### Post by oldrocker99 on 2015-01-21
One thing not mentioned. Before repartitioning; DEFRAG the NTFS partition first; Windows scatters files all over its paritition, and fragments them. All Linux distributions write files to the smallest contiguous free space that will hold the whole file; NO fragmentation!

---

### Post by verymadpip on 2015-01-22
Hi Jonathon Precise.
Thanks for having a look anyway.
I tried a bunch of things for the shutdown/reboot issue before throwing the towel in & nothing worked.
It's a shame really, because I could boot into Ubuntu, albeit by having to change the boot device at startup, but the restart or shutdown would hang requiring a hard power off.

If I'm feeling brave I may try one more time following your steps.

Thanks again.

---

### Post by Jonathan Precise on 2015-01-22
> **oldrocker99 said:**
> One thing not mentioned. Before repartitioning; DEFRAG the NTFS partition first; Windows scatters files all over its paritition, and fragments them. All Linux distributions write files to the smallest contiguous free space that will hold the whole file; NO fragmentation!

+1. Thanks for telling me this, I forgot to add it to the post.

In fact I can't stress this enough, how defragmentation can save a broken Windows install or the ability to shrink a partition.

---

### Post by Jonathan Precise on 2015-01-22
> **verymadpip said:**
> Hi Jonathon Precise.
Thanks for having a look anyway.
I tried a bunch of things for the shutdown/reboot issue before throwing the towel in & nothing worked.
It's a shame really, because I could boot into Ubuntu, albeit by having to change the boot device at startup, but the restart or shutdown would hang requiring a hard power off.

If I'm feeling brave I may try one more time following your steps.

Thanks again.

Might be fixed with latest Ubuntu, try the noefi or acpi=off if still not working, both might bring other problems, though...

---

### Post by Derrick_Katula on 2015-01-23
Try this tutorial [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by oldfred on 2015-01-23
While this is Mint, it may be similar?

 black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)

---

