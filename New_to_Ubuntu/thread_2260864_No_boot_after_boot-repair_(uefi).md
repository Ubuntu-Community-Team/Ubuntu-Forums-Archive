---
title: "No boot after boot-repair (uefi)"
date: 2015-01-14
forum: New to Ubuntu
---

### Post by franky2 on 2015-01-14
[FONT=arial]After boot-repair: I reboot and nothing happens. Only [/FONT][B][grub2]("https://www.google.nl/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CCoQFjAB&url=http%3A%2F%2Faskubuntu.com%2Fquestions%2F362689%2Fgpt-detected-please-create-a-bios-boot-partition-while-using-boot-repair&ei=Bf62VOJYiKtRy7SDUA&usg=AFQjCNEeu17qOAo180FRQ8a3NvSk9xx6_Q&sig2=eltemrxDffvcgr9EHWGvGQ&bvm=bv.83640239,d.d24") menu appears with choices of ubuntu and advanced ubuntu options but neither load. 
they get stuck at (initramfs) switched to clocksource tsc..[/B]

I am new to the forum so please excuse my errors/ignorance or lack of info :))
 I was running boot-repair tool cause of black screen in booting and followed instructions:

[FONT=arial]
[/FONT][FONT=arial]Boot successfully repaired.[/FONT]
[http://paste.ubuntu.com/9752816/](http://paste.ubuntu.com/9752816/)



[FONT=arial]You can now reboot your computer.[/FONT]
[FONT=arial]Please do not forget to make your BIOS boot on sda (500GB) disk!


[/FONT]I think I did not set the boot on sda in bios.
Any ideas what to do? I wanted to install Xubuntu (that I liked better) and I already have it on a usb stick, but it does not load it..

Any help would be great

Thanks
Franky

---

### Post by franky2 on 2015-01-15
hello Everyone,
I am stuck at (initramfs) and no boot after using boot-repair tool
[http://paste.ubuntu.com/9752816/](http://paste.ubuntu.com/9752816/)

(I have lubuntu installed - which gave me boot in black screen after a few days, on an uefi asus netbook)

Any help would be appreciated.

Franky

---

### Post by fantab on 2015-01-15
> I was running boot-repair tool cause of black screen in booting 
This is generally a graphics issue, which is usually remedied with using '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option.

```

parted -l:

Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size    File system     Name  Flags
1      1049kB  538MB  537MB   fat32
2      538MB   498GB  498GB   ext4                  bios_grub
3      498GB   500GB  2012MB  linux-swap(v1)        bios_grub

```
Using Gparted remove the 'bios_grub' flags from both, 2 & 3 parititon or /dev/sda2 and /dev/sda3.
Secondly, add a 'boot' flag to /dev/sda1 or your first partition.

See if you are able to boot..

If you can't then Re-run Boot-Repair tool, use Advanced options and install Grub to ESP [EFI System Parttion], which is /dev/sda1 or the FAT32 partition to which you added a 'boot' flag.

---

### Post by grahammechanical on 2015-01-15
Please do not double post about the same problem.

[http://ubuntuforums.org/showthread.php?t=2260918](http://ubuntuforums.org/showthread.php?t=2260918)

Personally, I would like to see a screenshot of Gparted showing the partitions. That Boot Repair report does not show one Ext4 partition with Ubuntu on it. And that is unusual. Are you running Boot Repair from a Live session or from Xubuntu installed on the hard disk.

> [COLOR=#666666]===================[/COLOR] os-prober:
/dev/sda2:The OS now in use - Ubuntu 14.10 CurrentSession:linux

> [COLOR=#BB4444]=================== No kernel in /media/laura/C8A7-9A41/boot:[/COLOR]

And yet there is this

> update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-29-generic
Found initrd image: /boot/initrd.img-3.16.0-29-generic
Found linux image: /boot/vmlinuz-3.16.0-28-generic
Found initrd image: /boot/initrd.img-3.16.0-28-generic
Found linux image: /boot/vmlinuz-3.16.0-23-generic
Found initrd image: /boot/initrd.img-3.16.0-23-generic

---

### Post by oldfred on 2015-01-15
Merged threads, please do not post duplicate threads on same topic. 

We all are volunteers and need to know what has been posted to avoid duplication and wasted effort.

---

### Post by franky2 on 2015-01-15
> **fantab said:**
> 
If you can't then Re-run Boot-Repair tool, use Advanced options and install Grub to ESP [EFI System Parttion], which is /dev/sda1 or the FAT32 partition to which you added a 'boot' flag.


Thank you very much for your help Fantab, but as I cannot boot into any mode so I don´t know how to actually run the boot-repair tool like this

---

### Post by franky2 on 2015-01-15
Sorry for the double post oldfriend, I thought I posted in the wrong place, that´s why I did it again in "New in Ubuntu". Won´t do it again :)

I tried the [COLOR=Navy]For info on UEFI boot install & repair:
[/COLOR][COLOR=#000000][/COLOR][http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

but apparently instead of fixing what Fantab said must have been an [COLOR=#000000]graphics issue, I made matters worse...[/COLOR]

---

### Post by franky2 on 2015-01-15
thanks for the help grahammechanical, I was running boot repair from Lubuntu installed on the disk. But now I cannot run anything as it gets stuck on boot, so I cannot take [COLOR=#000000]screenshot of Gparted showing the partitions. Or I don´t know how to access this info.[/COLOR]

---

### Post by oldfred on 2015-01-15
You can run Ubuntu or Lubuntu live installer and add Boot-Repair or run other commands to update system.

You may need to change UEFI/BIOS settings. Try both UEFI and BIOS, but you really are UEFI and only should boot in UEFI mode.

And black screen is almost always video related. What video card/chip do you have?

---

### Post by franky2 on 2015-01-15
> **oldfred said:**
> You can run Ubuntu or Lubuntu live installer and add Boot-Repair or run other commands to update system.

?

That was my problem...I connect the usb and boot but I don´t know how to access the live stick as I get stuck on the [COLOR=#333333][FONT=UbuntuRegular]grub2 menu with 2 options Ubuntu or Ubuntu advanced settings (that neither boot). Is there a command I can run from there to boot from usb stick?[/FONT][/COLOR]


> **oldfred said:**
> You may need to change UEFI/BIOS settings. Try both UEFI and BIOS, but you really are UEFI and only should boot in UEFI mode.?

Do you know any commands to access it without booting into Lubuntu ?

> **oldfred said:**
> And black screen is almost always video related. What video card/chip do you have

Computer was new and I din´t  get the chance o check...
 
thanks sooo much for the help !!



[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

---

### Post by oldfred on 2015-01-15
UEFI and BIOS settings are long before grub menu. 

You should see a UEFI/BIOS screen just as system starts. If you still have a fast boot in UEFI which is different than a fast boot in Windows you may not see any UEFI screen. Often then a cold boot or shutdown totally power off, remove battery if laptop and hold power switch to drain any power. Then boot and press correct key for UEFI for your brand /model computer. Check manual if not sure, but often del, f2 or other.

What brand model system? And what video card/chip?

---

### Post by franky2 on 2015-01-16
> **oldfred said:**
> UEFI and BIOS settings are long before grub menu. 

You should see a UEFI/BIOS screen just as system starts. If you still have a fast boot in UEFI which is different than a fast boot in Windows you may not see any UEFI screen. Often then a cold boot or shutdown totally power off, remove battery if laptop and hold power switch to drain any power. Then boot and press correct key for UEFI for your brand /model computer. Check manual if not sure, but often del, f2 or other.

What brand model system? And what video card/chip?
 
I have asus netbook. Managed to enter uefi settings but pressing delete when computer opens.

info on video card:
[FONT=arial]*-display               [/FONT]
[FONT=arial]       description: VGA compatible controller[/FONT]
[FONT=arial]       product: ValleyView Gen7[/FONT]
[FONT=arial]       vendor: Intel Corporation[/FONT]
[FONT=arial]       physical id: 2[/FONT]
[FONT=arial]       bus info: pci@0000:00:02.0[/FONT]
[FONT=arial]       version: 0c[/FONT]
[FONT=arial]       width: 32 bits[/FONT]
[FONT=arial]       clock: 33MHz[/FONT]
[FONT=arial]       capabilities: pm msi vga_controller bus_master cap_list rom[/FONT]
[FONT=arial]       configuration: driver=i915 latency=0[/FONT]
[FONT=arial]       resources: irq:106 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)

[/FONT]UPDATE:
I managed to enter uefi settings and when trying to run "try ubuntu" I get the black screen again so not able to update or access boot-repair tool.

Update 2:
By trying different options in the uefi menu, I enabled "fast boot" and finally run xubuntu in live mode. Now trying to do repairs with boot-repair.

Upadte 3: Boot repair said boot fixed
[FONT=arial]Boot successfully repaired.[/FONT]

[FONT=arial]Please write on a paper the following URL:[/FONT]
[http://paste.ubuntu.com/9761291/](http://paste.ubuntu.com/9761291/)

But fresh install for xubuntu gave me this error:
[FONT=arial]The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.

[/FONT]Tried to run gparted from ubuntu live mode . I had to loggin as root user to be able to do so, and followed instuctions from another thread:
[COLOR=#333333][FONT=UbuntuRegular]if you want to turn into a root user then you can use sudo -i from terminal .
[COLOR=#000000]
[/COLOR]> [COLOR=#000000]Using Gparted remove the 'bios_grub' flags from both, 2 & 3 parititon or /dev/sda2 and /dev/sda3.[/COLOR]
[COLOR=#000000]Secondly, add a 'boot' flag to /dev/sda1 or your first partition.[/COLOR]

[COLOR=#000000]See if you are able to boot..[/COLOR]

[COLOR=#000000]If you can't then Re-run Boot-Repair tool, use Advanced options and install Grub to ESP [EFI System Parttion], which is /dev/sda1 or the FAT32 partition to which you added a 'boot' flag. [/COLOR][FONT=Verdana]

So all this is done
I have:
sda1 - fat32 with boot flag
sda2 ext4 - /target with no flags
sda3 linux-swap no flag
unallocated 1.01mb no flags

But still cannot do fresh install

[/FONT][/FONT][/COLOR][FONT=arial]

[/FONT]

---

### Post by oldfred on 2015-01-16
It looks like now grub is correctly installed to efi partition for UEFI boot. The grub in the MBR for BIOS boot will not work and is not required, but is no issue.

With only one install you normally should not get grub menu, but may have to press escape key at UEFI first boot screen before grub stgarts to load.

With Intel nomodeset does not work, but other settings may which you add the same way to grub menu's linux line. See ubfan1's post.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by LostFarmer on 2015-01-16
Which ASUS do you have.  My ASUS X551MA would fail installing grub ,Ubuntu,Mint.  Once I finally got linux to boot, it would not load all the EFI firmware (i think).  My ASUS after 4 weeks would not even post so sent it back for repair last week.  I would  suggest doing a bios update to see if it helps.   

You could delete all and be sure to boot/install in MBR mode, so EFI would not be used.

---

### Post by franky2 on 2015-01-16
If only I knew that half an hour ago. I thought the no grab-efi issue, was serious, so as suggested in another thread, i formated the [COLOR=#333333][FONT=Verdana]sda1 - fat32 with boot flag[/FONT][/COLOR]
 partition and then tried a fresh install. So now I cannot install it again, and I am left with no operating system, as installer quits when [COLOR=#000000][FONT=arial]'grub-efi-amd64-signed' package failed to install into /target/. 

Also tried this suggestion but didn´t work
[/FONT][/COLOR]http://askubuntu.com/a/500098

---

### Post by franky2 on 2015-01-16
> **LostFarmer said:**
> Which ASUS do you have.  My ASUS X551MA would fail installing grub ,Ubuntu,Mint.  Once I finally got linux to boot, it would not load all the EFI firmware (i think).  My ASUS after 4 weeks would not even post so sent it back for repair last week.  I would  suggest doing a bios update to see if it helps.   

You could delete all and be sure to boot/install in MBR mode, so EFI would not be used.

I have asus x200m. From what I have been told is that if I have efi I should use efi to install xubuntu and not mbr mode as that could cause problems. As I am very new and with very little knowledge I am a bit afraid to disobey hahahaha.  What do you think?

---

### Post by LostFarmer on 2015-01-16
You should be able to install in MBR mode but it must be done correctly.  One must change the hdd from EFI to MBR correctly, or you will have problems.  I do not know the correct way so will let 'oldfred'  give instructions if he think that is the way to go.

---

### Post by franky2 on 2015-01-16
thanks a lot old farmer. I don´t know either, trying different installation types and settings, but I think the partition that I formated (sda1/fat32/boot) messed things up, cause in gparted I see that partition sda2/ext4 still has 10giga used, so something must be installed but uefi settings don´t see any operating system, or anything to boot with except usb stick...

---

### Post by oldfred on 2015-01-16
A lot of the UEFI have been modified by the vendor to only boot "Windows" and we have to do various work arounds. One major work around is a BIOS install, but most are able to use various UEFI work arounds.

Do you get grub menu?
If not make sure secure boot is off, but UEFI is on, not BIOS/CSM/Legacy or whatever your system calls it.

All the work arounds. If only Ubuntu and no Windows often just renaming the UEFI entry works. Others have to copy grub/shim into /EFI/Boot and rename it bootx64.efi which is the hard drive entry that vendors still allow to boot.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Various Asus models, not sure if yours is similar or not.

 UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

This was a Toshiba, but same type of issue with details on fix that worked.

 Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)

---

### Post by franky2 on 2015-01-17
> **oldfred said:**
> 
Do you get grub menu?
If not make sure secure boot is off, but UEFI is on, not BIOS/CSM/Legacy or whatever your system calls it. 

when I have no usb of xubuntu plugged in get direclty uefi menu and no boot option (menu for boot options is blank)
with xubuntu live usb plugged I get grub menu of trying or installing Xubuntu

Secure boot is off and there´s no option for BIOS/CSM/Legacy (there never was one).

I don´t understand if there is xubuntu installed or not, and wheather that´s just a boot problem that you´re explaining how to work around.
( So I dont helplessly try to fresh install xubuntu every time :))

And about the black screen that I still get occasionally that you said that is fixed by NOMODESET, is that something that I try to fix before the booting issue, after, or is irrelevant? I read the thread about it, ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)) but I am not sure if I can use these comands in live session, or I have to do them through gryb, once everything is up and running.


This is my boot-repair report:
[URL="http://paste.ubuntu.com/9767487/"]
http://paste.ubuntu.com/9767487/[/URL]

[FONT=arial]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

thanks again very much

[/FONT]

---

### Post by oldfred on 2015-01-17
If you have an UEFI system, you need to always boot in UEFI mode.
If Boot-Repair is asking for a bios_grub partition, which it cannot create, then you have booted in BIOS mode and it wants to install the BIOS boot version of grub.

Only some crippled 32bit UEFI systems are the new class 3 UEFI or UEFI without BIOS mode. But if you are booting flash drive in BIOS Mode then you have a BIOS mode.

There really are three boot modes. UEFI with secure boot, UEFI, and CSM or BIOS/legacy. But some lower cost systems have a very limited UEFI and do not make it clear or auto switch between modes depending on what is found.

Can you press escape key when booting without flash drive? If at UEFI then escape key should bring up grub menu. Then you can add mode settings for Intel type video.

---

### Post by franky2 on 2015-01-21
oh, now I understand a bit more :)
When I press esc at boot without usb, a blue box appears 
 please select boot device:
Enter setup

No other option, no boot device, so I can only enter the same setup menu, that is like the old bios menu (I am assuming it is the uefi settings)

But when I boot from usb in the boot option it says: UEFI:scandisk (that is the brand of my usb)...

I can´t seem to be able to get to the grub menu or uefi boot.

---

### Post by oldfred on 2015-01-21
Did you look at the other threads with Asus systems and run the detailed commands in the Toshiba P50 thread?
You often have to create a hard drive boot in /EFI/Boot/bootx64.efi or rename grub or shim's entry in UEFI to be Windows to get it to boot. Vendors are modifying UEFI to only boot by description where description must read "Windows" or you can boot a hard drive entry. The ubuntu entry just will not work, but with UEFI it should.

---

### Post by franky2 on 2015-01-22
Hello Again,
tried :
the renaming of grub, did not work (manually or through boot-repair)
reFind bootloader : Did not work (only option was to shut down or restart)
Different settings in uefi, 
updating bios
Creating new  boot option with edited path - did not work (did not even see anything except usb)

Tried anything I remotely understood in those threads :))

What did it in the end was downgrading bios (by flashing it through usb with the help of a friend)
And then I could finally see all those settings that people where talking about in those threads. 

Successfully installed xubuntu

Thank you very much everyone for he help.

---

