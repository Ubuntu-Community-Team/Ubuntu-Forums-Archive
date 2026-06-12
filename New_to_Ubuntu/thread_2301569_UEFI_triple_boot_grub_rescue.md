---
title: "UEFI: triple boot grub rescue"
date: 2015-11-03
forum: New to Ubuntu
---

### Post by tlau2 on 2015-11-03
Hi guys, 
I have a similar problem with my laptop. I have a toshiba L45b with triple boot system (w10, ubuntu & debian8). It have been functional, both linux distros were installed  in uefi with secureboot disabled. After I reinstalled debian8  to solve a login issue, i just switched to grub rescue prompt.  
Then, I tried to restore grub2 menu with my ubuntu LiveCd, i installed & ran boot repair and it worked without errors. I clicked  on recommended option, after reboot I was able to see the grub menu ( the windows bootloader on sda2 option was not functional anymore btw, i choosed that one and following i just switched to grub, again. But i was able to boot in w10 from other grub option on the list, i dont know why). At that point i was able to boot ubuntu, debian and windows. Then I rebooted again and the grub rescue prompt appeared again.
This is my last paste link from boot repair..
[http://paste.ubuntu.com/12960083/](http://paste.ubuntu.com/12960083/)
i repeated the described steps three times, in every attempt i obtain same result.
Sorry for my english.

---

### Post by oldfred on 2015-11-03
Moved to your own thread since while a boot issue, yours is different than orginal threads's issue.

You have two grub installs one is Ubuntu & the other is Debian's.
In UEFI you show Windows as default.
From UEFI boot menu or one time boot key like f10 or f12, check manual, can you boot all three installs, Windows, Ubuntu or Debian. Or which do not work.

After Windows updates make sure you reset its defaults back to no secure boot, fast startup off, and it probably resets itself to first in boot menu.

You may want to house clean older kernels and some of the Boot-Repair logs in the ESP.

I see Debian has the 0077 setting in its fstab for the ESP - efi system partition. Ubuntu has used defaults, but recent versions now use the 0077, With the 0077, you cannot edit or change any files in the ESP. I changed mine back to defaults but had to reboot for it to take effect.

---

### Post by tlau2 on 2015-11-03
Hi Oldfred, thanks for you response, i really apreciate that.
Well, when i reinstalled debian, the netinstall cd don't offered me the option "continue without grub install". Maybe that is the reason of  my two grub installs.
I can boot ubuntu from the grub rescue prompt manually, but if i press f12 when toshiba logo are appearing, it shows me the boot order menu, not the Os in my hard drive. F10 don't works.
Its weird that boot repair can reinstall ubuntu grub and make it functional, and next to reboot the problem persist. I dont understand how it is working.
If i  quit or erase the grub install for debian, can i see the old ubuntu grub ?  
You mentioned that i may want to clean house of older kernels and logs, how can i do that from ubuntu ? Or i've to do from windows ?

And , how can i change the 0077 setting of debian to defaults ? 
I dont have idea of what to do right now.

---

### Post by oldfred on 2015-11-03
Since UEFI, you should be able to boot any install directly from UEFI or from f12 (f10 is perhaps other brands).
But in UEFI you set default boot order. And only one can be first. You should be able to set in UEFI or you can with efibootmgr.

You may be fixing one grub with Boot-Repair and the other is the issue & also is default. UEFI has a one time boot setting, so that may be why it works once.

Boot-Repair shows Windows as default - 0000

```
BootOrder: 0000,0006,0001,0002,0005,0003
Boot0000* Windows Boot Manager	HD(2,200800,32000,d6b1ebe7-cf07-11e3-930a-0c54a5f57a0b)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller	ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(60029210defa,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller	ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(60029210defa,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* ubuntu	HD(2,200800,32000,d6b1ebe7-cf07-11e3-930a-0c54a5f57a0b)File(EFIubuntushimx64.efi)
Boot0005* debian	HD(2,200800,32000,d6b1ebe7-cf07-11e3-930a-0c54a5f57a0b)File(EFIdebiangrubx64.efi)
Boot0006* UEFI: TSSTcorp CDDVDW SU-208FB	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000CD-ROM(1,76991,1240)..BO

```

       You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu or Debian entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.) Some require all 4 numbers and some only require the first or most significant. 

      
 Change the parameter to from umask=0077 to defaults.

   sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
or
sudo nano /etc/fstab

---

### Post by tlau2 on 2015-11-03
Thanks for your help Oldfred. Its really usefull at moments like this.
Since UEFI i can't find the Os boot order menu or something similar, only shows the Device boot order (sorry, i was not specified before). The same when i press f12 or f2 at booting.
I'm gonna try with efibootmgr as you recommend. But I have another cuestion: at the first days after i installed ubuntu, i had a problem with boot in wich only boots windows, i solved this changing the bcd path to "grub_x64.efi", instead the original windows efi file path. After w10 upgrade, im not sure if this change was disabled or rewrited (i had to use boot-repair after). 
my question is if this may complicate the actual issue, or simply i dont have to worry about lose a valid efi path to boot in windows ?
Do you recommend to make a back up windows efi partition before i try with efibootmgr?

---

