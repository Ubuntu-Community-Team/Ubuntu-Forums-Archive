---
title: "Minimal BASH ERROR - Can't boot Ubuntu on my HP ENVY 13 Laptop"
date: 2019-02-27
forum: New to Ubuntu
---

### Post by bkalem4 on 2019-02-27
Hey everyone!

For the past 4 days, I'm struggling to install Ubuntu on my brand new external HDD for a dual-boot. (Seagate Expansion 1TB)

I've followed the instructions on this youtube tutorial: [https://www.youtube.com/watch?v=glFCEauwGgw](https://www.youtube.com/watch?v=glFCEauwGgw) 

I created a partition on my external HDD for the install of the OS. I used live USB for installation. Everything seemed normal after installation after I clicked "Restart now.". The system froze I had to hard reset my PC. When I clicked ubuntu on BIOS boot selector, it gave me the notorious "minimal BASH ERROR":

```
[COLOR=#000000][FONT=&amp]Minimal BASH like line editing is supported. For the first word, TAB lists possible command completions. anywhere else TAB lists possible device or file completions.[/FONT][/COLOR]
```

After I searched the web for some solutions, and I figured turning off SecureBoot could be a solution. But no, I formatted the HDD number of times and installed the OS. But it's the same.

One of the error when I tried to boot Ubuntu read like this:

```
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi : Not Found
Failed to start MokManager : Not Found
Something has gone seriously wrong: import_mok_state() failed : Not Found
```


I tried Boot-Repair as well - on recommended settings - , but it did not work. I feel like I have ran out of options. Please help!

Thank you :)
---


ps: the system uses UEFI boot

---

### Post by oldfred on 2019-02-27
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some have just copied mmx64.efi to /EFI/Boot.
It should be there anyway, but some do not seem to get it. It also should be in /EFI/ubuntu.
And if not available some have just copied grubx64.efi and renamed it ot mmx64.efi. Just to not try to change Secure boot settings as that is what mmx64.efi is for. May be required to turn off Secure boot for video or Wi Fi driver or if Secure boot on to create your own signing key to install those drivers. Most do not need it.

       
 Ubuntu recently renamed MokManager.efi to mmx64.efi, and added fbx64.efi (which just launches GRUB through a new path). 
            System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

---

### Post by bkalem4 on 2019-02-27
Hey thanks for the reply, I got boot-repair from the terminal using the "add-apt-depository..." command. I tried running it multiple times it takes really long, can you give me an estimated time of the scan? It feels like it will never finish the scanning.

btw: the program says to turn off SecureBoot before scanning.

---

### Post by oldfred on 2019-02-27
I have many installs and it does take a couple of minutes.

But it longer then you may have a partition issue or Windows fast start up on?

Have you updated UEFI from HP? Important even if not dual booting.
And if SSD updated firmware. 
Are drives in AHCI mode, not RAID nor IDE nor Intel SRT. If dual booting install AHCI drivers first into Windows.

Make sure Windows fast start up is off, and in UEFI fast boot is off.
Often better to have UEFI Secure Boot off.

---

### Post by sanctimonious on 2019-03-12
I was able to make it work on an Envy 13 using a version of the instructions below:

[https://www.dionysopoulos.me/portable-ubuntu-on-usb-hdd/](https://www.dionysopoulos.me/portable-ubuntu-on-usb-hdd/)

Instead of putting the EFI partition on the native HD, I simply created it on the external HDD and then booted up from the live USB, reformatted the EFI partition and installed a secure-boot EFI grub with the --removeable parameter. 

Your laptop is most probably not starting because the Ubuntu installation messed a bit with your Windows EFI partition. You will need to fix that - instructions are provided within the article quoted above.

---

### Post by oldfred on 2019-03-12
@sanctimonious     

A few comments on your link's instructions, which do seem like they work but some understanding and simplification is possible.

Best to  only use Ubuntu's default of ext4 as he suggests, not any other format.
Just partition in advance or during install with Something Else and include the ESP - efi system partition (FAT32) as first partition. Installer will not use it, no matter what you do (so far), but then you have it. Then no need to go back and redo partitioning to add ESP.
You then can copy all of /EFI/ubuntu from internal drive to /EFI/ubuntu to ESP on external drive. And then copy /EFI/Boot to ESP on external. As in instructions, you need to update /etc/fstab with external drive's UUID for ESP.
External drives only boot from /EFI/boot, but full install version of grub is hard coded to use /EFI/ubuntu for some of the files.  The grub install command used in link also works as the --removable knows to create /EFI/Boot/bootx64.efi.

The /EFI/Boot/bootx64.efi in the internal drive is normally a copy of /EFI/Microsoft boot file. Also known as fallback or hard drive boot entry as similar to external drive UEFI boot entry. Best to reset to Windows file if not installing Ubuntu on internal drive. 

From Ubuntu you can reset boot order in UEFI for most systems with efibootmgr, a few only work from within UEFI to change boot order. Ubuntu full install will normally make Ubuntu first in boot order. You can change back to Windows if Windows drive not disconnected.
Removing a drive, or using settings in UEFI to hide/turn off drive often reset UEFI boot entries as then drive is not there. Some auto find Windows when drive turned on, others require either Windows repairs or use of efibootmgr to add a new Windows boot entry.

---

