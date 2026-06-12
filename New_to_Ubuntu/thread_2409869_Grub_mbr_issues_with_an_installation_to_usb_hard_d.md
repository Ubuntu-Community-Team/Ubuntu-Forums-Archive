---
title: "Grub mbr issues with an installation to usb hard drive"
date: 2019-01-07
forum: New to Ubuntu
---

### Post by chagzuki on 2019-01-07
Around a year ago I wanted to try transitioning from Windows 10 to Ubuntu (I installed from a version 16 ISO and it may have then been updated to whatever was current at the time)... I knew that there’d be a learning curve in starting to use the command line but thought it would be worth persisting. I had it in mind to try dual booting on the same internal laptop hard drive but was persuaded that simply running a full installation of Ubuntu on an external usb drive would be cleaner. Prior to that I’d run Ubuntu in trial mode from flash drives. I watched a couple of YouTube tutorials on doing a full install to USB hard drive and it seemed fairly straightforward. But I must have specified that the boot information (I don’t particularly understand mbr and grub boot loader theory) be on the laptop’s internal unpartitioned hard drive as when I restarted the machine with the USB drive disconnected I still got the dual boot options (I can’t remember exactly what those options were but I’m fairly sure the Ubuntu option stated ‘grub loader’). Or maybe this happened automatically as a result of my laptop having the UEFI type of boot option selected during the Ubuntu installation.
I enabled the home folder encryption option in Ubuntu.
Recently I swapped my laptop hard drive temporarily to try to troubleshoot some performance issues, and in the process switched from UEFI booting to normal/non-UEFI. After returning things to how they were prior, I found I’d lost the grub loader dual boot options and could no longer boot from the USB drive. I tried following some tutorials on accessing the encrypted home folder from a Ubuntu iso boot disc but couldn’t get eCrypt terminal commands to work. Really I’d like to get the USB drive to be bootable again, but I don’t want to make any mistakes in trying to install the grub boot loader... I’m not a programmer and I can only really follow step by step guides. As far as I’m aware it should have been on the usb drive in he first place... but I don’t really mind where it is so long as I can get the drive to boot. Getting access to the encrypted home folder would be a second-best option, but quite acceptable. Any advice would be greatly appreciated.

---

### Post by oldfred on 2019-01-07
New systems, since Windows 8 five years ago are UEFI with gpt partitioning.
The 35 year old BIOS with MBR partitioning is available for backwards compatibility, but UEFI & BIOS boot modes are not compatible.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Generally best to have all installs in same boot mode, but UEFI install to external drive is a bit more complex.
And BIOS install to external drive requires you to use Something Else install option and select that drive as location of grub installer. 

That selection in UEFI mode, is there but does not work. UEFI Grub only installs to ESP - efi system partition on first drive seen, normally Windows drive as sda. If only booting external drive from that one system, that will work. But if you try to boot another system, it has no boot files on it.

New versions of Ubuntu do not support encrypted /home, just full drive encryption using LVM an advanced volume management system.

Lets see where you are at now, make sure external drive(s) are plugged in.
      
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by chagzuki on 2019-01-13
Thanks for your help. I&#8217;ve been somewhat distracted with other things and I&#8217;m taking my time to digest the concepts mentioned in your reply, but I&#8217;ll get onto this shortly.

---

### Post by chagzuki on 2019-01-16
OK, if I've understood the advice correctly this is the link, though it looks like a complete report rather than a summary(?). I should add that the live CD was a USB flash drive, so there are two external USB drives plugged in.

[http://paste.ubuntu.com/p/ztnkzrzVpV/](http://paste.ubuntu.com/p/ztnkzrzVpV/)

---

### Post by oldfred on 2019-01-16
Report suggests you turn off UEFI Secure Boot.
It also says meta-data in NTFS partition. That means Windows fast start up is on. Windows will keep turning that on with major updates & main turn UEFI Secure Boot back on, also.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Your external drive, sdc does not have an ESP. As long as you want to boot from ESP on internal drive that will work.
But UEFI usually forgets boot entries when you unplug a drive.
You do show this, does it boot, since using grub Secure Boot has to be off.
        
>  Boot0001* HDD: 	HD(2,GPT,f220a113-6dab-416f-a384-0758ae234928,0xc8808,0x96008)/File(EFIubuntu[COLOR=#ff0000]grubx64.efi[/COLOR])RC 

    With UEFI Secure boot off, does the HDD entry work?

Ubuntu's UEFI install only installs grub to first drive's ESP. Which normally works. But I prefer to have boot files on same drive.
But the only way to do that is to manually partition in advance to have an ESP on second drive, and copy files and use efibootmgr or reinstall grub.

Also external drives are normally booted from UEFI with /EFI/Boot/bootx64.efi. Grub used to not even create that file, but now does, but only on internal drive as fallback boot entry. We used to just copy shimx64.efi or grubx64.efi to /EFI/Boot on external drives. But also had to copy all of /EFI/ubuntu as that configuration of grub or shim looks for more boot files on /EFI/ubuntu.
 
If you ever want to boot external drive from another UEFI system, you need to add an ESP, you could shrink swap by 300MB and make a new ESP - efi system partition FAT32 with boot flag and copy files as above.

---

### Post by chagzuki on 2019-01-19
Are UEFI and &#8216;secure boot&#8217; synonymous? If I disable UEFI and switch to &#8216;legacy&#8217; in the bios and try to boot I get told that there&#8217;s no boot filename received and no bootable device.

---

### Post by yancek on 2019-01-19
> Are UEFI and ‘secure boot’ synonymous?

No.  Secure Boot is a very minor part of UEFI.  If you have a Legacy install of Ubuntu or any other Linux, the Grub bootloader will not boot a windows EFI install.  If you are still having problems, you should answer all the questions asked above.

---

### Post by chagzuki on 2019-01-19
I ask because in my Bios I have just the two options, UEFI with secure boot, and legacy. I don't appear to be able to turn off secure boot whilst staying in UEFI mode.

---

### Post by chagzuki on 2019-01-20
I'm thinking it's probably easiest to reinstall grub on the internal hard drive, which as far as I understand is what the automatic repair would do. So as in the summary report:

"The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sdc2, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file"

am I right in interpreting this to mean that it will write instructions on the internal hard drive re-establishing the link to the external usb drive, without altering any data on the external drive?

---

### Post by oldfred on 2019-01-20
Most systems have a UEFI setting & Secure boot setting. A lot of those use "Windows" and "Other" as the Secure boot on/off setting. Since they manual will say to use "Other" with Windows 7. Windows 7 does not support UEFI Secure Boot.
Some systems do seem to just have settings as you describe, but then somewhere or somehow you can still boot in UEFI mode with Secure Boot off. Microsoft has required vendors to let users turn off Secure Boot. (Some large customers want to install Windows 7.)

You always should have a good backup of system. 
Then if you make a mistake on selecting where to write data, it is not the end of the world.
Boot-Repair normally works, but sometimes you need to use Advanced mode to correctly repair some systems.

---

### Post by chagzuki on 2019-01-26
So, I realized I needed to set an administrator password in the bios and  then I had access to the option to switch secure boot off, and that  indeed made it possible to boot from the USB drive. I've not decided  what my next step is, i.e. whether I'd like to try to make the drive  bootable on any computer, but the important immediate issue is that I  have access to the contents of the home folder. Thanks for your help.

---

### Post by oldrocker99 on 2019-01-28
I always use the legacy boot, since my own experience is that grub will not install during system installation, leaving an unbootable brick. If I don't use UEFI, the installation is perfect.

---

