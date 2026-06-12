---
title: "Problem with boot menu finding windows 7"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Subcomfreak on 2014-05-08
Hi all again.

I have a problem when I tried to upgrade my system from win7/xubuntu 12.04 to Windows7/Ubuntu 14.04 (note, not X). The process I used is as follows:

Downloaded and made live usb drive
Installed ubuntu by something else option. I reformatted my /etc and /home partitions, nothing else.

When I finished the install it would not boot so I went back to the life USB and ran boot repair (like I had to do last time). Now whenever I boot the computer there are only three options Ubuntu, advanced options for Ubuntu, and windows boot manager. When I select windows boot manager it says "could not find file" and then crashes to the grub rescue console. 

In my old, working, setup it had many different options, and I would boot to windows with a .efi file with a funny name. That option does not seem to appear on grub's menu any more. Every thing in Ubuntu is working better than expect, but I really need to boot to windows.

I wouldn't mind to add an entry into grub, but I need instructions on how to do that...

here is an image of my partition configuration:
[IMG]http://i.imgur.com/OgQEzZt.png[/IMG]

---

### Post by Subcomfreak on 2014-05-08
I tired boot repair again and it said:

> An error occurred during the repair.

Please write on a paper the following URL:
_[http://paste2.org/LcKDYnvE](http://paste2.org/LcKDYnvE)_

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.


The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

My windows OS is installed on sda3, and obviously I want to somehow but to it from grub.

---

### Post by Subcomfreak on 2014-05-09
I really need help finding a solution to this problem.

---

### Post by newbie2244 on 2014-05-09
Check out [COLOR="#B22222"]**oldfred's **[/COLOR] posts on this forum. Usually its an uefi problem. Go into BIOS and turn of secure boot and turn on legacy mode. You may also have to change boot order
during the install process. But when you are finished with the install reset the boot order to the original sequence.

---

### Post by oldfred on 2014-05-09
Who? :)
some others have actually installed with UEFI and also are helping with UEFI issues.

It looks like Ubuntu was in BIOS mode, Boot-Repair may have converted it to UEFI mode. You now have entry for efi partition in fstab and signed kernels.

Not sure about burg. I did not think it worked with UEFI.

There are some issues booting Windows from grub menu when secure boot is on. Best to have it off for now.

Do both Windows & Ubuntu boot from UEFI menu? With secure boot on or off?

If you want graphical boot menu you can install rEFInd. 
 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
More info on secure boot - Ubuntu's shim may need changing to work with Refind
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by Subcomfreak on 2014-05-10
I was able to fi this by running a program that restored some of the windows files and now the windows boot menu entry works fine.

---

