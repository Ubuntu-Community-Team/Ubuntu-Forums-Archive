---
title: "Messing around with easy bcd, messed up MBR"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by 3219150-r on 2014-04-09
So, last night i was messing around with easyBCD 2.2 trying to repair my legacy win8 MBR when i messed it up even worse.

I can boot from ubuntu 12.04 efi file, but not into windows from that efi file. I can boot into windows in uefi mode.
Before, when i started it it would go straight to GRUB2 and would boot into ubuntu, but not windows 8 (The boot configuration files are missing or contain errors). Now, when trying to boot legacy, instead of grub menu, i get "No bootable device -- insert boot disk and press any key".


I could not originally boot into windows 8, but i fixed that with bootrec /fixmbr, bootrec /rebuild bcd and /fixboot. After that I used boot-repair to no avail. I believe the problem is that my bios is not pointing to my hard drive, but i have no idea why. My Boot-repair url is '[http://paste.ubuntu.com/7227528/](http://paste.ubuntu.com/7227528/)'. I'm not sure what exactly what everything there means, or how it relates to my problem. I'm new to ubuntu, but good with computers, so any help is appreciated(No matter how advanced it is) Any way to fix?

---

### Post by oldfred on 2014-04-10
Clickable link
[http://paste.ubuntu.com/7227528/](http://paste.ubuntu.com/7227528/)

At some point you did install Ubuntu (or Kali) in BIOS boot mode. That is not compatible with UEFI, and you then can only boot from UEFI/BIOS menu. Many system then also require you to turn on/off UEFI mode and/or turn on/off BIOS/CSM/Legacy boot mode to change from one boot mode to the other.
UEFI & BIOS are not compatible and once you start booting in one mode you cannot change. Or once you start to boot and are at grub in BIOS mode you cannot boot Windows in UEFI mode. 

It also looks like you converted or Installed Ubuntu in UEFI mode, but Kali is still in BIOS boot mode. You may be able to reinstall Kali's boot loader to gpt's protective MBR to boot Kali in BIOS mode, but will not be able to boot from Ubuntu's grub even if shown in menu.

It also looks like you ran Boot-Repair's 'buggy' UEFI. That is for systems that modify UEFI to only boot Windows. It renames grub/shim to have the Windows efi file name, but then you only can boot Windows from grub menu as it has a different name.
Not sure if HP's need rename to boot or not?

This is the renamed (bkp at beginning) Windows file that should boot Windows from grub menu.
>  menuentry "Windows UEFI [COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi" {



Because of the rename, from UEFI menu booting Windows entry takes you to grub menu. 
But if you can directly boot ubuntu entry in UEFI menu, you do not need rename.

       Line 1048 in script is an extract from UEFI. If you can boot either of ubuntu entries 0002 or 0005 which are grub and shim, then you do not need rename. If you can only boot Windows you need rename, but have to know the issues.
BootOrder: 0001,3001,[COLOR=#ff0000]0002[/COLOR],0005,2001,2002,2003
Boot0000* Notebook Hard Drive	BIOS(2,500,00)................-.U.......U.A.U........................................
Boot0001* Windows Boot Manager	HD(2,c8800,82000,5e937f74-b55b-4280-b5ec-0763344de30f)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot[COLOR=#ff0000]0002[/COLOR]* ubuntu	HD(2,c8800,82000,5e937f74-b55b-4280-b5ec-0763344de30f)File(EFIubuntushimx64.efi)
Boot0005* Ubuntu	HD(2,c8800,82000,5e937f74-b55b-4280-b5ec-0763344de3

Make sure secure boot is off. And fastboot is off. Windows may on updates or changes or even edits to its settings reset to those on and you need to have them off.

You also changed grub's default

 GRUB_DEFAULT="Windows Boot UEFI loader"
But the current working one is
Windows UEFI [COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi

If you can boot ubuntu entry, use Boot-Repair to undo the rename. Then the grub default of Windows should be correct, but double check that it is exact.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Boot-Repair creates a 25_custom with all the extra .efi files as bootable including the renamed bkp files.
With 14.04, grub2's os-prober now correctly finds Windows efi file, and you may not need 25_custom at all. But if you have the buggy UEFI, you have to keep renamed Windows file but can house clean out most of the HP .efi boot entries in 25_custom. Details in link in my signature on house cleaning 25_custom.

---

### Post by 3219150-r on 2014-04-11
Can't boot with secure boot off, it does not detect my hard drive. Have tried all alternatives i could think of, to no avail. Originally I was booting windows 8 through secure boot, and then going legacy for ubuntu. Now, i have to boot from the EFI file i made. It can redirect me to Ubuntu or Kali with no problems, and Windows 8 secure boot EFI, but not standard Win8 boot file (Not efi).

---

### Post by oldfred on 2014-04-11
Microsoft agreed that secure boot would not be required for PCs. 
Have you updated UEFI/BIOS, vendors also are making many fixes.

But for some other new tablet or tabet with keyboard that are not PC and may use special processors as well may have locked UEFI where nothing else can be installed.

What model HP, processor & video card.

Some other HPs. Others seem to have had issues with many model HPs.
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

### Post by 3219150-r on 2014-04-11
Hp2000
Raedon hd 8400
amd a6-5200 2ghz
It's an internal HDD.

---

### Post by oldfred on 2014-04-11
Some more HP links, 

 HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

---

### Post by 3219150-r on 2014-04-15
Okay, so i fixed it, but now, in legacy mode, selecting windows 8,  i am getting "Windows failed to start. A recent hardware or software change might be the problem.... 0xc00000e The boot configuration data is missing or contains errors" I have no clue what's going on with windows. can still start in uefi mode.

---

### Post by oldfred on 2014-04-16
UEFI & BIOS are not compatible. So if one install is UEFI, you can only boot it from UEFI menu. And then you can only boot BIOS install from UEFI/BIOS menu. 
Or you cannot use grub to dual boot as once you start in BIOS and grub is in BIOS, you cannot switch to UEFI to boot Windows.
Some systems will auto switch in UEFI/BIOS menu. Others may require you to turn on/off UEFI mode or turn on/off BIOS boot mode to make switch.

---

