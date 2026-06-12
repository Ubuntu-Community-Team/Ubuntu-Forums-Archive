---
title: "How to restore Windows 8 bootloader after installing Ubuntu 14.04"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by dss1873 on 2014-09-14
System: Dell XPS 8700 running Windows 8.1 using secure boot and UEFI.

Boot Info Summary: [http://paste.ubuntu.com/8340337/](http://paste.ubuntu.com/8340337/)

I installed Ubuntu on a USB flash drive using the Live CD version. My goal was to keep the Dell untouched and have Ubuntu on a removable flash drive that I could plug into the computer, hit the appropriate key on my computer at power on to get a list of boot options and then choose Unbuntu when I wanted to run Ubuntu. Otherwise, with the flash drive removed, the computer would run Windows 8.1 as before

To install Unbuntu, I created a EFI system partition on the flash drive (sdf1) and explicitly specified during installation that the Grub files be installed there and not on my Windows drive (sda).

Everything works fine if I have the flash drive with Ubuntu plugged in and turn on the computer. Grub comes up with a menu of boot options including Windows and both Ubuntu and Windows run fine. The problem is that if I remove the flash drive from the computer, then instead of booting Windows I get a Grub command prompt.

1) What do I need to do to get the Dell computer back to it's original state where it boots Windows as it did before using the Windows bootloader. It's my father's computer so I need to get it back to the way it was (I did it on his computer because I had tried on mine, but couldn't get Ubuntu to install on the flash drive).

I've researched the problem and tried most of the things on the Windows end (running Windows repair, booting to a command prompt and running bootrec /fixboot and such). I think I did see somewhere that perhaps Ubuntu renames the Windows bootloader to shimx64.efi (or maybe it is only BootRepair that does that). Can it be as simple as renaming /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi??

2) Once I've fixed the computer, can I copy the boot files in sda2 to sdf1 in order to be able to get my flash drive to boot when plugged into the computer? This is not a big deal as I can live without the Ubuntu; my primary concern is getting the computer back to booting Windows.

I'm hoping somebody out there actually knows how this works and what the Ubuntu install does and how to reverse it or at least what needs to be reversed instead of just guessing at things that may work which is what I've been doing for the last several days from the information on various forums. It seems like things are working as they should (other than the fact that the Ubuntu boot files got installed on sda2 instead of sdf1 as I specified) so there should be no "bugs" or guesswork in any of this--just a question of understanding what the Ubuntu install did. 

Please let me know if this would be a question better asked elsewhere.

---

### Post by fantab on 2014-09-14
There are some errors in your bootinfo but I would first change the 'boot device' from USB to HDD... or from Ubuntu to Windows in UEFI/BIOS menu....
If you don't want grub to load when USB is unplugged.. then you should set the machine to boot from HDD Windows Efi file:
Windows Boot Manager	HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(**EFIMicrosoftBootbootmgfw.efi**)


```
efibootmgr -v
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,0003,0007,0008,0005,0006,0001,0000,0002
Boot0000  P0: ST1000DM003-1CH162        	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001  P1: MATSHITA DVD+/-RW SW830   	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0002  Realtek PXE B03 D00	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0003* Windows Boot Manager	HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...h................
Boot0004* ubuntu	HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(EFIubuntushimx64.efi)
Boot0005* UEFI: IP4 Realtek PCIe GBE Family Controller	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8b156ad13f6,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0006* UEFI: IP6 Realtek PCIe GBE Family Controller	ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8b156ad13f6,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0007* ubuntu	HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(EFIUbuntugrubx64.efi)
Boot0008* UEFI: MATSHITA DVD+/-RW SW830	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000CD-ROM(1,86c,1d04e5)..BO
```

```
Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdf.
```

It is unusual to have "*Windows 7/8/2012 is installed in the MBR of /dev/sda*" on a UEFI boot.
This could be because of your 'fixmbr' fix.

---

### Post by oldfred on 2014-09-15
You say when you installed you specified that grub be installed to the sdf drive.

