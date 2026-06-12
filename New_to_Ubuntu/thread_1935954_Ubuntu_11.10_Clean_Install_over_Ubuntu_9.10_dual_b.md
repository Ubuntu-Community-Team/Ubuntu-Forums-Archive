---
title: "Ubuntu 11.10 Clean Install over Ubuntu 9.10 dual boot with Win XP"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Ramveng on 2012-03-05
No background knowledge on Linux. Not much in Windows either. I can operate a computer on Windows platform.. That's all.  :confused: 
Installed **Ubuntu 9.10** alongside *Win XP* as dual boot two weeks back inspired by the **Free Software** principle. Liked it. Later a friend gave DVD of Ubuntu 11.10. Now I want to upgrade to 11.10 by clean install process as dual boot alongside Win XP. 

[LIST=1]
[*] When the DVD of 11.10 is autorun in Win XP, on clicking "*Help me boot from CD*", a dialogue "*Are you sure to unistall Ubuntu*?" is displayed. Am I to give "*yes*"?
[*][COLOR=Red]**If the answer is [B]"*Yes*"** for the above question, then please explain in detail (assuming that I am a layman) the procedure to proceed further ie., as to how to remove Ubuntu 9.10 and complete the installation of the latest version. (While installing 9.10,I selected something like *"use largest contiguous disk space..." *without knowing what I was doing.[/B][/COLOR]
[*] Please note that while trying to edit the boot priority option in BIOS (AMI) The DVD-RAM writer of TSST corporation is not seen listed!
[*]On pressing F8 key on boot up, the DVD RAM drive can be selected. But, again, it goes from there to the OS choices screen where ubuntu 9.10 and WinXP are listed.
[*]Otherwise on selecting the option "*Boot from CD" * in the autorun dialogue boxin Win XP, on rebooting, the OS choices screen lists only the installed version of Ubuntu 9.10 and Win XP and not the latest version in the DVD..
[*]I reproduce the boot info script result herunder: (Sorry, I don't understand any bit of this jargon)                                                                                       ```
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 11 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda10 
                       starts at sector 63.
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25712570

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda2          61,432,560   312,576,704   251,144,145   f W95 Extended (LBA)
/dev/sda5          61,432,623    67,730,039     6,297,417   7 NTFS / exFAT / HPFS
/dev/sda6          67,730,103    95,827,724    28,097,622   7 NTFS / exFAT / HPFS
/dev/sda7         122,865,183   184,297,679    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda8         184,297,743   245,730,239    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda9         245,730,303   252,027,719     6,297,417   7 NTFS / exFAT / HPFS
/dev/sda10        252,027,783   282,840,389    30,812,607   7 NTFS / exFAT / HPFS
/dev/sda11        282,840,453   311,227,244    28,386,792  83 Linux
/dev/sda12        311,227,308   312,576,704     1,349,397  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2A00D70B00D6DCBF                       ntfs       
/dev/sda10       3030D2CF30D29AE4                       ntfs       
/dev/sda11       69fb0a6c-5aef-4892-8e49-88c2348023ef   ext4       
/dev/sda12       1e099cbb-7164-4525-8a25-21c91ffba9c5   swap       
/dev/sda5        5A88C56288C53D6F                       ntfs       
/dev/sda6        FCB4BF61B4BF1CD8                       ntfs       
/dev/sda7        EE240A212409ED81                       ntfs       
/dev/sda8        0040654C40654A0C                       ntfs       
/dev/sda9        8C00D3A400D39394                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda11       /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /media/0040654C40654A0C  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /media/Picture Book      iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sr1         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ramesh)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr="Ubuntu" 
--------------------------------------------------------------------------------

======================== sda8/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

======================== sda9/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

========================== sda11/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,11)
search --no-floppy --fs-uuid --set 69fb0a6c-5aef-4892-8e49-88c2348023ef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 69fb0a6c-5aef-4892-8e49-88c2348023ef
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=69fb0a6c-5aef-4892-8e49-88c2348023ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 69fb0a6c-5aef-4892-8e49-88c2348023ef
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=69fb0a6c-5aef-4892-8e49-88c2348023ef ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2a00d70b00d6dcbf
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=69fb0a6c-5aef-4892-8e49-88c2348023ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=1e099cbb-7164-4525-8a25-21c91ffba9c5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.31-14-generic              1
               =                boot/vmlinuz-2.6.31-14-generic                 2
               =                initrd.img                                     1
               =                vmlinuz                                        2

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```
[*]Please note that while trying to edit the boot priority option in BIOS (AMI) The DVD-RAM writer of TSST corporation is not seen listed!
[*]The important hardware details are furnished here.
[/LIST]

[LIST]
[*]Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
[*]*-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW  CRX230EE
                vendor: SONY
[*]  *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S223C
                vendor: TSSTcorp
[*]*-memory
          description: System memory
          physical id: 0
          size: 993MiB
[/LIST]

---

### Post by Frogs Hair on 2012-03-05
From the very top of the output the following line seems to indicate you are using Wubi which is installed inside the Windows partition .```
Boot files:        /boot.ini /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr 
``` 

I think that is why you are being asked "are you sure you want to install Ubuntu." If you have a Wubi installation remove it from the windows side and then proceed with installing Ubuntu from the disk. You can choose to use Wubi again or install a  traditional dual boot. 

Wubi can be upgraded and use the same space but I would not recommend because 9.10 is no longer supported . At best you could upgrade to 10.04.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Ramveng on 2012-03-05
Thanks Frogs Hair for the immediate reply. Though I am not a computer expert, I have some lingering doubts. Kindly clarify. 
When I decided to try Ubuntu, my friend gave me 4 CDs, namely., Ubuntu 8.04, 8.10, 9.10, 10.04 LTS in DVD). I was inclined to install 10.04, but the computer would not boot from CDs. Everytime it stops at some point. Once I went as far as the screen to select the type of install and I checked the Data Integrity. But from there I could not go any further. Hence, I kept on trying all the four versions. I was able to work live on 9.10 which I was able to install later. Now, it is the Grub 1.97 Beta 2 that shows the OS choices. And please note that there is an Ubuntu folder of 600MB in Windows  drive C and Ubuntu is listed in the control panel\programs. But, the hard disk partitions sda 11 and sda 12 are linux partitions. I am able to run Ubuntu independently. So, does it mean that some remains of an earlier Wubi installation are there to be removed? [COLOR=Red][B]How to check whether my present working installation is traditional dual boot or wubi?

[/B][/COLOR][COLOR=Blue]Please note that in my original post I mentioned: "When the DVD of 11.10 is autorun in Win XP, on clicking "*Help me boot from CD*" in the ensuing dialogue, a dialogue "*Are you sure to **UNINSTAL** Ubuntu*?" is displayed".[/COLOR][COLOR=Red][B] (Sorry, the word UNINSTAL was inadvertently mispelt in my post).
[COLOR=Black]Please think of this and advise.
[/COLOR]
[/B][/COLOR]

---

### Post by oldfred on 2012-03-05
You have three systems. XP, a full install of Ubuntu and the wubi install inside your XP. If you boot XP and try to run the wubi installer it will uninstall the old wubi. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

When you boot you get the Ubuntu and XP choice and then in XP you should get XP or wubi. 

To install from the DVD you would have to select in BIOS. If BIOS does not let you boot DVD that is your system issue. Maybe with both CD & DVD it only boots from CD? or maybe a BIOS update would let you boot from either.

You can download a new ISO can create your own CD or USB (if you system boots from USB flash).

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Frogs Hair on 2012-03-05
> How to check whether my present working installation is traditional dual boot or wubi?One simple way is to look at the the picture of the boot loader at the Wubi Guide link. If you are using the Windows boot loader you are most likely using Wubi .

---

### Post by Ramveng on 2012-03-06
> **oldfred said:**
> You have three systems. XP, a full install of Ubuntu and the wubi install inside your XP. If you boot XP and try to run the wubi installer it will uninstall the old wubi. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

When you boot you get the Ubuntu and XP choice and then in XP you should get XP or wubi. 



**Thank You Mr. Old Fred!** You are right. There were 3 systems: Win XP, a failed wubi installation of Ubuntu inside Win XP, and a working independent dual-boot installation of Ubuntu 9.10. When I tried to boot into the wubi installation a black screen showed the following message: 

[COLOR=Red][I]"Windows could not start because the following file is missing or corrupt: <Windows root>\system32\hal.dll
Please re install a copy of the above file."[/I]
[/COLOR]
So I unistalled the wubi installation. 
Tried to boot from DVD of Ubuntu 11.10  by selecting "Help me boot from CD" dialogue on running the DVD in Win XP. The ensuing error screen is uploaded as an attachment. 

Thanks once again
Ramesh (Ramveng)

---

### Post by Ramveng on 2012-03-06
> **oldfred said:**
> 
To install from the DVD you would have to select in BIOS. If BIOS does not let you boot DVD that is your system issue. Maybe with both CD & DVD it only boots from CD? or maybe a BIOS update would let you boot from either.


I was able to make the DVD RAM drive as Ist boot device by playing around inside the BIOS set up utility. 
I tried restarting the system with the DVD of Ubuntu 11.10 in the DVD RAM drive. Pressed F8. Selected the DVD Drive from the options of boot device. Then again it was the Grub screen that appeared as described below:-[INDENT][INDENT]```
GNU GRUB Version 1.97~Beta4

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (Recovery Mode)
Memory Test (Memtest86+ serial console 115200)
Microsoft Windows XP Professional on /dev/sda1.

