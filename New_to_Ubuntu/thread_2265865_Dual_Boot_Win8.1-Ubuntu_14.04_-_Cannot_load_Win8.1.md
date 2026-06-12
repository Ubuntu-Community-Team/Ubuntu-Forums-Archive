---
title: "Dual Boot Win8.1-Ubuntu 14.04 - Cannot load Win8.1 after reinstalling Ubuntu"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by carlo8 on 2015-02-18
Hi everyone, as suggested by the title of the topic I'm having troubles with the dual boot of Win8.1 and Ubuntu 14.04.....forgive me if the post is gonna be a little long, but I guess it should be better to explain how I got into the current situation, please take the trouble to read through the end of it. :P

So, my laptop had Windows 8.1 as the default OS, but I need to use some programs for my Thesis, so I had to install Ubuntu.
It was very easy, I followed some guides on the UEFI installation, making a manual partitioning of the disk, and I ended up with a dual boot working **perfectly fine** (at boot, a GRUB screen would appear asking me which OS I wanted to boot).

Now, I was with a professor who was helping me to compile the programs I need to use (which is a mess, they are old F77 programs and the compiler is no longer suppported)....long story short, she mistakenly
removed a system folder, so that Ubuntu couldn't load anymore. Windows was still working, of course.


No big deal, I got back home and I prepared to install Ubuntu again.
But this time, I made a mistake myself. During the process, the system detected the previous installation of Ubuntu, so this time I didn't use the manual partitioning, but I selected the option to reinstall the OS.
I thought it would only reinstall Ubuntu, leaving the Windows partition alone, but instead it formatted everything and installed Ubuntu as the only OS. ](*,)



After barely restrainin myself from throwing the PC out of the window, I created an empty partition and installed Windows in it.
After this, my disk was partitioned as in this image

[IMG][IMG]http://i.imgur.com/Vyao0z2.png?1[/IMG][/IMG]




After the installation, the system booted Windows by default (no GRUB screen), which I guess is normal.....I loaded Ubuntu from the BIOS, and I used Boot Repair to solve it.
It gave me this error

[IMG][IMG]http://i.imgur.com/TM9Vj6s.png[/IMG][/IMG]



so I selected the Advanced Options, I activated the option "Separate /boot/efi partition" selecting the sda1 partition, and I launched it.


Now, when I turn on the PC the GRUB screen appears, showing the options to load Ubuntu or WIndows.
When I choose Ubuntu it works fine, but if I select Windows an error flashes for an instant, saying

```
[COLOR=#555555][FONT=Monaco]Failed to open \EFI\Microsoft\grubx64.efi - 800000000000000E[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Failed to load image[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Failed to open \EFI\Microsoft\MckManager.efi - 00000000000000000E[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Failed to load image [/FONT][/COLOR]
```

and it goes back to the GRUB screen.


