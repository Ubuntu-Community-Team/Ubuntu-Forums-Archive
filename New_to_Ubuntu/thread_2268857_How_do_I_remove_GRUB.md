---
title: "How do I remove GRUB?"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by numeric2 on 2015-03-12
Hello,
  How do I remove GRUB? I know this has been asked many times before; however none of the solutions have worked. Short of re installing Windows 8.1, is there a method that works?
  Windows and Ubuntu are installed on separate hard drives. I have no problem booting to Windows. There should be no need for the original install disks. Besides, the Dell computer came pre-installed with Windows. Also, there is no CD drive. It has two USB 3 ports and one USB 2 port. I can access the DOS screen command prompt on the Windows boot up procedure. Recently booting to Ubuntu no longer works, so I want to totally remove GRUB and start over again.

  Windows 8.1 is installed on an internal 500GB hard drive.
  Ubuntu 14.04.2 LTE is installed on an external 1TB Western Digital Elements USB 3 hard drive.
  So far I have tried:
  From DOS
  >bootrec  /fixmbr
  >bootrec  /fixboot
  The DOS fix fails to remove GRUB.
  I can boot to Ubuntu using the USB thumb drive which has the install option. I have been able to access the boot repair utility.


  [FONT=&amp]sudo add-apt-repository ppa:yannubuntu/boot-repair[/FONT]
  
  [FONT=&amp]sudo apt-get update[/FONT]
  
  [FONT=&amp]sudo apt-get install -y boot-repair && (boot-repair &)[/FONT]
  
  Unfortunately this did not remove GRUB.


  I have tried iterations with secure boot on and secure boot off, so far nothing works.
  My internal hard drive has the following partitions:
   
  [TABLE="class: MsoNormalTable, width: 317"]