```[/INDENT][/INDENT]On selecting the first option the installed Ubuntu 9.10 gets started! Is there a way out to get the Ubuntu 11.10 listed in Grub? (Of course, without much of learning from the Tutorial; I am aged over 46! Ha Ha)
Advance Thanks.
Ramesh (Ramveng)

---

### Post by oldfred on 2012-03-06
It still may be a hardware issue. Or, are you sure the DVD is bootable?

Some have reported issues with RW disk, not sure about RAM disks, but most seem to have the fewest issues with CD-R from a CD bootable device.

 I now use USB flash drives as then I do not have to burn new CDs every install as I like to test various things. I also now use grub2 to directly (loopmount) boot an ISO from the hard drive and install to another hard drive. It also works if installing to another partition. But that is a bit more advanced as you have to manually edit grub's 40_custom with a boot stanza to boot the ISO.

---

### Post by Ramveng on 2012-03-08
> **oldfred said:**
> It still may be a hardware issue. Or, are you sure the DVD is bootable?

Some have reported issues with RW disk, not sure about RAM disks, but most seem to have the fewest issues with CD-R from a CD bootable device.

 I now use USB flash drives as then I do not have to burn new CDs every install as I like to test various things. I also now use grub2 to directly (loopmount) boot an ISO from the hard drive and install to another hard drive. It also works if installing to another partition. But that is a bit more advanced as you have to manually edit grub's 40_custom with a boot stanza to boot the ISO.
Thanks a lot Mr. OldFred. I think you should put up a good write up in this issue that be made sticky so that no other beginner wastes so much time trying to install from DVD and be driven away altogether from Linux/Ubuntu. I successfully installed *Oneiric Ocelot *from USB with no problems. And I am thrilled by the level of immediate online help by you people, like., OldFred and Frogs Hair. 
I am a leftist campaigning against monopolisation of the market by multinationals. I installed Ubuntu with a plan to propagate the use of Free Software. I would like to learn more so that I can help others locally.

---

### Post by oldfred on 2012-03-08
Glad you got it working.:)

If you have other issues, please start a new thread. You can change thread to solved.

---

