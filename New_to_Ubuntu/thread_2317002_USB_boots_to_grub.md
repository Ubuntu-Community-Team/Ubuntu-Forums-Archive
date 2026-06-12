---
title: "USB boots to grub"
date: 2016-03-12
forum: New to Ubuntu
---

### Post by Dazappa on 2016-03-12
I am trying to make a live usb of Ubuntu 15.10 (to verify it works with my laptop features, and then to install if all goes well as a dual boot with Windows 10). The usb is 128gb formatted as ntfs. I've used both pen drive linux's image writer as well as unetbootin. Both successfully write an image and allow the laptop (Asus F555LA-AB31) to boot, however it just boots into a grub command prompt. I have tried disabling in the bios secure boot and fast boot, and fast boot from within Windows 10. I tried formatting the usb as exfat, but the bios no longer detected it as a bootable drive. I have tried putting the usb drive in both usb 3.0 and 2.0 ports (same results).

I don't have another computer to test on. My only other option would be a dvd install... which is annoying to go to an electronic store to buy some blank dvds.

---

### Post by oldfred on 2016-03-12
If new Asus, then it is UEFI.
And you will want to install Ubuntu in UEFI boot mode also.
And how you boot installer is how it installs, so boot installer in UEFI mode, which does use grub menu.
UEFI boot partition always must be FAT32, not NTFS nor exFAT. And have boot flag for UEFI to know it has boot files.
Both for installer and after install, UEFI uses FAT32 for all boot files.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by Dazappa on 2016-03-12
Hello, yes it is UEFI (a laptop about a year old). The BIOS recognizes the USB as uefi (it is listed as UEFI: SanDisk). The USB boots to grub as a black screen not purple. The problem, is the screen with grub is a blank command prompt. It does not have a list of options like "Try Ubuntu without installing".

It has 

GNU GRUB version 2.02~beta2-29
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
grub> _

From here I can type in commands like "help"

I can boot Windows successfully with the following commands
set root=(hd0,msdos1)
search --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
boot

Possible devices are memdisk hd0 hd1 hd2.

There is also
set root=(hd1,gpt1)

It lists (by hitting tab at the second parameter) gpt2, gpt3, gpt4 but they all say "No known filesystem detected". gpt1 is "Filesystem type fat - label 'SYSTEM', UUID OAEO-EC9E partition start 1024 kib - Total size 266240 kib"

There is also an hd2 which apparently has no partitions.

What is extremely odd... is with hd1,gpt1 is where /efi/Microsoft/Boot/bootmgfw.efi is... (I hit chainloader /[TAB] and it lists efi/Microsoft...) so I think the hd0,msdos1 is something else entirely, and the second "search" command overwrites whatever root I just specified, I think.

Doing chainloader /[TAB] with hd0,msdos1 and hd2 are blank.
Chainloader with memdisk provides "error: not a valid root device."

So now I am confused. Because it is very obviously booting off of the USB to get to grub, yet grub seems unable to find the USB drive it just booted off of?

---

### Post by fantab on 2016-03-12
If the USB 'boots to grub as a black screen' with grub menu then it is booting in UEFI mode. Legacy boots with purple screen. In your case, you are greeted to the console... and this is probably because the ubuntu.iso did not write propery to USB.

Rewrite the .iso file to USB: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
Also format USB as FAT32, not NTFS.

---

### Post by Dazappa on 2016-03-12
Thank you very much fantab. Windows 10 did not want to let me format the drive as fat32 because it was large (128gb). I was able to get a third party tool to do so. Then I copied using win32diskimager. The usb drive was now able to boot successfully into Ubuntu! Many thanks again.

---

