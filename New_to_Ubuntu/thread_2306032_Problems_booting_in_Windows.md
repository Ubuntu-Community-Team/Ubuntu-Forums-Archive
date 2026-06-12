---
title: "Problems booting in Windows"
date: 2015-12-11
forum: New to Ubuntu
---

### Post by Vighnesh on 2015-12-11
Hey,


 I am a Windows 8.1 user, and I wanted to install Ubuntu in  my laptop as it is a popular OS in our university. I used the YUMI (Your  Universal Multiboot Integrator) app from[ www.pendrivelinux.com]("http://www.pendrivelinux.com")  to create a live usb with the .iso file downloaded from the official  ubuntu website. I did not allocate space for persistent data, if that  may have been a problem.


 I went ahead with my plan and all was well till step 4,  where I chose "something else" (image shown below) as I wanted to create  partitions for dual booting. Strangely, it did not display anything  about Windows 8.1 or how much memory the latter was using up. My laptop  is a HP Pavilion 15 with 750 GB HDD. In the ubuntu partition page  however, they displayed the entire 750.2 GB as free space,without displaying the allocated partition for windows (Image shown  below)


 Now I had used Disk Management in windows, prior to this  installation, to reduce the partition size of windows. Although it  initially showed 698 GB total memory available, I shrunk the windows  partitions to approximately 300 GB (200 GB for C: and 100 GB for D: )  After reading a lot of forums, I created partitions in the ubuntu  installer accordingly for /, /home, /boot, /var, /tmp, swap etc.


 I also created a /windows partition of 300 GB, assuming it  would fit in windows, and by now, the available space was just 114 GB in  the ubuntu partition page. I proceeded with the installation and  completed it. My Ubuntu was just perfect with no visible bugs. But when i  tried to reboot, it automatically booted to Ubuntu. I tried boot  repair, uninstalled GRUB, reinstalled it, yet the only change was a  proper menu of available OSs showing just Ubuntu.


 My paste bin link was:
 [URL="http://paste.ubuntu.com/13930930/"]http://paste.ubuntu.com/13930930/

[/URL]

 I cannot boot into Windows, nor can I see it in my list of  OSs. This is a major problem as I have various useful pre installed  packages in Windows. I would be very obliged if you could help me  urgently. I have attached all possible information, please feel free to  contact me if you require more.
 With warm regards,


 Vighnesh
( [email]vighneshck@gmail.com[/email] )

---

### Post by Bucky Ball on 2015-12-11
Welcome. The bad news is no more Windows. Fingers crossed you have a backup:

```
Partition    Start Sector    End Sector  # of Sectors System
/dev/sda2     585,936,896   617,187,327    31,250,432 Swap partition (Linux)
/dev/sda3     617,187,328   812,498,943   195,311,616 Data partition (Linux)
/dev/sda4     812,498,944 1,203,124,223   390,625,280 Data partition (Linux)
/dev/sda5   1,203,124,224 1,204,099,071       974,848 Data partition (Linux)
/dev/sda6   1,204,099,072 1,223,630,847    19,531,776 Data partition (Linux)
/dev/sda7   1,223,630,848 1,243,162,623    19,531,776 Data partition (Linux)
/dev/sda8   1,243,162,624 1,243,164,671         2,048 BIOS Boot partition
```

That is what you have on your hard drive, sda. Not a Windows partition in sight unfortunately. 

I have a feeling Windows was installed in UEFI and you've installed Ubuntu in GPT and wiped Windows somehow. There are a number of steps you need to perform prior to installing dual-boot with Windows in UEFI. To start, you need to boot into Windows and switch off hibernate. That is why you couldn't see the Win partition at the partitioning section during 'Something Else'. 

