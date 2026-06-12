---
title: "GRUB in usb pen drive"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-06-28
Is it possible to install Ubuntu along with other OS in the HDD but install GRUB on a USB pen drive instead of HDD ?
If so how do we do that ? If possible then can i transfer my existing GRUB to a pen drive ?

---

### Post by oldfred on 2013-06-28
Yes, several ways.

If you have an Ubuntu install, just boot into it and install from a working system to another drives MBR.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

You can install just grub to a flash drive MBR with grub files in a partition on the flash drive. But since it does not have the rest of grub files, you have to manually create and maintain your grub.cfg. 
      
 Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
Label partition if grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)
Reported to have a few typos? But shows process on one page
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

---

### Post by 3dmatrix on 2013-06-28
Thanx !

[COLOR="#FF0000"]sudo fdisk -l
#if it's "/dev/sdb" then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub[/COLOR]

In the above commands, sdb is the usb drive ?
Do i need to remove grub from my hdd also ? If so how do i do that ?

After installing, when i boot, what happens if the usb pen drive is attached and when it is not attached ?

---

### Post by oldfred on 2013-06-28
If you set BIOS to boot flash drive first, then it will boot that. If not plugged in BIOS skips flash drive and boots hard drive.
What other systems do you have on hard drive? You can install Windows or a different grub to the MBR of the internal drive.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

You can also use Boot-Repair but it often just defaults to installing grub to all drives. You want to use advanced options and choose what to install where.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by 3dmatrix on 2013-06-28
I have Ubuntu 12.04 , Ubuntu 13.04 and windows. I wish to remove grub from my hdd so that windows boots by default.
When i attach my pen drive (BIOS is set to boot from it) then it should give me options to boot in to other OSs.
Is it possible to that ?

---

### Post by oldfred on 2013-06-28
If you put a Windows boot loader that is how it will work. The MBR on the flash drive is the MBR the Ubuntu install uses to boot from. You can install the grub from either 12.04 or 13.04, but whichever you install will be first. It will still use the grub menu from your install.
BIOS boot order of devices is important.

You can install a Windows type boot loader from Ubuntu, but you really should have a Windows repair CD or flash drive for the current version of Windows. 

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

If you want an actual Windows boot loader make the Windows repairCd and use it to fix the MBR.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by 3dmatrix on 2013-06-29
Thanx ! I will give it a try and get back  :)

---

### Post by 3dmatrix on 2013-06-29
Its working fine till now. Can you kindly tell me how can i keep the GRUB in pen drive updated ?
I hope grub.cfg changes with ubuntu updates.

---

### Post by oldfred on 2013-06-29
Grub2's boot loader in the MBR, will not change often. Only on a major update to grub itself. Since you will be booting with flash installed just do not remove it when running updates.

Of course with every new kernel or some other changes a sudo update-grub or dpkg equivalent will be run, but that just updates menu which is still inside your Ubuntu in /boot/grub folder.

I do a bit different install of grub to my flash drives where I have a fully bootable grub in the flash drive. But I still have to manually maintain menu as flash drive does not have the rest of grub that is in various places in Ubuntu like os-prober and the configuration file. But then I can directly boot other ISO on flash drive as repair tools or to install another version.

---

### Post by 3dmatrix on 2013-06-30
So if i wish to update GRUB in the pen drive then what command do i need to enter ?
Or does Ubuntu knows where my GRUB is and can automatically update it when ever it passes a grub update command ?

---

### Post by oldfred on 2013-06-30
Grub knows, but since it now is a removeable device you need to have it plugged in.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by 3dmatrix on 2013-07-01
Thats good thanx  :)

---

