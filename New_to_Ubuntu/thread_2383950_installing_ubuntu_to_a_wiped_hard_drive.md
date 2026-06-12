---
title: "installing ubuntu to a wiped hard drive"
date: 2018-01-31
forum: New to Ubuntu
---

### Post by dharris1234 on 2018-01-31
I have a Dell Latitude E5530 with a wiped HHD. I bought the Ubuntu 17.10.1 32GB flash drive but I can not get it to load. it ask if I want to install I hit enter an it goes to a purple screen with the Ubuntu logo and 5 dots but nothing after that for hours.
any help would be great.
Thanks

---

### Post by deadflowr on 2018-01-31
Sounds like you might need to set nomodeset in at the menu screen 
(where it lists the option to install or try or check disk for defects or memory test, et al)

In this screen press the F6 key and select nomodeset, then press Esc to return the screen to normal.
Then try running the installer.

It could also be another option, so if that doesn't work, come back and maybe someone knows which option might work.

---

### Post by dharris1234 on 2018-01-31
I go into help and hit F6? if so I did that but don't see where to change to nomodeset.

---

### Post by deadflowr on 2018-01-31
> **dharris1234 said:**
> I go into help and hit F6? if so I did that but don't see where to change to nomodeset.

No, on this page at the start:

Just hit F6 and then go down the list in the popup field that appears and hit enter or space, then hit Esc to close the popup field.

---

### Post by dharris1234 on 2018-01-31
I do not have that on my screen.[ATTACH=CONFIG]278406[/ATTACH] sorry couldn't get it to rotate.

---

### Post by haplorrhine on 2018-01-31
> **dharris1234 said:**
> I have a Dell Latitude E5530 with a wiped HHD. I bought the Ubuntu 17.10.1 32GB flash drive but I can not get it to load. it ask if I want to install I hit enter an it goes to a purple screen with the Ubuntu logo and 5 dots but nothing after that for hours.
any help would be great.
Thanks

It might be corrupted. Unfortunately, in flash memory blocks die, and that can affect a checksum of a bootable Ubuntu flashdrive.

---

### Post by oldfred on 2018-02-01
Is this an UEFI system?
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And if UEFI, you have to manually edit grub menu when booting.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by dharris1234 on 2018-02-01
Thanks I contacted OSDisc where I purchased it, waiting on a response.

---

