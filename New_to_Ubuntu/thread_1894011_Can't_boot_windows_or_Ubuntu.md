---
title: "Can't boot windows or Ubuntu"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by santhosh.1984e on 2011-12-11
#                  Boot Info Script 0.60    from 17 May 2011


#============================= Boot Info Summary: ===============================

 #=> Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

#sda1: __________________________________________________________________________

  #  File system:       ntfs
   # Boot sector type:  Windows Vista/7
    #Boot sector info:   No errors found in the Boot Parameter Block.
    #Operating System:  
    #Boot files:        /bootmgr /Boot/BCD

#sda2: __________________________________________________________________________

    #File system:       ntfs
    #Boot sector type:  Windows Vista/7
    #Boot sector info:   No errors found in the Boot Parameter Block.
    #Operating System:  Windows 7
    #Boot files:        /Windows/System32/winload.exe

#sda3: __________________________________________________________________________

   # File system:       ntfs
    #Boot sector type:  Windows Vista/7
    #Boot sector info:   No errors found in the Boot Parameter Block.
    #Operating System:  
    #Boot files:        

#sda4: __________________________________________________________________________

  #  File system:       Extended Partition
    #Boot sector type:  -
    #Boot sector info:  

#sda5: __________________________________________________________________________

  #  File system:       ntfs
    #Boot sector type:  Windows Vista/7
    #Boot sector info:   According to the info in the boot sector, sda5 starts 
    #                   at sector 2048.
    #Operating System:  
    #Boot files:        

#sda6: __________________________________________________________________________

  #  File system:       ntfs
   # Boot sector type:  Windows Vista/7
    #Boot sector info:   According to the info in the boot sector, sda6 starts 
      #                 at sector 2048.
   # Operating System:  
    #Boot files:        

#sda7: __________________________________________________________________________

  #  File system:       ext4
    #Boot sector type:  Unknown
    #Boot sector info:  
    #Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda7,
      # missing codepage or helper program, or other error
       #In some cases useful info is found in syslog - try
       # dmesg | tail  or so


# sda8: __________________________________________________________________________

   # File system:       swap
   # Boot sector type:  -
   # Boot sector info:  

#============================ Drive/Partition Info: =============================

# Drive: sda _____________________________________________________________________

#Disk /dev/sda: 250.1 GB, 250059350016 bytes
 # 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
#Units = sectors of 1 * 512 = 512 bytes
#Sector size (logical/physical): 512 bytes / 512 bytes

# Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

#  /dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
#  /dev/sda2             206,848    63,965,183    63,758,336   7 NTFS / exFAT / HPFS
#  /dev/sda3          63,965,184   169,871,359   105,906,176   7 NTFS / exFAT / HPFS
#  /dev/sda4         169,873,406   488,396,799   318,523,394   f W95 Extended (LBA)
# /dev/sda5         169,873,408   275,779,583   105,906,176   7 NTFS / exFAT / HPFS
# /dev/sda6         275,781,632   381,687,807   105,906,176   7 NTFS / exFAT / HPFS
# /dev/sda7         381,689,856   483,944,447   102,254,592  83 Linux
# /dev/sda8         483,946,496   488,396,799     4,450,304  82 Linux swap / Solaris


# "blkid" output: ________________________________________________________________

# Device           UUID                                   TYPE       LABEL

# /dev/loop0                                              squashfs   
# /dev/sda1        4C641ACD641ABA22                       ntfs       System Reserved
# /dev/sda2        8C941B73941B5ED0                       ntfs       
# /dev/sda3        0E0020F60020E705                       ntfs       
# /dev/sda5        4074C08A74C0845E                       ntfs       Data
# /dev/sda6        14E8E405E8E3E34A                       ntfs       Entertainment
# /dev/sda7        bb8bf986-d0b9-4efb-96c7-a93bdd44a1d8   ext4       
# /dev/sda8        78822509-f8ca-4cd9-b64e-4b64949168d7   swap       

#================================ Mount points: =================================

# Device           Mount_Point              Type       Options

# /dev/loop0       /rofs                    squashfs   (ro,noatime)
# /dev/sda1        /media/System Reserved   fuseblk    # # #(rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
# /dev/sr0         /cdrom                   iso9660    (ro,noatime)


