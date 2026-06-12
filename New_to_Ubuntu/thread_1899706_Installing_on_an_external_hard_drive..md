---
title: "Installing on an external hard drive."
date: 2011-12-24
forum: New to Ubuntu
---

### Post by pinksynth on 2011-12-24
Hi, I'm totally new to Ubuntu and would like to start learning how to use it and all the successive knowledge that entails.  First I have to install it.  I think that I've installed it successfully on an external disk.  I used the CD method and Ubuntu said that it had installed successfully.  I am running Mac OSX 10.7.2 Lion.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209646&stc=1&d=1324723277[/IMG]

What I want to know is how to boot up Ubuntu from this external disk, in layman's terms, if possible.  I've checked a million places online and everything goes right over my head.

Thanks a lot,
Sammy Taylor

---

### Post by shashanksingh on 2011-12-24
Have you tried your BIOS setup?

When the computer boots up, you keep pressing the "delete" key.
What you then get is the BIOS setup.

In the BIOS setup, it asks you which drive to boot from.
(Boot Device priority)
You can put your extenal drive to a higher priority than the first.

Although I havn't tried booting from an external drive, I think this may do it. It should load the grub of the external device.

---

### Post by Mahkoe on 2011-12-24
Also, just making sure, but did you install grub to the MBR (Master Boot Record, essentially what this means is did you select the correct drive for the "bootloader location" option during the installation) of the USB HDD? I've installed Ubuntu to a flash drive before and it took me an hour to realize I had been installing grub on the wrong disk altogether

---

### Post by fantab on 2011-12-24
Dual booting with Mac is not as easy as it is with Windows. Still its simple. You may have to reformat the ExHDD and reinstall Ubuntu. But First:

Is it a Mac book/Desktop or PC Intel?
Does your computer use BIOS or (U)EFI? Can you set your BIOS/UEFI to boot USB Devices First?
Can you post the Screen-Shot of Mac partitions?

Meanwhile be patient and read the following links. The info on these links caters to the laymen like us... its quite easy to understand.

For more info:
[B][https://help.ubuntu.com/community/DualBoot/MacOSX](https://help.ubuntu.com/community/DualBoot/MacOSX)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
[http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu/](http://www.omgubuntu.co.uk/2011/10/dual-boot-os-ubuntu/)


[/B]I don't use mac so I suggest you wait for someone who does to reply.Try installing Grub to the ExHDD and see if you can change the boot order in BIOS or UEFI to boot EXHDD first.It may work since you are not installing it to the Mac HD.I am only guessing the solution here.

---