PS: You essentially only need two partitions with the mountpoints / and /swap (which are defaults you can set in 'Something Else'). You really don't need all the others. Lots of people use /home (in which case your / partition only needs to be around 20-25Gb and /home large as that's where your personal data goes) but it is a little redundant if you want to share data with Windows (it can't read/write to Linux filesystems). In this case you would create an NTFS shared partition and link to the folders in there from the /home directory in / . 

There are variations, but that's the basics. /swap need only be 2Gb unless you intend to hibernate and generally comes after / .

PPS: No, not adding persistence to the USB had nothing to do with this.

---

### Post by LostFarmer on 2015-12-11
```
Number  Start  End    Size    File system     Name  Flags
2      300GB  316GB  16.0GB  linux-swap(v1)
3      316GB  416GB  100GB   ext4
4      416GB  616GB  200GB   ext4
5      616GB  616GB  499MB   ext4
6      616GB  626GB  10.0GB  ext4
7      626GB  636GB  10.0GB  ext4
8      636GB  637GB  1049kB                        bios_grub
```  as shown your first partition starts 300gb into the disk.  It is possible the Windows partitions are still in good condition but for some reason the information was removed from the EFI partition table.

try linux version of program "testdisk" to recover the partitions.  Not sure if it is installed in Ubunut or not.  Open a terminal and type and enter " testdisk", it will run or I think it will tell you how to install.  Do a web search on how to use testdisk.

After the recovery of the windows partition (NOT BEFORE) , you need to get your linux booting in EFI mode, it is currently in MBR/Legacy mode (bios_grub partition).

---

### Post by Bucky Ball on 2015-12-11
> **LostFarmer said:**
> ```
Number  Start  End    Size    File system     Name  Flags
2      300GB  316GB  16.0GB  linux-swap(v1)
3      316GB  416GB  100GB   ext4
4      416GB  616GB  200GB   ext4
5      616GB  616GB  499MB   ext4
6      616GB  626GB  10.0GB  ext4
7      626GB  636GB  10.0GB  ext4
8      636GB  637GB  1049kB                        bios_grub
```  as shown your first partition starts 300gb into the disk.  It is possible the Windows partitions are still in good condition but for some reason the information was removed from the EFI partition table.

try linux version of program "testdisk" to recover the partitions.  Not sure if it is installed in Ubunut or not.  Open a terminal and type and enter " testdisk", it will run or I think it will tell you how to install.  Do a web search on how to use testdisk.

After the recovery of the windows partition (NOT BEFORE) , you need to get your linux booting in EFI mode, it is currently in MBR/Legacy mode (bios_grub partition).

Good find. Perhaps better to start again and do it the correct way for a UEFI install. If you boot from live media and open Gparted do you see all partitions then? If the Windows partition is still there (in 'good condition') on the hidden 300Gb there is no need for testdisk. The partition is already there and intact. Perhaps set to getting Windows to boot (I would delete the Ubuntu partitions and reinstall the correct UEFI way once you have Windows booting, probably by using the Windows recovery disk should fix and you will also find guides online).

---

### Post by Vighnesh on 2015-12-12
Hi,

Thanks a lot for your reply. I overlooked the fact that Windows 8 uses UEFI. I shall take care next time. Just to clarify, but the ubuntu installer asked me to set aside 1 mb for bios grub. Is that mandatory?
Moreover, how important is the installation of GParted in this entire process?

Thanks,

Vighnesh

---

### Post by LostFarmer on 2015-12-12
the ' bios_grub' partition is need only when linux is being installed in legacy/mbr mode on a GPT disk.  If you are installed on GPT disk in EFI mode the installer will not ask for the bios-grub partition, it will ask for a EFI partition if it does not find one.

I would not reinstall or change linux till the lost Windows partitions is recovered.  Some how your Windows partitions were deleted from the partition table and it is not due to linux being installed in legacy mode. 

testdisk might not work.  I did get to test program on a GPT disk to recover partitions after zeroing the partition tables , it did not work to good.

---

### Post by Bucky Ball on 2015-12-12
Gparted doesn't come into this. Where would you install it? It is included by default on the live session on the install media (not on the installed version) if you need to use it. Use the partitioner during the install by choosing 'Something Else'. Or is that what you mean?

---

