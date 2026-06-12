---
title: "Dual Booting w/ Win 8.1 and UEFI"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by mevets on 2014-03-31
I have a VAIO Fit 15534 and want to dual boot with Ubuntu. I am worried about UEFI and am not confident that the system will boot after installation.

If I resize my win partition /sda5 and install Ubuntu in the free space, will I be able to boot? I am not sure how GRUB will work nicely with win 8.1/UEFI.

NOTE: When I changed bios setting to Legacy from UEFI it could not find Windows. Will this change if GRUB is installed when installing Ubuntu?

[IMG]http://i.imgur.com/7ETzqSV.png[/IMG]

---

### Post by squakie on 2014-03-31
There are MANY, MANY, MANY threads on Windows 8, UEFI and Ubuntu on the forum.  I mean a LOT.  You would be best off taking some time searching for those.  Also search for threads with replies from user oldfred.  They have been giving fantastic advice on this for months.

Personally, I wouldn't resize a Windows 8 partition in the installation - do it before hand using the Windows tools to do so.

---

### Post by oldfred on 2014-03-31
You must turn off fast boot or the always on hibernation. 
Best to also turn off secure boot.
Your Windows will only boot in UEFI mode not legacy/CSM/BIOS mode. 
Best to install Ubuntu in UEFI mode if at all possible. But a few systems will only let you install in BIOS mode and you have to use Boot-Repair to uninstall grub-pc(BIOS) and install grub-efi(UEFI) to convert to UEFI boot.
Some Sony's seem to have the vendor modified UEFI to only boot Windows. That is against UEFI standard and if your system is that way complain to Sony. Boot-Repair has a fix to rename the Windows efi file to really be shim/grub. Then System thinks it boots Windows but actually boots grub. But with rename/fix you can only boot Windows from grub meu.

Other Sony's, not sure if they are similar to your model or not:
 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)
Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

Lots of links to the importantant info you need in the link in my signature. Particularly the first three.

@squakie
Thanks. Just trying to help

---

### Post by squakie on 2014-03-31
Thanks oldfred!!! ;)

---