But your sda1 efi partition has all the efi boot files and the sdf1 efi partition is not showing any efi boot files.
But since Windows efi boot files are also in sda1, that should also boot. What is boot order in UEFI set to. There may be several lists as BootCurrent is just last boot, BootOnce is a setting to change UEFI so next reboot is that boot order. It may also have secure boot boot order and UEFI (not secure boot) boot order.

I might just copy the /efi/ubuntu folder from sda1 to sdf1. With UEFI you should not have to do any special install to use that as the boot. But UEFI has its own memory and may need updates to remove old entries.
But you also need to change fstab UUID from the UUID of sda1 to the UUID of sdf1 so updates will reinstall to the correct efi partition.

If you want to be sure you can do a full uninstall reinstall of grub and be sure to install to sdf.

# to see current entries directly or same as shown in Boot-Repairs report
       modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by dss1873 on 2014-09-15
Thanks fantab & oldfred!

> I would first change the 'boot device' from USB to HDD... or from Ubuntu to Windows in UEFI/BIOS menu....
If you don't want grub to load when USB is unplugged.. then you should set the machine to boot from HDD Windows Efi file:
Windows Boot Manager    HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(**EFIMicrosoftBootbootmgfw.efi**)

Ok, how do I do that? It's not an option showing on my machine boot options screen. See below image.

> 
You say when you installed you specified that grub be installed to the sdf drive.
But your sda1 efi partition has all the efi boot files and the sdf1 efi partition is not showing any efi boot files.

Yes, that was my point is that Ubuntu put all the files on sda1 and none on sdf. Because I've done this numerous times, I was specific about selecting sdf1.

> 
 But since Windows efi boot files are also in sda1, that should also  boot. What is boot order in UEFI set to. There may be several lists as  BootCurrent is just last boot, BootOnce is a setting to change UEFI so  next reboot is that boot order. It may also have secure boot boot order  and UEFI (not secure boot) boot order.

See below image of my boot options screen on my Dell. I don't see a way to select an option to boot from Windows EFI from sda1.

[ATTACH=CONFIG]256469[/ATTACH]

---

### Post by oldfred on 2014-09-15
Now that is unusual. 
Almost always it shows Windows and we have issues getting it to show ubuntu. 

You do show secure boot enabled. But again it is Windows that works with secure boot and you can install Ubuntu either with or without secure boot so it then depends on UEFI settings.
Try with secure boot off. But I do not expect that to make any difference.

Since XPS model this may apply.
       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by dss1873 on 2014-09-15
Again, at this point I don't care about Ubuntu. I just want to get the system back to the way it was before I installed Ubuntu on the flash drive (so the computer uses the original Windows bootloader and automatically boots Windows on startup).

I'm just totally guessing but is this the way the UEFI works: at startup the firmware executes sda2/EFI/Boot/bootx64. That then calls sda2/EFI/ubuntu/shimx64.efi which in turn starts sda2/EFI/ubuntu/grubx64.efi. Grub in turn gets the configuration settings and menu options from sdf2/boot/grub/grub.cfg & /etc/fstab. So what Ubuntu did was change bootx64 either by replacing the file or modifying it and what I need to do is get bootx64 back to the way it was.

If I can understand the way things work and what the Ubuntu install did then I have some chance of fixing it versus just stabbing in the dark.

---

### Post by LostFarmer on 2014-09-15
Try changing the efi boot order with linux command **sudo efibootmgr -o 0003,0004**  that should put Win8 first.  
or
You can see if your comps Setup utility will let you change the boot order, see if you can put the curser on 1st boot device, if so click it, it may have a drop down of all efi devices you can select.

---