# ======================== Unknown MBRs/Boot Sectors/etc: ========================

# Unknown BootLoader on sda7

# 00000000  46 49 4c 45 30 00 03 00  d7 0f 6a 0b 00 00 00 00  |FILE0.....j.....|
# 00000010  01 00 01 00 38 00 01 00  b0 01 00 00 00 04 00 00  |....8...........|
# 00000020  00 00 00 00 00 00 00 00  04 00 00 00 dc 00 00 00  |................|
# 00000030  10 06 00 00 00 00 00 00  10 00 00 00 48 00 00 00  |............H...|
# 00000040  00 00 00 00 00 00 00 00  30 00 00 00 18 00 00 00  |........0.......|
# 00000050  ae 94 11 2c e8 56 cb 01  00 95 d7 f1 39 0e c6 01  |...,.V......9...|
# 00000060  78 b2 a3 4c 98 8f cb 01  b6 83 47 f5 cf 8b cc 01  |x..L......G.....|
# 00000070  22 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |"...............|
# 00000080  30 00 00 00 78 00 00 00  00 00 00 00 00 00 03 00  |0...x...........|
# 00000090  5a 00 00 00 18 00 01 00  a5 00 00 00 00 00 01 00  |Z...............|
# 000000a0  ae 94 11 2c e8 56 cb 01  ae 94 11 2c e8 56 cb 01  |...,.V.....,.V..|
*
# 000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
# 000000d0  20 00 00 00 00 00 00 00  0c 00 49 00 4d 00 47 00  | .........I.M.G.|
# 000000e0  5f 00 30 00 31 00 39 00  37 00 2e 00 6a 00 70 00  |_.0.1.9.7...j.p.|
# 000000f0  67 00 00 00 00 00 02 00  50 00 00 00 68 00 00 00  |g.......P...h...|
# 00000100  00 00 00 00 00 00 01 00  50 00 00 00 18 00 00 00  |........P.......|
# 00000110  01 00 04 80 14 00 00 00  24 00 00 00 00 00 00 00  |........$.......|
# 00000120  34 00 00 00 01 02 00 00  00 00 00 05 20 00 00 00  |4........... ...|
# 00000130  20 02 00 00 01 02 00 00  00 00 00 05 20 00 00 00  | ........... ...|
# 00000140  20 02 00 00 02 00 1c 00  01 00 00 00 00 03 14 00  | ...............|
# 00000150  ff 01 1f 00 01 01 00 00  00 00 00 01 00 00 00 00  |................|
# 00000160  80 00 00 00 48 00 00 00  01 00 40 00 00 00 02 00  |....H.....@.....|
# 00000170  00 00 00 00 00 00 00 00  03 03 00 00 00 00 00 00  |................|
# 00000180  40 00 00 00 00 00 00 00  00 40 30 00 00 00 00 00  |@........@0.....|
# 00000190  84 39 30 00 00 00 00 00  84 39 30 00 00 00 00 00  |.90......90.....|
# 000001a0  32 04 03 ab 70 04 00 c2  ff ff ff ff 00 00 00 00  |2...p...........|
# 000001b0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
# 000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
# 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 10 06  |................|
# 00000200


I am not able to open windows or linux. i ve loaded live ubuntu cd and got these stuff.
Please tell me what need to be changed so that i can see dual booting menu when i start the system.

---

### Post by nothingspecial on 2011-12-11
Post moved to it's own thread.

---

### Post by mastablasta on 2011-12-11
use windows 7 cd to repair main boot record.
then try to install linux again:

#Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda7,
      # missing codepage or helper program, or other error

how did you install it ? what filesystem did you choose?

---

### Post by westie457 on 2011-12-11
Hello and welcome.

Not sure exactly what you have done. At first glance you have no Grub installed.

Open a terminal (Ctrl+Alt+T is the quick way) type in ```
sudo update-grub
``` any errors highlight all the output copy it and paste in a new reply between [CODE] tags. You get those by clicking on the # symbol at the top of the message window.

Thank you.


Edit: Ninjaed by mastablasta. His reply is probably better than mine.

---

