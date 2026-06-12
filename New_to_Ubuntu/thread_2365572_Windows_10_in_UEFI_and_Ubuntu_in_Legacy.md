---
title: "Windows 10 in UEFI and Ubuntu in Legacy?"
date: 2017-07-07
forum: New to Ubuntu
---

### Post by domino552 on 2017-07-07
I want to dual boot ubuntu and windows 10. I was able to install and start using Ubuntu successfully. I can also boot into Windows if I press the F12 key at startup. However, Windows 10 is not a listed option in the grub menu (other than Windows Boot Manager Recovery which I don't think is what I want since it wants my encryption key for recovery). From what I've read it seems most common to have Windows10 available as an option for Grub. 

From doing a bit of research, I thought I was not seeing Windows10 because it's using UEFI mode and Ubuntu is in legacy. See: [https://askubuntu.com/questions/822759/no-windows-10-option-in-grub](https://askubuntu.com/questions/822759/no-windows-10-option-in-grub)

If I run [COLOR=#333333][FONT=Ubuntu][ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode" I see UEFI mode though. 

Are there any other possible issues I should check? 
[/FONT][/COLOR]
Thanks in advance for your help!

-------
Here are other steps that I've taken to try and resolve this: 
[LIST=1]
[*]updated grub and restarted
[*]ran the boot-repair utility
[*]double-checked to make sure partitions were healthy with gparted (screenshot attached).
[/LIST]

---

### Post by RobGoss on 2017-07-07
Hello and welcome to the forums,

> From doing a bit of research, I thought I was not seeing Windows10 because it's using UEFI mode and Ubuntu is in legacy

This clearly shows me that  you have not installed Ubuntu correctly, If you want your system to boot normally using the Grub menu then you'll need to install Ubuntu in the same mode as Windows UEFI. What version of Ubuntu do you have installed?

You may need to make some adjustments to the Ubuntu partition and reinstall Ubuntu in UEFI mode, this should solve the boot problem you're having because you have Ubuntu installed in Legacy mode

You can delete the Ubuntu partition and ether reclaim the disk space or use the **unallocated **space to reinstall Ubuntu again. Windows has a good partitioning tools that will help you achieve this

---

### Post by domino552 on 2017-07-07
Thanks for the reply and welcome. 

Yes, I thought that was the issue but if I run: 
[COLOR=#000000]If I run [/COLOR][COLOR=#333333][FONT=Ubuntu][ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode" I see UEFI mode though. 
[/FONT][/COLOR]
So I don't think that is the issue. Perhaps could be an issue with Windows partition being encrypted by default? This was an installation on a brand new computer.

---

### Post by RobGoss on 2017-07-07
I don't know much about having partitions encrypted so I'm not gonna be much help there, But I do know it you what your system to dual boot correctly you need both OS's to be install in UEFI. I had one of my installations installed as you do and each time I wanted to boot in to Windows I would have to access the BIOS and change the boot order...

---

### Post by yancek on 2017-07-07
If you have installed Ubuntu UEFI, you should be able to mount the first partition (FAT32 format) and access it in a file manager to see whether you have an ubuntu directory there.  If windows is installed UEFI, you should see a Microsoft directory there.  For more detailed information, you can download and run boot repair on Ubuntu and select the option to Create BootInfo Summary and post a link to the output given when boot repair finishes.  That should give more info that would help others to help you.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could also post the output of:  sudo efibootmgr here as that would give some info on your boot options in UEFI.

---

### Post by domino552 on 2017-07-07
Below is the boot order- on a high-level everything seems to make sense to me. I'm able to mount the Win directory and browse contents too. The grub listing looks a little bit different than what I've seen in some of the other set-up guides which is the main point of confusion for me. I disabled the default encryption and now it directly loads Windows so I guess I'm good to go? 

```
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000,0017,0018,0019,001A,001B,001C,001D,001E,0023
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0010  Setup
Boot0011  Boot Menu
Boot0012  Diagnostic Splash Screen
Boot0013  Lenovo Diagnostics
Boot0014  Startup Interrupt Menu
Boot0015  Rescue and Recovery
Boot0016  MEBx Hot Key
Boot0017* USB CD
Boot0018* USB FDD
Boot0019* NVMe0
Boot001A* ATA HDD0
Boot001B* USB HDD
Boot001C* PCI LAN
Boot001D  Other CD
Boot001E  Other HDD
Boot001F* IDER BOOT CDROM
Boot0020* IDER BOOT Floppy
Boot0021* ATA HDD
Boot0022* ATAPI CD
Boot0023* PCI LAN
```

---

