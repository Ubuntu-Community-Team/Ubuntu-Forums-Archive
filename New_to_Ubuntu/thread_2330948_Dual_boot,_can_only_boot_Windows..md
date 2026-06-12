---
title: "Dual boot, can only boot Windows."
date: 2016-07-16
forum: New to Ubuntu
---

### Post by jain6971 on 2016-07-16
Hello
I installed Ubuntu 16.04 LTS via bootable USB key using "install alongside windows option". I already have Windows 10. however it just directly boots to Windows. No dual boot option to choose an OS appears. I am running Ubuntu via "try ubuntu without installing".
Here is the info about boot that I got via the command in your post. Could someone please help me out. 

[http://paste2.org/J5kE624w](http://paste2.org/J5kE624w)

However I am confused. It shows Windows 8 sectors however I bought a new HP laptop with Windows 10 pre installed.

---

### Post by gpstrucker on 2016-07-16
What brand computer? With efi the default is set to Windows. During initial startup you need to access the BIOS boot menu to select Ubuntu to boot. On an HP you press the F9 key when the screen first lights up, but it will likely be something different on your machine if not an HP. Google linux efi boot your machine.

---

### Post by oldfred on 2016-07-16
HP are not dual boot friendly. And Boot-Repair may see all the HP .efi files for HP maintenance and add to a new 25_custom grub file to add to grub menu. 

I would run Boot-Repair. But you may have to run and then reboot and run again. 
The fstab has a setting on the efi partition umask=0077 that prevents editing/updating. When I manually edited mine I had to reboot for new settings to work.
And Boot-Repair wants to run the use-standard-efi-file option which rename's /efi/boot/bootx64.efi. Then you may be able to boot an internal hard disk UEFI entry or we can add one.
HP violated UEFI spec and uses description as part of boot. And only valid description is "Windows Boot Manager". But UEFI has a fallback or hard drive entry and that does work.

[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file) 

But most manually copy files, that Boot-Repair will now auto copy.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