[TR]
[TD="width: 96"]   [CENTER][CENTER]**[COLOR=black][FONT=Calibri]Partition[/FONT][/COLOR]**[/CENTER]
[/CENTER]
[/TD]
[TD="width: 96"]   [CENTER][CENTER]**[COLOR=black][FONT=Calibri]Size[/FONT][/COLOR]**[/CENTER]
[/CENTER]
[/TD]
[TD="width: 96"][/TD]
[TD="width: 202"]   [CENTER][CENTER]**[COLOR=black][FONT=Calibri]Type[/FONT][/COLOR]**[/CENTER]
[/CENTER]
[/TD]
[TD="width: 144"]   [CENTER][CENTER]**[COLOR=black][FONT=Calibri]Label[/FONT][/COLOR]**[/CENTER]
[/CENTER]
[/TD]
[/TR]
[TR]
[TD="width: 96"]   [RIGHT][RIGHT][COLOR=black][FONT=Calibri]-1[/FONT][/COLOR][/RIGHT]
[/RIGHT]
[/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]500M[/FONT][/COLOR][/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]FAT32[/FONT][/COLOR][/TD]
[TD="width: 202"]   [COLOR=black][FONT=Calibri]EF EFI[/FONT][/COLOR][/TD]
[TD="width: 144"]   [COLOR=black][FONT=Calibri]ESP........[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD="width: 96"]   [RIGHT][RIGHT][COLOR=black][FONT=Calibri]-2[/FONT][/COLOR][/RIGHT]
[/RIGHT]
[/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]40M[/FONT][/COLOR][/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]FAT32[/FONT][/COLOR][/TD]
[TD="width: 202"]   [COLOR=black][FONT=Calibri]07 NTFS, HPFS[/FONT][/COLOR][/TD]
[TD="width: 144"]   [COLOR=black][FONT=Calibri]DIAGS......[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD="width: 96"]   [RIGHT][RIGHT][COLOR=black][FONT=Calibri]-4[/FONT][/COLOR][/RIGHT]
[/RIGHT]
[/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]750M[/FONT][/COLOR][/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]NTFS[/FONT][/COLOR][/TD]
[TD="width: 202"]   [COLOR=black][FONT=Calibri]27 Windows RE H[/FONT][/COLOR][/TD]
[TD="width: 144"]   [COLOR=black][FONT=Calibri]WINRETOOLS.[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD="width: 96"]   [RIGHT][RIGHT][COLOR=black][FONT=Calibri]-5[/FONT][/COLOR][/RIGHT]
[/RIGHT]
[/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]456G[/FONT][/COLOR][/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]NTFS[/FONT][/COLOR][/TD]
[TD="width: 202"]   [COLOR=black][FONT=Calibri]07 NTFS, HPFS[/FONT][/COLOR][/TD]
[TD="width: 144"]   [COLOR=black][FONT=Calibri]OS.........[/FONT][/COLOR][/TD]
[/TR]
[TR]
[TD="width: 96"]   [RIGHT][RIGHT][COLOR=black][FONT=Calibri]-6[/FONT][/COLOR][/RIGHT]
[/RIGHT]
[/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]8G[/FONT][/COLOR][/TD]
[TD="width: 96"]   [COLOR=black][FONT=Calibri]NTFS[/FONT][/COLOR][/TD]
[TD="width: 202"]   [COLOR=black][FONT=Calibri]27 Windows RE H[/FONT][/COLOR][/TD]
[TD="width: 144"]   [COLOR=black][FONT=Calibri]PBR Image..[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
   
  [FONT=&amp]Question, where is GRUB?[/FONT]
  
  Any help is greatly appreciated.

---

### Post by kevdog on 2015-03-12
Which bootloader are you using?  I guess I'm really just confused about your setup.  Grub is usually installed under the /boot directory or /boot partition of the Ubuntu install, however I don't think you have to grub by default if you use another bootloader.  I'm not sure about your setup since the information you posted is a little vague or maybe I'm just not understanding everything.  When I do a dual Ubuntu/Windows boot, I use grub as the bootloader and then use the chainloader directive, however there are other ways of doing things.

---

### Post by numeric2 on 2015-03-12
> **kevdog said:**
> Which bootloader are you using? 

Thank you for your reply. 
Grub shows up when I first try and boot. It shows up even if there are no bootable Ubuntu devices. The Ubuntu drive is a removable USB 3 device, which indicates GRUB is installed somewhere on the main hard drive; the one with 6 partitions. The 6 partitions is the way Dell pre loads Windows on new computers. I suspect that GRUB is installed on the first sector of the main drive of partition 1. A text search however of partition 1, including sector 0, does not match with "GRUB" (case insensitive). 
Setting the BIOS UEFI to "Windows boot loader" first on the list will boot directly to Windows and not show GRUB. However, GRUB is still there and I want to totally eliminate it. I believe that a fresh start will enable a successful boot to Ubuntu. Currently, none of my Ubuntu drives, except for the install Ubuntu thumb drive, will boot to Ubuntu. They did work before, now they do not successfully boot.

---

### Post by dino99 on 2015-03-12
without grub you will loss ubuntu booting

---

### Post by grahammechanical on 2015-03-12
If you have Windows 8 pre-installed then you have a UEFI boot system and not the older (legacy) BIOS boot system. This is just something to keep in mind and it might explain why some actions that you have taken have failed to work. They may be intended for a BIOS boot system and not intended for a UEFI boot system.

Boot Repair will reinstall the Linux boot loader (Grub) on both BIOS and UEFI boot systems. It will default to installing Grub on all drives unless we tell it to do otherwuise. II think, but cannot be sure, that it will restore a Windows boot loader. You can check the Secure Linux web site to confirm this, if you want. Here is the issue as I see it.

When we install Ubuntu the default location for Grub is the first hard drive (sda) unless we change the location to another hard drive (sdb or sdc or sdd). I am guessing that Grub was installed into sda but you have Ubuntu on an external hard disk. You need to have Grub installed somewhere and the external hard drive (sdb?) is a suitable place. It is also my understanding that with a UEFI system references to Ubuntu are put into the UEFI record. That can be confusing when it comes to finding out where Grub is installed to and why it it is not being removed. We can remove Grub by overwritting it with another boot loader but that may not remove the references to Ubuntu from the UEFI sysyem.

It is my understanding that with a UEFI boot system and with both Windows 8 and Ubuntu installed in EFI mode that Grub bootloader files will go into a partition called EFI or something like that. But do not expect them to have "grub" in the file name. When we run Boor Repair it will produce a report and store a copy of that report in Pastbin and provide a URL to the report. If you post that URL in this thread we may be able to get a better understanding of your setup.

Please also clalrify what you are trying to achieve apart from the removal of Grub which would disable the loading of Ubuntu. Do you want to remove Ubuntu and only load Windows 8? Do you wish to only load Ubuntu when the external hard disk is connected? But to still load Windows 8 when the external hard disk is disconnected? Do you wish to choose to load either Windows 8 or Ubuntu by going into the UEFI setup and selcting which drive to load an OS from?

Regards.

---

### Post by oldfred on 2015-03-12
If you have an ubuntu folder in the efi partition on the Windows drive, you have to delete that first. But I would fully backup efi partition just in case.
And UEFI remembers boot entries in its NVRAM. And will add back entries if found in efi partition so you must have removed ubuntu entry first from efi partition.

 Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by numeric2 on 2015-03-12
> **grahammechanical said:**
> 

Please also clalrify what you are trying to achieve apart from the removal of Grub which would disable the loading of Ubuntu. Do you want to remove Ubuntu and only load Windows 8? Do you wish to only load Ubuntu when the external hard disk is connected? But to still load Windows 8 when the external hard disk is disconnected? Do you wish to choose to load either Windows 8 or Ubuntu by going into the UEFI setup and selcting which drive to load an OS from?

Regards.

Thank you for your reply.
The short answer is "yes".

Rational starting from day 1.

[LIST=1]
[*]Successfully installed Ubuntu on my external removable USB 3 1 TB hard drive.
[LIST=1]
[*]Grub ran without problems. 
[*]Ubuntu ran without errors. 
[/LIST]
  
[*]Tried to install Lazarus. Lazarus is a Delphi like IDE. I love Delphi!
[LIST=1]
[*]Ran into errors during install. 
[/LIST]
  
[*]Tried to install Ubuntu onto a 32 GB USB 3 Flash drive.
[LIST=1]
[*]Ubuntu installed without problems. 
[*]Reboot. 
[*]Ubuntu did not boot 
[/LIST]
  
[*]Installed again Ubuntu onto the external USB 3 hard drive.
[LIST=1]
[*]No problems with installation. 
[*]Reboot 
[*]Ubuntu did not boot. 
[/LIST]
  
[*]No installed Ubuntu device will boot to Ubuntu. 
[*] I want to remove GRUB
[LIST=1]
[*]Start over again. 
[*]Hope I can restore Ubuntu working on my computer as a removable USB 3 device.
[LIST=1]
[*]Want to boot to Windows if no Ubuntu device is present. 
[*]Want to boot to Ubuntu or Windows if either the
[LIST=1]
[*]External hard drive is present or 
[*]USB 3 flash drive is present. 
[/LIST]
  
[/LIST]
  
[/LIST]
  
[/LIST]

---

### Post by numeric2 on 2015-03-12
I will try your suggestions. Thank you for the links, they seem to address the issue.

---

### Post by oldfred on 2015-03-12
If an external drive, make sure you manually create an efi partition on that drive before install. Even though I told Ubuntu to install grub2's boot loader to sdb, it still overwrote my grub folder in sda's efi partition. I just then copied that folder to my sdb drive and had to reinstall grub on sda. (Should have backed up efi partition first). 

If your install is the same version of grub, the only real difference in the efi partition is another grub.cfg that has 3 lines in the ubuntu efi folder and is only a configfile entry to load the real grub.cfg in your install's /boot folder.

---