I created a Boot Repair log if it can be of any help: [http://paste.ubuntu.com/10290244](http://paste.ubuntu.com/10290244), 


Any ideas to solve this and load Windows again?

Thank you!


P.S. Sorry for the bad English, if I wasn't clear enough just tell me!

---

### Post by oldfred on 2015-02-18
The installer does have a major bug, and on reinstall only the manual partition choice works.
       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You reinstalled Windows in BIOS boot mode which with Windows has to have MBR partitioning. But it does not correctly convert drive from gpt which is for UEFI boot. It leaves the backup gpt partition table. So then Linux tools see both MBR & gpt and assume you want to erase drive to correct that error.
And if then you reinstalled Ubuntu in UEFI mode, you converted to UEFI mode, but then a BIOS Windows will not work.

You can either reinstall Windows in UEFI mode, or use fixparts to remove backup gpt table so Ubuntu can install in BIOS mode. Depending on where you are at you may have to reinstall Windows.

With both Windows and Ubuntu how you boot installer UEFI or BIOS, is then how it installs. UEFI & BIOS are not compatible. Once you start to boot from UEFI boot menu, you cannot switch modes. Or grub menu only works for systems installed in same boot mode.
If you have Boot-Repair in BIOS mode with a gpt drive, then it also asks for the bios_grub partition to install grub to MBR for BIOS type boot. But if you have UEFI system, you need to also boot Boot-REpair in UEFI mode.
      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by carlo8 on 2015-02-18
First of all, thanks for the answer.


So, if I understood it correctly, the problem is that I installed Ubuntu in UEFI mode (I checked it, and there is [COLOR=#333333][FONT=Ubuntu]an EFI partition (mount point: /boot/efi) in my [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] /etc/fstab file) and Windows in BIOS mode? 
Just to understand, how did you see that Windows is installed in BIOS? I seem to remember that I booted the Windows installation DVD selecting the UEFI option, I must be wrong about it! 


[/FONT][/COLOR]And about the solution, you said

> y[COLOR=#000000]ou can either reinstall Windows in UEFI mode, or use fixparts to remove backup gpt table so Ubuntu can install in BIOS mode.[/COLOR]

but what is the difference between these two solutions?
Reinstalling Windows seems to take longer, but what happens to my Ubuntu installation if I convert Ubuntu in BIOS mode?

My computer boots the HDD in EFI mode (the result of [COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" is [/FONT][/COLOR][COLOR=#333333][FONT=monospace]"EFI boot on HDD"[/FONT][/COLOR]), does it make any difference?

---

### Post by oldfred on 2015-02-18
You may have Windows in UEFI boot mode, I thought the error of gpt was from Windows having converted to BIOS mode. You still have the Windows UEFI boot files in the efi partition.

Can you boot Windows with UEFI on, and/or CSM off, directly from UEFI menu or perhaps one time boot key like f12 (but varied by vendor).

---

### Post by carlo8 on 2015-02-18
I tried entering the Boot menu (F12 at startup)

[IMG][IMG]http://i.imgur.com/PDRZEZdl.jpg[/IMG][/IMG]


but selecting UEFI Options-Windows Boot Manager brings me back to the GRUB screen.
There, as I said, I can load Ubuntu, but if I select Windows it flashes an error

> 
[COLOR=#555555][FONT=Monaco]Failed to open \EFI\Microsoft\grubx64.efi - 800000000000000E
[/FONT][/COLOR][COLOR=#555555][FONT=Monaco]Failed to load image[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Failed to open \EFI\Microsoft\MckManager.efi - 00000000000000000E
[/FONT][/COLOR][COLOR=#555555][FONT=Monaco]Failed to load image [/FONT][/COLOR]

and brings me back to GRUB.


If it can be useful, these are my boot settings

[IMG][IMG]http://i.imgur.com/fvMs2Nml.jpg[/IMG][/IMG]

---

### Post by oldfred on 2015-02-18
Did you run an old version of Boot-Repair that renamed the Windows efi boot file to really be grub?

Post this:
sudo efibootmgr -v

Or did you reinstall Windows and efi files are from previous install and GUID's in efi boot do not match? You then may need to run Windows repairs to update efi boot files.

---

### Post by carlo8 on 2015-02-18
This is the output of the command

> BootCurrent: 000ETimeout: 0 seconds
BootOrder: 0001,0002,0003,000E,0008,0000,000C,000D
Boot0000* ubuntu	HD(1,800,100000,24a9417a-1173-4838-9223-0ed95e7aae44)File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Realtek PXE B07 D00	BIOS(14,0,00)..BO
Boot0002* P0: TOSHIBA MQ01ABD100        	BIOS(10,0,00)..BO
Boot0003* P1: MATSHITA DVD+/-RW UJ8E2   	BIOS(12,0,00)..BO
Boot0008* Windows Boot Manager	HD(1,800,100000,24a9417a-1173-4838-9223-0ed95e7aae44)File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot000C* Onboard NIC(IPV4)	ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(b82a72c12339,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot000D* Onboard NIC(IPV6)	ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(b82a72c12339,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot000E* ubuntu	HD(1,800,100000,24a9417a-1173-4838-9223-0ed95e7aae44)File(\EFI\UBUNTU\GRUBX64.EFI)




---

### Post by oldfred on 2015-02-18
Windows should be booting this:
\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI

Did you run an old copy of Boot-Repair that copied grub into the Microsoft folder and renamed the grub file to be the Windows file name? If so the Windows actual file gets renamed to bkpbootmgfw.efi.

Post the full details of your installs:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by carlo8 on 2015-02-19
The version of BootRepair I'm using is 4ppa33, and this is the summary report: [http://paste.ubuntu.com/10306727/](http://paste.ubuntu.com/10306727/)

As for the details of my installations, I don't understand what you need to know that I didn't mention in my first post, can you be more specific (sorry, as you may have noticed I'm kind of a noob :-| )
Thanks!

---

### Post by oldfred on 2015-02-19
You also need to boot the live installer in UEFI mode. And since all installs are UEFI always boot in UEFI mode.


But I do not see anything specifically wrong. Boot-Repair can only do minor fixes to Windows. You probably need a Windows repair flash drive and run Windows repairs.
Grub really only boots a working Windows.

If you directly boot Windows from UEFI menu or one time boot key does it work? Or can you get into Windows internal repair tools with f8 as soon as you click on the Windows entry?

---

### Post by carlo8 on 2015-02-19
> **oldfred said:**
> 
If you directly boot Windows from UEFI menu or one time boot key does it work? Or can you get into Windows internal repair tools with f8 as soon as you click on the Windows entry?

No, I can't boot Windows from UEFI menu. If I press F12 at startup and go to this menu

[IMG]http://i.imgur.com/PDRZEZdl.jpg[/IMG]



if I select "Windows Boot Manager" it just brings me to the GRUB screen.
There, it shows the options to load Ubuntu (which works) and Windows, but if I select Windows it flashes the errors I showed you and brings me back to GRUB.



I can boot the Windows installation DVD and I tried to run an installation repair, but it did not change anything so far....maybe I'll try it again

---

### Post by oldfred on 2015-02-19
You should not be getting grub if booting Windows directly from UEFI. One of the old fixes to boot grub/Ubuntu was to copy grub to be the Windows file.

Back but entire efi partition if you have not yet. Also good to have backups.

Lets make sure the Windows efi file is a good copy. Copy this file to \EFI\MICROSOFT\BOOT\BOOTMGFW.EFI if booted in Ubuntu it mounts that folder/partition at /boot/efi.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

---

### Post by carlo8 on 2015-02-19
I have the C:\Windows\Boot\EFI\bootmgfw.efi file, even if when I installed Windows I already had Ubuntu installed on my PC, so it was not a "clean" install as the one described in the guide you linked me (it was working, though).

[COLOR=#000000]
[/COLOR]The point is, I have already a bootmgfw.efi file in /boot/efi/EFI/Microsoft/Boot.
I could replace it with a copy of the one in C:\Windows\Boot\EFI .....but, when I select "Windows Boot Manager" in GRUB, it says

```
Failed to open \EFI\Microsoft\grubx64.efi -80000000000000E
```

like it's trying to open a different file (this grubx64.efi, which doesn't even exist).

---

### Post by oldfred on 2015-02-19
That is why I thought you have copied grub and renamed it to the Windows file name. That has been a standard fix, but others now are better.

And I wanted the known good bootmgfw.efi.

One of the other fixes was if only Ubuntu to rename in UEFI the grub entry to read Windows. But you still show Windows as name and bootmgfw.efi as boot file.

```
 Boot0008* [COLOR=#ff0000]Windows Boot Manager[/COLOR] HD(1,800,100000,24a9417a-1173-4838-9223-0ed95e7aae44)File(\EFI\MICROSOFT\BOOT\[COLOR=#ff0000]BOOTMGFW.EFI[/COLOR] )WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a .8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................


```

---

### Post by carlo8 on 2015-02-19
Ok sorry, I'm kinda lost, I didn't get what I should do now.....:confused:

---

### Post by oldfred on 2015-02-19
Did you copy known good bootmgfw.efi to /efi/Microsoft/Boot overwriting existing one?

Not sure what else, I do not see how UEFI could want to boot grub from that file or folder?

---

### Post by jason.e.cobb on 2015-02-19
I see one option for you. I assume that the file system on the actual installations is intact, as you had only mentioned bad boot sector. You could simply backup all important files from the disk, and use an Ubuntu live disk. On this disk, there should be GParted, you could use this to create a new GPT partition table. THIS WILL WIPE ALL DATA ON DRIVE! Then, you could fresh install Windows, since you semmed to be able to do so before, and then install Ubuntu. Be careful to boot ALL installer disks in same mode (UEFI), as mentioned before by oldfred, and which I did not know before.

I hope this helps.

(jason.e.cobb)

---

### Post by carlo8 on 2015-02-20
> **oldfred said:**
> Did you copy known good bootmgfw.efi to /efi/Microsoft/Boot overwriting existing one?



IT WORKED!!!!!
I copied the bootmgfw.efi file from the Windows folder to /efi/Microsoft/Boot and now the dual boot is working again!!!
I'll be honest, I didn't do it immediately 'cause I suspected it would not work (I thought I had to modify **the path** of the file GRUB was looking for, not the file itself).....shame on me for not trusting you! :p

Thank you so much for your help oldfred, you really saved me.

And thanks to jason.e.cobb for your suggestion too (I'm happy I did not have to reinstall everything from scratch, though! :D)

---

### Post by oldfred on 2015-02-20
Glad it worked. :)

---

### Post by jason.e.cobb on 2015-02-22
Me too! :grin: Just glad you were able to recover!

---