### Post by oldfred on 2015-11-03
Backup always a good idea before any changes.
So backup ESP - efi system partition.

If you renamed the Windows efi boot file to really be grub or shim that usually only temporarily works. Windows will overwrite it and grub updates may eventually make the copy not valid, or you need to recopy. Boot-Repair used to make that change but now recommends an entry in BCD.

Many others copy shim into /EFI/Boot and rename to bootx64.efi. And then boot the hard drive entry. Some have to create an UEFI entry for the hard drive. Needing to recopy may still be an issue, but often a good backup way to boot even if not your primary way to boot.

Details of copying files are in link in my signature.

Some other Toshiba systems that did work arounds to boot.
 Toshiba L50-A-1EH laptop - used bcd edit
[http://ubuntuforums.org/showthread.php?t=2295628](http://ubuntuforums.org/showthread.php?t=2295628)
Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)

---

### Post by tlau2 on 2015-11-03
Hi again, 

In grub rescue promt, i typed 'set' and shows me this result:

error: file '/boot/grub/x86_64-efi/normal.mod' not found

grub rescue> set
cmdpath=(hd0,gpt2)/EFI/Debian
prefix=(hd0,gpt11)/boot/grub
root=hd0,gpt11

Then, i was manually boot ubuntu kernel and typed sudo efiboootmgr -v and the result is following:

BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0000,0001,0002,0005,0003
Boot0000* Windows Boot Manager    HD(2,200800,32000,d6b1ebe7-cf07-11e3-930a-0c54a5f57a0b)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* UEFI: IP4 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(60029210defa,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: IP6 Realtek PCIe FE Family Controller    ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(60029210defa,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* ubuntu    HD(2,200800,32000,d6b1ebe7-cf07-11e3-930a-0c54a5f57a0b)File(\EFI\ubuntu\shimx64.efi)
Boot0005* debian    HD(2,200800,32000,d6b1ebe7-cf07-11e3-930a-0c54a5f57a0b)File(\EFI\debian\grubx64.efi)

As you said before, that indicates the problem is  debian's grub, wich is actually the current boot, right?

Now i will install & run boot-repair to have a chance to boot windows and make the back up of efi partition in a dvd, and a usb recovery image, assuming that i can mess it up if i set the #3 (ubuntu) as default boot loader.

---

### Post by oldfred on 2015-11-03
Grub uses a tiny grub.cfg in the ESP that is just a configfile.It sets the partition and finds the full grub.cfg in your install.

Boot-Repairs script does not show the grub.cfg in /EFI/Ubuntu or /EFI/Debian. But that may be part of the issue. You can review them to see if UUIDs are correct. And/or in Boot-Repair run the advanced mode and full uninstall/reinstall of grub. Perhap from both Ubuntu & Debian?

---

### Post by tlau2 on 2015-11-06
Hi oldfred, thanks for reply.
After my last messege, i used efibootmgr to set the boot loader (#0003) of ubuntu (in sda6) as default, instead of the debian's. After reboots, ubuntu grub2 showed me some entries like 'mok manager.efi', 'bkpbootmgfw.efi' and 'windows UEFI boot loader', wich were not displayed before. I have a little suspicion: that it's caused by boot-repair, just like the issue that ubuntu showed after login 'efi partitiion is full; erase or move programs or files to other partition'. To that point i was able to boot in ubuntu, windows and debian. Then, moved by curiosity, i choosed the last entry 'System Setup', and i just switched to UEFI menu. When done reboot, my last configuration was missed or something, because the grub rescue prompt appeared again.
I repeated the process with efibootmgr and it worked, but unstable. 
I ran again boot-repair and disabled the 'backup and rename' option, and set 'purge&reinstall grub', and 'purge kernels & reinstall latest' (to clean up), but i had a problem: boot-repair got stacked some hours in 'purging and reinstalling latest kernel (ins)', so i closed the window and went to check the list of kernels with 
dpkg -l | grep linux-image-.*-generic

and nothing happened, no lists anything. Scared, i reinstalled the current kernel and ran 'sudo dpkg...' again. This time it showed me the installed kernel.
After that, i typed sudo grub-update, wich apparently ran without errors. 
Now, I just clicked on info log option in boot-repair and there is
[http://paste.ubuntu.com/13129749/](http://paste.ubuntu.com/13129749/)

Also, since the wrong installed debian can't connect to network nor anything (no graphic environment, just the base system), 
i just thinking if a full reinstall (not net-install) can solve part of the problem, but i don't sure if this is secure right now.

---

### Post by oldfred on 2015-11-06
Some early Toshiba's with UEFI would just boot Ubuntu.
But then they must have gotten the discount from Microsoft to make it difficult for Linux and now most Toshibas need the work around of copying /EFI/ubuntu into /EFI/Boot and rename shimx64.efi to bootx64.efi. That is the UEFI fallback or default hard drive boot entry which is the standard for external devices. Details in link in my signature.

Boot-Repair does add entries to grub menu so you can boot anything in the ESP - efi system partition. You can edit those out if desired. Or manually create entires & turn off os-prober so it does not search for entries.  But some systems with UEFI's fast boot (not Windows fast start up) had issues getting into UEFI, so that is why you have

---

