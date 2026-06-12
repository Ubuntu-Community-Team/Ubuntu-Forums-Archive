---
title: "Win7 boot manager lost ! ... Please help!"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mrbaloob on 2012-03-03
Hello everybody,
I've updated recently to Usuntu 11.10. I really can't remember what i did wrong but it messed up the boot slightly. I lost Win7 entry.
I would appreciate your help and thank you in advance.
here's my boot script info :



  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 143521240 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /extlinux/extlinux.conf 
                       /grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    61,432,559    61,430,512   7 NTFS / exFAT / HPFS
/dev/sda2          61,442,048   103,647,356    42,205,309  83 Linux
/dev/sda3         103,649,278   156,296,384    52,647,107   f W95 Extended (LBA)
/dev/sda5         103,649,280   132,757,503    29,108,224  83 Linux
/dev/sda6         132,759,552   134,832,127     2,072,576  83 Linux
/dev/sda7         134,833,608   149,516,954    14,683,347  83 Linux
/dev/sda8         149,517,018   156,296,384     6,779,367  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CB9BCE0B9E67D0                       ntfs       
/dev/sda2        418aaa18-a29d-4729-93cc-9773e4e3d19d   ext4       
/dev/sda5        785970a0-4cbb-4832-9a1b-26e8624e8591   ext4       
/dev/sda6        5c799c83-769e-42cf-aacf-5191aec80076   ext4       
/dev/sda7        2a37fbbb-672d-493a-a813-ca505bab1a5d   ext4       
/dev/sda8        6181c882-c2bb-4e8e-ae9e-2eb8d72c6579   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda7        /boot                    ext4       (rw,commit=0)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=785970a0-4cbb-4832-9a1b-26e8624e8591 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2a37fbbb-672d-493a-a813-ca505bab1a5d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
```

---

### Post by oldfred on 2012-03-03
Please use code tags when posting long output or code. It makes it easier to read. # in the edit panel will automatically add code tags around hightlighted code in a post or you click on the # and paste between the code tags.

Is Ubuntu booting ok? The script has been fixed in the git/test mode to show which partition you actually are booting from, since you have two installs are you booting sda5 or sda7?

You also show grub2 installed to several partitions and menu.lst from grub legacy which normally is not now used. Did you find old instructions somewhere on Internet to make repairs or is this an upgrade from an older system?

You are missing all the boot files from a normal Windows install in sda1 and you have /boot/grub/core.img from a grub install to sda1 (?) which may have corrupted Windows.

Script should have found these files:
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Since you do not show a separate 100MB boot partition all three file should be in the NTFS partition with the boot flag. Or in Windows the active partition. Separately search to see if you have the files & Windows/System folders in your system. Script only looks in the standard places so if something got moved it may be there, but not in the correct place.

Do you have a Windows 7 repairCD? Or know someone else with the same 32 or 64bit (any) version of Windows.

---

### Post by Mark Phelps on 2012-03-04
Had you gone to the trouble, back when Win7 was working, to use the Backup feature, you could have created your own Win7 Repair CD -- and be using that now.

But since you didn't, you can still get the ISO image of a repair CD, but you have to purchase it.  Go to the link below to download an ISO image you can burn to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by Hedgehog1 on 2012-03-04
It surely looks like you installed Ubuntu several times, creating more partitions and eventually making the NTFS partition not bootable.

Oldfred is very correct when he says that most Win7 installs have a tiny 100 meg partition first on the disk that boots Win7, the the larger Win 7 NTFS partition.

**Before you do anything else, please boot up in Ubuntu (boot from the hard drive, or a live CD/USB) and backup all your data from both the windows and Ubuntu sides!!!**

You may need to acquire an external USB drive if you don't have one yet.  Backing up to that is easiest.

**NOW THAT YOU HAVE BACKED UP YOUR DATA** you can experiment with fixes suggested here.

Depending on your situation and skill level, you may need to rebuild hard drive and the restore your data to the newly restored drive.

May I suggest the following layout:

/dev/sda1 100 meg NTFS Windows boot partition
/dev/sda2 NTFS Windows OS partition
/dev/sda3 NTFS data storage partition (shared by both Windows & Ubuntu)
/dev/sda4 Logical partition that holds all additional partitions below (MSDOS partition map only allows 4 primary partitions, and this is how we get arounc that limit)
__/dev/sda5 ext4 '/' root Linux Partition (OS and Programs)
__/dev/sda6 ext4 '/home/' this partition holds your local data (bulk data is stored in the shared NTFS partition above)
__/dev/sda7 Linux Swap Space

Do you have your Windows 7 install disks?

***The Hedge***

:KS

---

### Post by mrbaloob on 2012-03-04
Hello everybody. thanks for your reply. 

Actually, my Ubuntu 11.10 is working like a charm. in fact, it's  directly on it that I could execute the Boot Info Script, without the  need to use the Live CD whatsoever.
I think that it is booting from Sda7 and not from Sda5, I'll let you  double check it on from the Gparted screen shot in here, it shows  '/Boot' next to sda7 !! :

This is an upgrade from an older system (Ubuntu 11.04). And honestly, I  did my best to repair the Grub2 myself in order to add the Win7 entry, I  used a tool called "Boot Repair" ... this is probably the reason why it  looks messed up!

those were the two drives that I have. I did not find any windows file !!!
and yes, i do have win7 installation CD.
I've already backed up all my data in an external hard drive.
would you then advise me to wipe up my drive and start a fresh installation?

Thanks.

---

### Post by mrbaloob on 2012-03-04
hey Hedge. Good architecture of the drive.
yes i've got my installation CD win7.
I tried on my previous message above to add a picture, of Gparted, but it was removed automatically when i hit submit message. anyways.
do you advise me to reinstall win7 and ubuntu 11.10 ?
if yes, which one should i install first ?

cheers mate.

---

### Post by oldfred on 2012-03-04
With BIOS/MBR it is slightly easier to install Windows first. Windows would overwrite the grub2 boot loader in the MBR if you install it second. It is relatively easy to reinstall the grub2 boot loader with Boot-Repair or the Ubuntu liveCD.

If you do reinstall then be sure to backup anything in Ubuntu you may want to keep. Including /home, if you made any system wide changes those are in /etc and if you added a lot of programs you can export a list to reinstall easily.

Once you get Windows installed make that Windows repairCD that Mark suggested.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by mrbaloob on 2012-03-04
hi oldfred. Appreciate your answer.

I'll basically follow your advice. I already backed up everything and I am ready now to install fresh OSs starting with Win7, followed by Ubuntu 11.10.

But you know what, i really liked as well Mark's Drive Layout that he suggested to me. In fact, i'd like to follow his advice as well.

My only problem is that I'm not sure I know how to install the Win7 Boot in the first 100 MB partition that I'll create ! then the Win7 OS in a different partition !!
when I installed previously my Win7 .... I only chose to install everything in the drive C:/
Please, if you can explain it quickly or if you have any link to a detailed method I'll appreciate it.
in face, i found that the installation of ubuntu is better organised than Windows ... it gives you from the start the option to choose how to configurate your drive and how to install /boot, /home, /media ...etc however you like !

I'll be waiting for your answer before I install anything,

Thanks a lot.

---

### Post by Mark Phelps on 2012-03-04
When you install Win7 to a blank drive (unformatted) or to unformatted space on a drive, it automatically creates the 100MB partition and writes the boot loader files there.

If you don't want to bother with a separate Win7 boot partition (and if you're not encrypting your disk, you don't need it), then you can create an existing NTFS partition with GParted and install to that.  Just be sure to have win7 REFORMAT that partition as part of the installation.

With one NTFS partition, it will include the boot loader files and OS files in the same partition.

---

### Post by NikTh on 2012-03-04
> **mrbaloob said:**
> 

My only problem is that **I'm not sure I know how to install the Win7 Boot in the first 100 MB** partition that I'll create ! then the Win7 OS in a different partition !!

Its not necessary to create a 100MB partition. Windows will do that automatically. Do not bother for that. 
Just install windows first and ubuntu after.

---

