---
title: "Ubuntu flash drive boot problem"
date: 2018-11-24
forum: New to Ubuntu
---

### Post by jayhalitzer on 2018-11-24
Hi everyone.  My name is Jay and I'm new to Linux.  I hope you can help with my problem.  I created a live Ubuntu 18.04 on a small flash drive and really enjoyed it.  However, I quickly became tired of not being able to save files or settings.  So I embarked on a new mission to create a full install on a newer and larger flash drive.  I was successful and everything was going fine until it froze, while doing a software update.  I had no choice but to power down manually.  When I tried to boot from the flash drive it brought me to a grub prompt and I was not sure what to do.  I initially thought the flash drive itself got corrupt but it seems that the original smaller flash drive also brings me to the same grub prompt.  The MS Windows 10 laptop that I use seems to boot up fine but I'm not sure why it's doing this.  I even tried another live flash drive that I made with Ubuntu Studio 18.10 and it still brings me to that grub screen prompt.  I would really appreciate it if someone could help me diagnose and fix this problem.  Thx -Jay

---

### Post by yancek on 2018-11-24
When you installed Ubuntu to the second flash drive, did you change the boot order in the BIOS to enable booting that flash drive?  Have you change the boot priority back to one of the other flash drives?
If you have windows 10 installed it is probably a UEFI install.  Did you install Ubuntu as a UEFI system on the flash drive?  Are you able to access the BIOS to make changes in boot priority?  What is the manufacturer of the computer?

---

### Post by jayhalitzer on 2018-11-24
Hi  Yancek,  

Thx for the quick response.  The original small live flash drive was made, using rufus ver.3.3, on my Windows 10, Toshiba Satellite 550 laptop. I set the boot order to boot from USB. I believe UEFI. The 2nd larger flash drive was made while in Ubuntu 18.04 environment, from the original smaller flash drive.  I did a full install, simply by installing it as Ext4 and boot to / (root). Everything seemed fine.  I booted to the drive and I was able to work within the system just fine, although it seemed very slow, compared to the live version on the original flash drive.  It was only when I was in the full install system and updating the Ubuntu software that the system froze and I began having the problem that all the flash drives with Ubuntu installed started to boot to a grub prompt and not boot all the way to the Ubuntu desktop.  Thx J

---

### Post by jayhalitzer on 2018-11-24
Hi again Yancek.  Since you mentioned booting into my Bios, I attempted it without the flash drives.  I was able to boot into my Bios. My boot order is still in the order I left it in.  Which is 1st boot to USB then 2nd to HDD.  Secure Boot is disabled and it is showing Boot type is UEFI.  However when I exit the Bios setup it does take me to a grub prompt screen but without the flash drives attached.  Is my Windows 10 possibly have a corrupt MBR?  What do you suggest I do to try and fix it?  Thx J

---

### Post by C.S.Cameron on 2018-11-24
Is there any possibility that when doing the Full install to USB, you might have put the bot loader on the small flash drive or on the internal disk?

---

### Post by oldfred on 2018-11-24
If you installed in UEFI boot mode, Ubuntu's version of grub only installs to the first drive it sees, usually sda and usually your internal drive. That will let you boot flash drive, if not otherwise corrupted by abnormal shutdown or other issues.
Flash drive will not boot as USB flash drive, but as another choice of hard drive in UEFI boot menu. But in UEFI it will only be ubuntu.

But if you want to directly boot a full install of Ubuntu on flash drive like you boot live installer, you must have an ESP - efi system partition on flash drive. You  can only have that if you partition in advance.
Also then UEFI only boots external devices from /EFI/Boot/bootx64.efi Installer for both Windows & Ubuntu uses that name with different files. 

My work around is to copy all of /EFI/ubuntu from ESP on sda, to ESP on sdb (or whatever external drive is) twice. Once to /EFI/ubuntu and once to /EFI/Boot. Then rename shimx64.efi to bootx64.efi. You have to have /EFI/ubuntu as shim/grub expect some files in that path.

---