### Post by ubfan1 on 2014-09-15
Can you use a function key at power-on and bring up the efi menu (the one which offers devices /OSes to boot)?  If so, can you boot Windows from it (might have to select HDD first, then a Windows /ubuntu choice will be presented)?  The nvram boot order might have been changed, but the Windows bootloaders should not have been UNLESS you have done that in the boot-repair yourself (undo it if so). 
 Now, on removable media like USB, the bootloader is in /EFI/Boot/bootx64.efi (on the EFI partition), and that should be a copy of shim.efi in your case of secure boot.  The grubx64.efi (signed) should also be present in /EFI/Boot.  The grub.cfg three line stub should be present in /EFI/ubuntu (along with shim and grubx64).  You can set this up yourself, all the files are in the internal disk's /EFI partition, just copy them over.  
  On the internal disk's EFI partition, the /EFI/Boot/bootx64.efi is not normally used, BUT some machines (like my Toshiba) will fall back to trying that if a boot failure occurs, like trying to boot grubx64.efi (instead of shim.efi ) when secure boot is enabled.  I always have it set up as shim and the grubx64.efi present just like on the USB for this reason.  Running from USB on a UEFI machine can and will result in unwanted changes to nvram boot entries and order!  Nasty!  I got in the habit of using the efi menu to select my OS, but my problem is that it is Windows which keeps putting itself first.  But this is on a machine with both OSes on the hard disk, so hopefully, keeping your internal disk just Windows will avoid such changes.

---

