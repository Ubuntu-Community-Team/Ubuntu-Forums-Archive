---
title: "External HDD with Ubuntu boots in emergency mode"
date: 2023-03-01
forum: New to Ubuntu
---

### Post by lovedlx on 2023-03-01
I recently installed Ubuntu on my 500GB external HDD with my Acer  Aspire laptop from a live USB, the installation was successful (even  installed grub on the external HDD) and I could boot from the external  HDD with my Acer laptop. The problem is that that laptop only used as  installation media and my goal was to use the external hard drive with  Ubuntu installed on my main laptop which is an HP Envy, but when I turn  on the laptop with the hard drive attached it boots normal at first even  crashes see the logo of HP and Ubuntu while loading, but then emergency  mode appears on the screen with the following


 Emergency mode boot:
[IMG]https://i.stack.imgur.com/DjuXm.jpg[/IMG] 

Results of ```
journalctl -xb | grep failed
``` :

[IMG]https://i.stack.imgur.com/BQdhh.jpg[/IMG]

The Acer laptop I use as installation media  has an Intel Pentium Silver CPU and graphics is the one integrated into  the CPU and my main HP laptop has an AMD Ryzen 7 CPU with Radeon Vega  Graphics

I don't know why Ubuntu starts on my Acer laptop and not on my HP laptop.

---

### Post by yancek on 2023-03-01
The errors reported "failed for /boot/efi" and  "filesystem check on UUID  9452-EB6A" failed would indicate that you did an EFI install on the Acer which put the EFI files on the internal EFI partition of the Acer.  This is by design by the Canonical (Ubuntu) developers, installing to the first EFI partition it finds.  If you did create an EFI partition on the external drive, you may be able to copy the Ubuntu EFI files from the Acer EFI partition to the external drive.  

Did you do an EFI install on the external drive of Grub?  If so, did you then change the boot priority in the BIOS to the external drive?
Is there any reason why you did the install on the Acer when you wanted to use the external on the HP?  Can you use the Ubuntu install USB on the HP to get partition info with the command:  sudo fdisk -l  This will list partitions so you can see if you have an EFI partition on the external drive.

What OS do you have (if any) on the HP?

If you have EFI files on the EFI partition for ubuntu on the Acer and copy those files to the EFI partition on the External it might work.  If this doesn't help, try going to the site below while using the Ubuntu USB installert and downloading and running boot repair from it, using the 2nd option described on the page to use the PPA.  Do this on the HP and then run the Create BootInfo summary option which will give you a link when it finishes and you can post that link here so members can view it and give suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lovedlx on 2023-03-01
Answering the questions I can say that:
-Yes, I did the EFI installation on the external hard drive
-In the BIOS of both laptops, the external disk is prioritized
-I did the installation with the Acer laptop since according to the tutorial that said that when installing ubuntu on the external disk the windows EFI file would be damaged but it could be recovered and since my HP laptop has all my important files I wanted to be cautious and better to do it on the laptop because it did not have important files
-HP laptop has Windows 10 as single operating system and Acer laptop has dual boot with Windows 10 and Ubuntu on a small 25GB partition

and to do the sudo fdisk -l command, does it have to be on the HP laptop with an installation USB or can I do it from the Acer laptop that already has Ubuntu installed?

---

### Post by oldfred on 2023-03-01
What site said installing Ubuntu damages Windows? That is wrong. 
Users can select install options like totally erase drive with Windows which would damage Windows. Or a full drive (where drive is entire drive, not a partition) will also erase Windows.

External or any second drive install has this bug on installer.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Edit, often Boot-Repair report shows many details, but if trying to boot from two different systems, not sure what a report would show.
May be best to run report from system you used to create external drive.

---

### Post by lovedlx on 2023-03-01
After all from my Acer laptop I booted Ubuntu on the external hard drive and used Boot Repair and it worked as I installed the necessary files so I can boot Ubuntu on the external hard drive from any PC
I'm actually typing this from Ubuntu on my HP laptop with the external hard drive
So I was able to fix this and I will mark this thread as solved

---

### Post by yancek on 2023-03-02
>  I did the installation with the Acer laptop since according to the  tutorial that said that when installing ubuntu on the external disk the  windows EFI file would be damaged 

THat is incorrect as pointed out above.  If you mount your EFI partition, you should see a Microsoft directory in addition to an ubuntu directory.  Each OS puts its boot files in these separate directories and neither is damaged.  When each system is installed, it may set itself to first boot priority in the BIOS firmware and that would need to be changed.  Best to avoid that site if they are posting inacurrate information.

---

