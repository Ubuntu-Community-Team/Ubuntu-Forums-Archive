---
title: "installer claims i dont have enough space when i do"
date: 2017-09-30
forum: New to Ubuntu
---

### Post by tovelw on 2017-09-30
Hi there!
I am trying to install Ubuntu Studio, from windows 10, being completely new to Linux. Must have done something terribly wrong, booting from a usb worked fine but then the installer says i need 8.6 gb, it says i only have 8 while its a new computer, so I for sure have about 475gb diskspace and 16gb RAM... Also just the tryout version without installing looks really old and primitive, no apps or nothing... What happened? 
I am super thankful for all help.

- Tove

---

### Post by ajgreeny on 2017-09-30
Tell us more about the "install Ubuntu Studio from Windows 10" as you can not install Ubuntu from any Windows OS now.

It used to be possible to test Ubuntu versions that way using WUBI but that method has not been supported for some time now and will certainly not work with UEFI at all; if your Windows 10 came preinstalled on the machine it will be UEFI.

You need to either burn a DVD disk image of the .iso file you have
[https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows)
or copy as an image it to a USB
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)
then boot the computer to the DVD or USB and install Ubuntu from the icon that will appear on the desktop of that live system.

---

### Post by Impavidus on 2017-09-30
Do you wish to replace Windows with Ubuntu or do you wish to install them side by side? That can be done, although because of changes in recent years (mostly in Windows) it's not as easy or reliable as it used to be. Or you can use a virtual machine.

To install Ubuntu you need unallocated space on your hard drive. You may have a lot of space on your hard drive that isn't used for files, but it's already allocated to a file system, that is, the C or D partition (or drive, as Windows calls them). Use Windows tools to shrink some partitions to make unallocated space on the drive.

If I'm not mistaken, Ubuntu Studio uses the xfce desktop manager. It's highly configurable, so you may be able to give it a more modern look, for any definition of modern. I assume you try release 16.04 LTS or 17.04.

---

### Post by ian-weisser on 2017-09-30
> **tovelw said:**
> then the installer says i need 8.6 gb, it says i only have 8 while its a new computer, so I for sure have about 475gb diskspace

You did not partition your disk correctly,

Or (if your are trying to dual boot) you selected the wrong partition.

---

### Post by tovelw on 2017-10-01
Thank You plenty for the answer! 
I did the partition only using the control panel on windows, though this problem actually went away first when I switched to a bigger USB pendrive...
Now I have another issue tho, I cannot complete the installation because 'No root system is defined. Please correct from partitioning menu.' But the menu is completely empty I cannot change option... The 'device for boot loader installation' is marked /dev/sda and thats the only option, but its not acceptable... hmm
Super happy for any help, cheers!

---

### Post by ian-weisser on 2017-10-01
Use Windows to fiddle with Windows partitions.
Use Linux to fiddle with Linux partitions.

Windows deliberately makes dual-booting hard: Windows tools are deliberately unhelpful, and Microsoft deliberately makes it hard for Linux tools to work in the Windows environment.

Use the Live (not installed) environment to install and run GParted, an appropriate Linux partitioning tool.
Verify which partitions house Windows and which partitions you have created to run Linux. You may (or may not) need to create the new Linux partition. Note the names of each partition (write them down, you need them later)
Then run the Linux installer.

Pro Tip: While in the Live environment, always record your Windows Product Key onto paper, in case something very unexpected happens and you need to reinstall Windows.

---

### Post by HermanAB on 2017-10-01
Old Pro Tip: Data that isn't backed up, doesn't really exist.

So, before you mess up more, backup your data on your Windows machine, before it disappears in a puff of logic.

---

### Post by oldfred on 2017-10-01
When using the Something Else install option (which is better if you understand partitions are not necessarily Windows "drives") then at the minimum you must have a / (root) partition. If partition already exists, you choose it (change button) specify ext4 & / . 
Default install is / & swap. But from 17.04 on, it will use a swap partition if one exists, but default is a swap file, not a partition.
You can add other partitions, many users have either /home which you can create during install, or later add a /mnt/data partition either ext4 for Linux only or NTFS for both Linux & Windows (if Windows fast start up is off).

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 UEFI install  Windows 10
[https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi)

