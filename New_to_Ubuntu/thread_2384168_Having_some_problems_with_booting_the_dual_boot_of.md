---
title: "Having some problems with booting the dual boot of Windows 10/Ubuntu 17.10"
date: 2018-02-03
forum: New to Ubuntu
---

### Post by tratten on 2018-02-03
Hello!

I recently got my new Dell XPS 9370 with Windows 10 preinstalled on it. Now I wanted the ability to dualboot Windows with Ubuntu 17.10.

After shrinking the memory of Windows I booted Ubuntu from a USB flash drive, but during the installation of Ubuntu I ran into the problem that Ubuntu couldnt detect my Harddrive and partitions.

To try and solve this I used this guidance: [COLOR=#444444][FONT=Roboto-Regular]Note:[/FONT][/COLOR][COLOR=#444444][FONT=Roboto-Regular] Users should go to the system BIOS (F2 on boot up) and change the SATA setting to AHCI. [/FONT][/COLOR] (From Dell's own support page: [http://www.dell.com/support/article/se/sv/sedhs1/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](http://www.dell.com/support/article/se/sv/sedhs1/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en))

After switching to AHCI Ubuntu did find the partitions and I was able to install Ubuntu 17.10 without further troubles. Now I wanted to try and boot into Windows to make sure everything was still working, here is where the troubles occured.

When trying to boot Windows with GRUB using SATA operation set to AHCI the boot gets stuck and I receive a BitLocker recovery screen telling me to unlock my drive, even if I unlock this screen I then receive a message saying something went wrong with the boot and is given the option to try and repair or restart. Neither of these options fixes the problem.

The only way I am now able to start Windows 10 is by switching SATA operation in BIOS back to RAID on and then pressing F12 at startup to use the UEFI boot manager and from there boot Windows 10 (does not work with GRUB). But if I now try to boot Ubuntu with these settings, the Ubuntu boot instead gets stuck and wont work.

**To summarize**: [COLOR=#000000][FONT=Consolas]Right now I can start Windows 10 if I use the UEFI boot manager and have SATA operation set to RAID on, but then I can't boot Ubuntu. If I instead use SATA operation set to AHCI I can boot Ubuntu perfectly fine using grub, but can't boot Windows (It gets stuck in bitlocker recovery).

[/FONT][/COLOR]**My question is**: Is there a way for me to get this boot process working without having to use different SATA operation settings and without using different boot managers (UEFI for Windows and GRUB for Ubuntu)?

(I got a tip from the Ubuntu IRC channel that maybe it would work if I were able to change Windows to using AHCI instead of Raid on, but I have no idea of how to do this)

Any help much appreciated!

---

### Post by oldfred on 2018-02-03
I am surprised Dell does not have instructions on adding the AHCI driver to Windows. 

I did find this:
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)

---

### Post by tratten on 2018-02-03
Trying to follow the steps by Sam I got stuck on "Update driver -> Uncheck show compatible hardware" since I do not have such a checkbox. I'm not sure of how to find this driver that he refers to.

Do you have any suggestion on where I might find a suitable driver for my computer which adds the AHCI driver to my Windows?

Should I try and contact Dell support with this?

Thank you for your help!

---

### Post by oldfred on 2018-02-03
Google has many posts with solutions.
I have not had to do it, so do not know what works.
Another link.
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---

### Post by tratten on 2018-02-03
After some unlocking of Bit Locker recovery screens I managed to get it working by the solution provided in your latest link.

Thank you very much!

---

