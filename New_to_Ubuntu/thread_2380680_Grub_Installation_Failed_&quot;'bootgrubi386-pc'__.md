---
title: "Grub Installation Failed: &quot;'/boot/grub/i386-pc' : No such file or directory&quot; Error"
date: 2017-12-20
forum: New to Ubuntu
---

### Post by burzumstride on 2017-12-20
Hello, I have recently completed a Lubuntu 17.10 install, alongside Windows 10 on my Acer Aspire Switch 10E.

In order to get anything Linux-related to boot past the initial bootloader off of a LiveUSB, I have to add the "nomodeset" command every time.
The Lubuntu installation itself was successfull, with the exception of an error stating that Grub could not be installed.  Re-installing yielded the same results.

The automated BootRepair function in the "BootRepair live USB" did not sort the problem, as I do not have wireless drivers or an ethernet port.
The proprietary linux drivers I do have access to need to be compiled before being used.  (unless tar.gz can be magically "double-clicked" by the virtue of some amazing, live-USB-compatible software?)

I have attempted to do a manual grub installation according to these sets of instructions:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)
[https://askubuntu.com/questions/126541/how-to-manually-install-boot-loader](https://askubuntu.com/questions/126541/how-to-manually-install-boot-loader)
These attempts always resulted in:
"cannot open directory '/boot/grub/i386-pc' : No such file or directory" error.  
(I did remember to use /dev/mmcblk0 or /dev/mmcblk0p5 instead of /dev/sda or /dev/sdaX)
Could this be related to the "nomodeset" command, and the fact my CPU is actually a x64 Atom Z8300?

Finally, there was one instance where I managed to connect to WiFi upon being informed that connections were available - this was after issuing 10 different variations of the grub-install /directory command, and forgetting to unmount the previously mounted directories (this also resulted in a permanently-blank terminal window and caused me to re-install the whole BootRepair... and subsequently lose internet access, either to re-booting or reinstalling haha).


Any help would be greatly appreciated.  Windows 10 is ridiculously slow, and I am not settling for sub-par slaveware.

---

### Post by oldfred on 2017-12-20
Do not use any tar.gz unless nothing in repository works.

Is this one the those that uses 32 bit UEFI, but is a 64 bit chip?
Did you install in UEFI boot mode? But you have to add grubia32.efi which is not part of standard Ubuntu.

[https://gist.github.com/franga2000/2154d09f864894b8fe84](https://gist.github.com/franga2000/2154d09f864894b8fe84)
[https://ubuntuforums.org/showthread.php?t=2234219](https://ubuntuforums.org/showthread.php?t=2234219)

---

### Post by burzumstride on 2017-12-21
Thanks for the quick reply!

Not sure whether the UEFI itself is 32 or 64 bit.
I am using a newer SW3-016 (2016) model, and I'm pretty sure it's incompatible with Legacy boot.  The installations of both x64Win10Home and Lubuntu were completed with Secure Boot "ON" and a whitelisted boot64.efi (can't remember if the Windows file had the same name, but was definitely x64).

I will try the solutions in the threads you have linked (ommitting the repeated Ubuntu installation - unless you think that's a bad idea) and see if that works!

---

### Post by oldfred on 2017-12-21
Do not know then if you have 32 bit or 64 bit UEFI. 

Re-install is a last resort. But can be done, just only use Something Else and choose same / (root) and /home if you created that also.

UEFI only boots from external drives from an ESP or FAT32 partition with boot flag and /EFI/Boot/bootx64.efi, if 64 bit or bootia32.efi, if 32 bit     UEFI (even if system is 64 bit). With Window that would have been a copy or version of Windows .efi boot file.
With Ubuntu it is a copy of grub, but not the full install configuration of grub. It just has parts needed to boot live installer in UEFI mode with either Secure boot on or off. Ubuntu live installer also has BIOS boot but uses syslinux for that to avoid issues.

---

### Post by Rex Bouwense on 2017-12-21
Not sure if this would apply.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)  It apparently is affecting some Acer products.

---

### Post by burzumstride on 2017-12-22
Thanks again, I will update on how I get on with the 32bit Grub installation.

Fortunately I don't think this is the "Corrupting BIOS" bug.  My UEFI Firmware seems as functional and poorly though-out as ever :)

---

### Post by burzumstride on 2018-01-02
Thank you all for your help, it was a rather silly mistake on my part.

The root of the issue was most likely me attempting to boot from the wrong file.  After trying multiple linux distros and looking closer at a few tutorials, I tried the boot-repair again with a wireless USB dongle.  The final message after a successful grub repair  mentioned that I should select the "shimx64.efi" file.  Previously I was attempting to boot from  "grubx64.efi" and "bootx64.efi" (once grub was correctly installed with lubuntu 16.04).

My Acer Aspire Switch 10 E (2016) SW3-016 did not appear to suffer from the 17.10 Ubuntu BIOS corruption error.

//For now I switched to Xubuntu due to Lubuntu's networking issues with the USB dongle

---

