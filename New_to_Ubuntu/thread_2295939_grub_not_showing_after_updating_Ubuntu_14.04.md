---
title: "grub not showing after updating Ubuntu 14.04"
date: 2015-09-22
forum: New to Ubuntu
---

### Post by James_Bellarby on 2015-09-22
Hello, 
Im relatively inexperienced with Ubuntu but have it dual booting on my laptop.
Everything worked fine until i updated Ubuntu recently.
Now it doesnt show grub on startup and goes straight to windows.
Ive tried boot-repair but no success and cant see where to go next.
boot repair file is [http://paste.ubuntu.com/12519923/](http://paste.ubuntu.com/12519923/)

Is says [COLOR=#000000] [/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]> No boot loader is installed in the MBR of /dev/sda.
is this the problem? how do i correct it?

thanks

James[/COLOR]

---

### Post by oldfred on 2015-09-22
With UEFI, you do not use MBR, only ESP - efi system partition. And you have ubuntu/grub boot files in the ESP.

What brand/model system?
Did you run Boot-Repair before to get system to boot? It used to rename grub's efi file to the Windows efi boot file, but any update in Windows overwrote grub and then only Windows would boot. This was required for some brands that modify UEFI to use description in UEFI boot and only valid description was "Windows". That is not per UEFI standards.

We now have other work arounds. Most rename bootx64.efi and boot a hard drive entry in UEFI or use rEFInd for a gui boot loader that also works.
Boot-Repair suggests the adding of a entry to Windows's BCD and that usually works, but you boot into Windows & reboot into grub using UEFI one time boot option.

Can you boot from one time boot key, often f10 or f12, check your system's manual. Or directly from UEFI boot menu one of the ubuntu entries? One is for secure boot and will work with secure boot on or off (shim) and other is grub for standard (secure boot off) UEFI boot. It says you have secure boot off so either ubuntu entry should work.

       Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)

---

### Post by James_Bellarby on 2015-09-23
thanks, sorry should of given more information.
Its an Dell Inspiron 7520. Yes I can still boot to Ubuntu by hitting F12 and selecting Ubuntu and it then loads Grub ok and I can get into Ubuntu.
Ive run boot-repair but made no difference, still had to use F12. I tried turning off secure boot in advanced options in boot-repair but that made it not boot at all and I had to run ubuntu live and run boot-repair again.

Can i use boot-repair to try these other options you suggest or do I try something else?

thanks for your help and time

James

---

### Post by James_Bellarby on 2015-09-23
thanks for the links, I was able to get it working using info in one for them. eg

[LIST]
[*]I made a backup of that file by moving it one level down:
$ sudo cp /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi /boot/efi/EFI/Microsoft/bootmgfw.efi

[*]Finally, I copied GRUB2's boot loader in that place, "tricking" the system into loading the boot loader I wanted instead of Windows' original boot loader.
$ sudo cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
[/LIST]

---

### Post by oldfred on 2015-09-23
We used to suggest that "fix", but an Windows update will overwrite it and you have to do it again.

There now are the multiple ways to work around the issue. I did not think Dell was one that used UEFI description to boot and only valid description was "Windows". That is not supposed to be done per UEFI standard. I have a new Dell SFF system and it just worked.

Link in my signature and these show the other work arounds. The ones used the most are renaming bootx64.efi to be really grub and boot hard drive/fallback UEFI boot entry. Or use rEFInd.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

---

