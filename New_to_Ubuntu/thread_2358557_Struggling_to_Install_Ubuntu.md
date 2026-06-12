---
title: "Struggling to Install Ubuntu"
date: 2017-04-14
forum: New to Ubuntu
---

### Post by linuxfool2 on 2017-04-14
System Model:    HP EliteDesk 705 G2 SFF

The error message I receive is while installing GRUB, it says that it can't do that (install GRUB) on /dev/sda/ "This is a fatal error."

I have two hard drives, one being /dev/sda and it has Windows 10 on it. I am trying to install Ubuntu to the second drive but evidently GRUB needs to be on the first. Not sure really what the issue is or how to fix it. Is there any relevant information missing?

---

### Post by oldfred on 2017-04-14
Is Windows 10 installed in UEFI on gpt partitioned drive?

And then is sdb also gpt?

And are you installing Ubuntu in UEFI mode.
If trying to install in BIOS mode, sda would not have correct partition.

If Windows is UEFI and you boot Ubuntu installer in UEFI mode and add Boot-Repair it can convert install from BIOS to UEFI, but only if drive is gpt.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by linuxfool2 on 2017-04-17
Not quite sure what you're saying, but this seems to be the Boot-Repair URL: [http://paste2.org/VgeC67IV](http://paste2.org/VgeC67IV) 
Sorry but I'm a complete newbie to UEFI.

---

### Post by oldfred on 2017-04-17
You have created a mixed system.
You have UEFI on gpt partitioned drive on sda.
And you have MBR(msdos) partitioned drive on sdb.

Normally gpt is used for UEFI. And MBR for BIOS.
But you installed Ubuntu to sdb in UEFI boot mode. Becuase it saw & used the ESP - efi system partition on sda, it does work in UEFI mode even if on BIOS/MBR.

You also have some BIOS boot loader in sdb.

You may want to convert sdb to gpt, but probably do not have to.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

If you tried to reinstall grub2's boot loader in BIOS mode to sda, which is gpt for UEFI then you get an error that it cannot install grub as not configured for BIOS boot.

HPs are not UEFI dual boot friendly.
Many copy shimx64.efi to be /EFI/Boot/bootx64.efi which is a fallback or hard drive entry.

 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 

Older HP threads, users had to manually copy files.

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886
[/URL]
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)[URL="http://ubuntuforums.org/showthread.php?t=2131886"] 
[/URL] If you run Boot-Repair in will see all the .efi boot files that HP has and create a new grub menu file with lots of entries. You can edit or delete 25_custom.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