### Post by fantab on 2014-09-15
> Again, at this point I don't care about Ubuntu. I just want to get the  system back to the way it was before I installed Ubuntu on the flash  drive (so the computer uses the original Windows bootloader and  automatically boots Windows on startup).
You can undo all the changes made to partitions, delete linux partitions, then run 'Recovery' to restore everything to 'factory setting'.
*Backup your DATA *before embarking to do the above.
[http://www.hasper.info/repair-a-destroyed-windows-7-uefi-boot-sector/](http://www.hasper.info/repair-a-destroyed-windows-7-uefi-boot-sector/)
The link shows how fix uefi boot secotr in Win7.

Yes it is very strange that your UEFI menu does not show Windows.... 
Ubuntu uses 'shim' to use Microsoft key to boot with 'Secureboot' enabled.
If secure boot is disabled, then grub uses 'bootx64'.
To boot windows Grub chainloads the windows boot manager...
```

menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-2421-7D76' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  2421-7D76
    else
      search --no-floppy --fs-uuid --set=root 2421-7D76
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
```

The real issue seems to be the missing Windows entry in the UEFI menu (from the screenshot you posted).
You can try booting into windows and running '[chkdsk]("http://www.w7forums.com/threads/how-to-use-chkdsk-check-disk.448/")' on both FAT32 ESP and Windows C: and see if it helps.

Edit:
@ubufan:
> The nvram boot order might have been changed, but the Windows  bootloaders should not have been UNLESS you have done that in the  boot-repair yourself (undo it if so).
What settings in BR do that? I mean how can nvram boot order be changed from Boot-Repair?

---

### Post by oldfred on 2014-09-15
UEFI normally boots the /Windows/Boot/bootmgfw.efi file directly. And the bootx64.efi is a hard drive entry as a backup. Newer Windows 8 systems often modified UEFI internally to only boot the bootmgfw.efi, but will boot boox64.efi, but not anything else. So the work around like ubfan1 did is common.

You should have a backup of the Windows file:
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

You may be able to add an entry to UEFI with efibootmgr also.
      
 modprobe efivars
sudo efibootmgr -v
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

This adds ubuntu and uses many of parameters together to build a new entry.
efibootmgr -c -d /dev/sda -p 2 -w -L ubuntu -l EFIubuntushimx64.efi.

---

### Post by dss1873 on 2014-09-18
I tried using efibootmgr to change the boot order and get an error that boot entry 3 does not exist which is weird because the verbose option lists entry 3 as the Windows entry. This would explain why the Windows option does not show up in my computer BIOS setup boot options screen I suppose or why the system can't boot to Windows if my flashdrive is removed. But as I stated, Windows boots and runs fine if I select it from the grub menu choices.
[B]> [B]$ efibootmgr -o 0003,0004,0007,0005,0006,0001,0000,0002

boot entry 3 does not exist[/B]
[/B]

This is the output from sudo efibootmgr -v:[B]

> BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,0003,0007,0005,0006,0001,0000,0002
Boot0000  P0: ST1000DM003-1CH162            Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001  P1: MATSHITA DVD+/-RW SW830       Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0002  Realtek PXE B03 D00    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0003* Windows Boot Manager    HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...h................
Boot0004* ubuntu    HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(\EFI\ubuntu\shimx64.efi)
Boot0005* UEFI: IP4 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8b156ad13f6,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0006* UEFI: IP6 Realtek PCIe GBE Family Controller    ACPI(a0341d0,0)PCI(1c,2)PCI(0,0)MAC(f8b156ad13f6,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0007* ubuntu    HD(2,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(\EFI\Ubuntu\grubx64.efi)

[/B]I tried running chkdsk on esp partition and it reported no errors. For kicks, copied C:\Windows\Boot\EFI\bootmgfw.efi to esp partion and made no difference. The ESP partition and windows boot files all seem perfectly fine so completely puzzled while efibootmgr reports that boot entry 3 does not exist.

I tried changing boot mode to legacy and system would not longer boot at all.

I can try using efibootmgr to delete windows entry and then create a new one, but need some assistance. Would the following command be correct to create a new one afer trying to delete the old one (though I assume there is a good chance I will just get the error "boot entry 3 does not exist" when I try to delete it as efibootmgr won't let me re-order it).

[B]efibootmgr -c -d /dev/sda -p 2 -w -L Windows -l                  \EFI\Microsoft\Boot\bootmgfw.efi

c - to create a new entry seems right
d - specify disk containing loader so  /dev/sda for me?
p - partition contianing loader so  2 for me which is the esp partition sda2
w - write unique signature to MBR so do I need that since I have gpt? I would guess not.
L - label to display seems fine
l - I assume the \efi\microsoft\bootmgfw.efi is the loader I want on the esp partition on sda2



[/B]

---

### Post by LostFarmer on 2014-09-18
> [B]efibootmgr -c -d /dev/sda -p 2 -w -L Windows -l                  \EFI\Microsoft\Boot\bootmgfw.efi
[/B]  almost correct ,  \EFI\Microsoft\Boot\bootmgfw.efi needs to be**'**\EFI\Microsoft\Boot\bootmgfw.efi'  , notice the **' '**.

I think I would give it a different name , for testing I have use Win8.   added:  for testing with comps boot hot key, grub.cfg would need to be updated for grub to use it.


One thing I do not understand yet, and do not know just how the EFI firmware works but, your efi output data:
"Boot0003* Windows Boot Manager HD(**2**,400800,fa000,5a1b3905-cb6e-43ce-856f-b6c24a729cf1)File(\EFI\Microsoft\Boot\bootmgfw.efi )WINDOWS"  the **2** is the hdd number , the next 2 hex numbers is the start sector and # of sectors of efi partition, the next long number is the Partition unique GUID # , can be seen with gkisk option i. why the 2 not 1, could be the problem.  

I did at one time try to use efibootmgr to delete an entry and it gave me your error, that was due to me having deleted the file in the EFI partition.

---

### Post by LostFarmer on 2014-09-19
Try the efibootmgr commands from a LIve CD not the installed linux on the usb.  when you boot the installed usb drive the system might be seeing it as drive 1 and the internal hdd as drive 2.

---

### Post by Michael_McKenney on 2014-09-19
You could try a repair install from Windows 8.   Did you change any of the BIOS or chipset settings?  If yes, change them back first.  I hope you don't break the secured encryption of Windows 8, if it is fully configured.  You will not be able to recover the files.  Did you at least backup his workstation or does he have cloud backup or an external drive backup?   

Windows 7, 8, and 2012 use same boot loader so they could show up as just a generic entry meaning you have one of the three installed.  Yes, I do have a test lab with the Windows 7, 8, 8.1 and server 2012 installed on the same box for testing software.  It is common in a corporate environment to have a test server with multiple OS installations for testing on one box.

---

### Post by dss1873 on 2014-09-19
It turned out to be a simple fix (to return the system where it boots Windows when the Ubuntu flash drive is not plugged in). I went to BIOS and chose to reload the default settings. That made the Windows boot manager show up once again and everything is back to working the way it way.

---