### Post by jayhalitzer on 2018-11-25
I don't think the boot loader could have been installed on the small flash drive because I was able to boot into the larger flash drive and run the system fine, without the smaller flash drive being present.  I do believe that the boot loader was loaded on the large flash drive with the full install but I am getting a "grub" prompt, when I exit my Bios UEFI firmware, without either of the flash drives present.  I'm far from a computer tech but seems to suggest that when the system froze while updating the software on the larger flash drive, it affected my pc somehow and the boot loader.  Is there something that somebody suggests I try to test and diagnose or fix the problem.  Thx J

---

### Post by yancek on 2018-11-25
It would be necessary to get more detailed information on the system and the best way to do that would be by downloading and running the boot repair software from the link below.  You would need to select the 2nd option using the ppa and follow the instructions on the page.  You should select the option to Create BootInfo Summary and post the link you get when it finishes here at the forums.  Do NOT try to make repairs.  Obviously, you will need to boot one of your usb drives and I expect if the second drive crashed during your update, you would be best off going into your BIOS and setting the smaller usb to boot first.  Once you have done that, attache the other failed usb before running boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by C.S.Cameron on 2018-11-25
Sounds like you put the bootloader on the internal drive.
This is not a disaster if you can still boot windows.
If you need to reinstall Windows bootloader, use Windows tools such as a Windows startup disk.
If you wish to reinstall Ubuntu to your larger USB, use the "Something else" option when you get to partitioning.
Confirm that the location for bootloader installation is the larger USB and not a partition on it, ie sdx not sdxn.
If you now have grub on the internal drive, it might be a good time to make it dual boot Windows / Ubuntu.

---

### Post by jayhalitzer on 2018-11-26
Thank you very much for your response.  I believe I have fixed the boot grub problem by creating a windows media usb and from a dos command line fixed the mbr.  However, I thought it would be smart to format the large flash drive and backup important data from my internal drive, in case something went wrong.  Since everything went well, I have formatted the drive and would like to try, again, to do a full install on the large flash drive.  I would love to do what you described by booting directly from the flash drive like I do with the live installer, using the ESP -efi system but I have no idea how I would do that.  It's very frustrated not being able to load programs and save data, because the system won't use the rest of the space  and therefore doesn't allow it to load programs or even update the software.  Not to mention being able to save system hardware settings.  I appreciate any advice or help you could give.  Thx J

---

### Post by sudodus on 2018-11-26
You can try to do a full install on the large flash drive according to the following link with detailed instructions.

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

### Post by oldfred on 2018-11-26
I partition in advance with gparted.
This is one of my 64B flash drives:

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          411647   200.0 MiB   EF00  ESP
   2          411648          415743   2.0 MiB     8300  bios_grub
   3          415744        44652072   21.1 GiB    8300  bionicUSB
   4        44652544       120985599   36.4 GiB    8300  data
```

This is my actual use, but I do not install a lot of apps on flash drive. It is more for emergency boot and/or saving some data. (ESP can be a lot smaller.) 
```
/dev/sdd1       197M  6.9M  191M   4% /media/fred/ESP
/dev/sdd3        21G  3.7G   16G  19% /media/fred/bionicUSB
/dev/sdd4        36G   25G  9.3G  73% /media/fred/data


```

If you can disconnect drive as sudodus suggests that is best case. Many new UEFI systems let you turn off a drive in UEFI, so you do not have to open case to unplug it. Then Ubuntu's grub will install to ESP on flash drive. Otherwise you will have to copy files from internal drive's ESP which I normally do.

Be sure to boot in UEFI boot mode, not BIOS/CSM/Legacy. UEFI should offer both modes. How you boot install media is then how it installs.
Only use Something Else and select (change button) the partitions for ESP & / (root). ESP is FAT32 and / is ext4.

---

### Post by C.S.Cameron on 2018-11-26
Following makes a Full install Flash drive that works on both BIOS and UEFI:

[https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083577#1083577](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083577#1083577)

It is a grub 2 booter so you can also use it to boot ISO files or multiple full installs.

---

### Post by yancek on 2018-11-26
> because the system won't use the rest of the space  and therefore doesn't allow it to load programs or even update the software.

If the above comment is about your Ubuntu Live/installl medium, that is by design.  You could create a persistent usb but it would be much better to do an actual install to the usb.  

The link below to the Ubuntu documentation explains creating an EFI partition if you want it separately on your usb to which you want to install Ubuntu.  Just scroll down the page to Creating an EFI system partition.  Also, check out the info at the links posted by other members. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

