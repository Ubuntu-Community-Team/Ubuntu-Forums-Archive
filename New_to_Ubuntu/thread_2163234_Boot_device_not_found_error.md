---
title: "Boot device not found error"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by thecjkid on 2013-07-17
Hello, I am a first time Linux user and after trying out ubuntu via the bootcd I decided to take the full plunge, installing it andd wiping out windows 8.  The installation process went fine but on restart the computer can not locate the OS.  When I tried to reinstall the disc was able to detect that I already had Ubuntu installed. Any advice? Thanks in advance!

---

### Post by oldfred on 2013-07-17
Did you turn fast boot off?
Are you booting with secure boot on or off. May be better off. Or you have to boot in secure boot mode and install the Microsoft signed version of grub and kernels from Ubuntu.

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

### Post by thecjkid on 2013-07-17
I am out of fast boot, I keep getting terminal errors when I try to install boot-repair.

---

### Post by oldfred on 2013-07-17
Copy & paste command from the link into your terminal. Even spaces may be important.
You do need Internet connection for it to work. Best to have hard wired Ethernet connection.

---

### Post by thecjkid on 2013-07-17
[http://paste.ubuntu.com/5885399/](http://paste.ubuntu.com/5885399/)  This is the link i got, or do you want me to paste the whole log?

---

### Post by oldfred on 2013-07-17
Link is better.

You show an efi partition, but Boot-Repair does not see it. Did you boot in BIOS/CSM/Legacy mode to run Boot-Repair. The request for a bios_grub partition is if you want to always boot in BIOS mode not UEFI.

I would try to run the suggested repairs and see what Boot-Repair comes back with. You do not have grub installed in either UEFI or BIOS boot mode, so you need something. 

Some systems have a locked efi partition which can cause issues. 
       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

      
 Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

I also prefer to create a smaller / (root) partition and use rest of drive as /home or as data partition(s). But that is not an auto install option and you have to use Something Else or manual install, to size, format and choose which partition is which.

---