More info in link in my signature. [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by tovelw on 2017-10-02
How do I go about installing the GParted? The Ubuntu Sdtudio live doesnt have a browser, i downloaded the gparted iso in another computer and just copied to another usb and then copied to the live environment but its just showing up as a lot of files i dont really know what to do with... I have to burn them onto something somehow right? But burning the gparted iso to a usb and boot it did not work...

---

### Post by oldfred on 2017-10-02
You install ISO to flash drive using tools that format flash drive, extract ISO and add a boot loader.
Process should be the same with all ISOs.

If system came with Window 10 then it is UEFI and you want to install Ubuntu in UEFI mode.
See links & info in link in my signature on UEFI install details.

If the Studio flavor does not have gparted, you can easily boot Studio in live mode and add gparted, if using terminal:
sudo apt install gparted

---

### Post by tovelw on 2017-10-02
Ok so now Ive started GParted in the usb live version of Ubuntu Studio, but the only thing showing up in the field of GParted is the usb-stick... I cant find the drive at all in the live session...

---

### Post by oldfred on 2017-10-02
Did you turn off Windows fast start up?
The Linux NTFS driver will not mount hibernated NTFS partitions read/write if hibernated & Windows fast start is just always on hibernation.
Details in link in my signature.

What brand/model system?
What video card/chip?

---

### Post by tovelw on 2017-10-02
Aha, no I will try to do that... Its a Dell XPS 13 9360... Also, should I write the usb disc in ntfs or fat32? Because now Ive had it in fat32, im also switching from uefi & bios to just GPT UEFI...

---

### Post by ajgreeny on 2017-10-02
Fat32 is fine and I think it is needed for a live USB, so don't worry about that.

Just turn off fast start in Windows then make sure it is fully shut down, not hibernated or suspended then boot to the USB live system and try again.

---

### Post by oldfred on 2017-10-02
Dell needs AHCI mode for drives, often is RAID or Intel SRT which looks like RAID.
I have seen where Dell needs Legacy/CSM/BIOS mode on, even when booting in UEFI. Everyone else with Legacy mode only boot in Legacy mode.
Many have needs both UEFI/BIOS updates and firmware updates for SSDs.

Similar models of Dell.
 Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444) 

        Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)

---

### Post by tovelw on 2017-10-04
Hey again guys! I followed the advice in some of the links and I have succeeded in installing my Ubuntu Studio! Thank You heaps for all help.
There is only one minor query now, i cant seem to switch in between windows and ubuntu without first changing the SATA in between Raid and AHCl, will it always be like this or is there something I'm doing incorrectly?

---

### Post by ian-weisser on 2017-10-04
> **tovelw said:**
>  changing the SATA in between Raid and AHCl

Which works with which?
Did you intend to use hardware RAID for one of your installations?

---

### Post by oldfred on 2017-10-04
Dell for some reason uses RAID mode even when only one drive.
But if RAID 0 and two drives, you can totally break your Windows install.

I would fully backup Windows if you have not already. And make sure a full backup not  just one that wants to run from a recovery partition.

You need to install the AHCI drivers into Windows.
Either when booted into it, from turning RAID on, or boot and get into recovery mode and add driver.

 XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 

 [https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)

---

### Post by tovelw on 2017-10-04
Wow...doesnt sound very good then... So is the backup i made with the usb not enough?

---

### Post by tovelw on 2017-10-04
No, I tried the Sam Nicholls thing and now i cant boot into windows at all...

---

### Post by oldfred on 2017-10-06
Did you also turn off UEFI fast start up. That assumes no changes to  configuration which then causes issues when reconfiguring system.

Does your Windows repair or install disks recovery mode not work?
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

