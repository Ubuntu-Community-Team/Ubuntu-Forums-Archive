---
title: "Windows loads automatically, no Ubuntu option"
date: 2018-03-03
forum: New to Ubuntu
---

### Post by astrokidd on 2018-03-03
Hello,

I just installed Ubuntu and when I restarted the computer, it automatically loads into Windows 10 and I don't see any option to select Ubuntu at all. I then installed boot-repair after googling a bit, and it said that boot-repair recovered grub successfully. It however didn't make any difference and I can't see an option to select Ubuntu when computer starts. I am ofcourse newbie to Ubuntu.

This was the link they provided when I installed boot-repair.

[http://paste.ubuntu.com/p/BWKcRcfbcM/](http://paste.ubuntu.com/p/BWKcRcfbcM/)

Any help?

Thanks.

---

### Post by oldfred on 2018-03-03
You have an HP. 

HP violates UEFI spec that says NOT to use description as part of boot.
And only valid description is "Windows Boot Manager".
But various work arounds.

Some only occasionally reboot and just manually select each time. The one time boot selection should work. escape & f8 or f9?
Many copy shimx64.efi to bootx64.efi which Boot-Repair has already now done for you. Can you boot hard drive or fallback entry?
The /EFI/Boot/bootx64.efi is the path & file for all external devices and can be used as a fallback for internal drives.

       Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)
HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[https://ubuntuforums.org/showthread.php?t=2376227](https://ubuntuforums.org/showthread.php?t=2376227)
HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[URL="http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook"]http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook

[/URL]
 Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114) 

Also Boot-Repair saw all the HP .efi files in the ESP - efi system partition. Those generally do not need to be in grub and are for whatever HP system maintenance you have.
 You can edit those you do not want or turn off execute to remove all of them.

 bootx64.efi Also edit of 25_custom
[http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)
# Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 

[URL="http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook"]
[/URL]

---

