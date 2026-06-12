---
title: "ubuntu will not boot - blank screen with flashing cursor"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by orinalees on 2015-04-14
Ubuntu crashed then when i tried to reboot it went into grub recovery. i tried to mount it via usb whihc failed, now when i try to boot it just has a blank screen with a flashing cursor and won't accept any commands.

this is what i was able to obtain from boot disk repair

Any help appreciated




 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

ubuntu-vg-root: ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

ubuntu-vg-swap_1: ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       499,711       497,664  83 Linux
/dev/sda2             501,758 1,953,523,711 1,953,021,954   5 Extended
/dev/sda5             501,760 1,953,523,711 1,953,021,952  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        QjGWvu-X50a-jVZS-ODlx-RcQA-Y2NR-bWV9lU LVM2_member 
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       54590126-0b57-4f92-9441-51e55daa2605   swap       
/dev/zram1       1319662e-ac84-492d-bb0b-cffb12f1f8f4   swap       
/dev/zram2       3b730dd7-9fbf-4ccf-842a-8b051ddb75f9   swap       
/dev/zram3       61ac844c-764d-440c-a0b2-d4da3e1e8581   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 14 14:02 ata-HL-DT-ST_BD-RE_BH10LS30_K95B2DA3451 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr 14 14:03 ata-ST31000526SV_9VPEATFZ -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 14 14:02 ata-ST31000526SV_9VPEATFZ-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 14 14:02 ata-ST31000526SV_9VPEATFZ-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 14 14:02 ata-ST31000526SV_9VPEATFZ-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Apr 14 14:03 dm-name-ubuntu--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Apr 14 14:03 dm-name-ubuntu--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 14 14:03 dm-uuid-LVM-ykHfzBOEVO8EAecOV1rLGgUl80Q2qCheXeYJCJxJ8jUJXAzfLv70MapX1ZFGOzxe -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 14 14:03 dm-uuid-LVM-ykHfzBOEVO8EAecOV1rLGgUl80Q2qCheY3dGkSuMoHwc5H7ZUm4nfCkS5MzhgOtH -> ../../dm-0
lrwxrwxrwx 1 root root  9 Apr 14 14:02 usb-Generic_USB_CF_Reader_2004888-0:1 -> ../../sdc
lrwxrwxrwx 1 root root  9 Apr 14 14:02 usb-Generic_USB_MS_Reader_2004888-0:3 -> ../../sde
lrwxrwxrwx 1 root root  9 Apr 14 14:02 usb-Generic_USB_SD_Reader_2004888-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 Apr 14 14:02 usb-Generic_USB_SM_Reader_2004888-0:2 -> ../../sdd
lrwxrwxrwx 1 root root  9 Apr 14 14:03 wwn-0x5000c5003f0d4700 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 14 14:02 wwn-0x5000c5003f0d4700-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 14 14:02 wwn-0x5000c5003f0d4700-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 14 14:02 wwn-0x5000c5003f0d4700-part5 -> ../../sda5

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ubuntu--vg-root
ubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  09 00 ac 00 0c 00 01 02  2e 00 00 00 2e 00 42 00  |..............B.|
00000010  0c 00 02 02 2e 2e 00 00  18 14 42 00 14 00 09 01  |..........B.....|
00000020  37 38 30 38 38 35 34 30  31 32 ac 00 3e 20 42 00  |7808854012..> B.|
00000030  14 00 0a 01 31 39 30 30  34 37 32 35 31 36 ac 00  |....1900472516..|
00000040  24 20 42 00 14 00 09 01  31 36 38 34 38 32 32 38  |$ B.....16848228|
00000050  35 00 ac 00 91 13 42 00  14 00 0a 01 32 31 31 32  |5.....B.....2112|
00000060  35 34 31 30 31 31 ac 00  9d 0c 42 00 14 00 0a 01  |541011....B.....|
00000070  31 30 35 36 32 34 34 39  35 31 ac 00 01 00 ac 00  |1056244951......|
00000080  14 00 09 01 34 33 35 34  35 34 30 38 31 35 ac 00  |....4354540815..|
00000090  2f 0e 42 00 14 00 0a 01  31 38 37 32 33 31 36 36  |/.B.....18723166|
000000a0  37 36 ac 00 26 29 42 00  14 00 0a 01 31 31 35 30  |76..&)B.....1150|
000000b0  38 30 32 36 30 31 ac 00  17 0c 42 00 24 00 0a 01  |802601....B.$...|
000000c0  31 34 38 34 36 30 39 37  35 33 ac 00 04 00 ac 00  |1484609753......|
000000d0  10 00 08 01 33 32 30 39  37 38 30 39 02 18 42 00  |....32097809..B.|
000000e0  14 00 08 01 38 37 39 39  31 33 31 33 32 36 31 30  |....879913132610|
000000f0  ff 0b 42 00 14 00 09 01  38 31 30 38 38 34 38 33  |..B.....81088483|
00000100  34 32 ac 00 02 1d 42 00  24 00 09 01 34 32 31 35  |42....B.$...4215|
00000110  36 34 32 35 33 38 0a 01  05 00 ac 00 10 00 08 01  |642538..........|
00000120  36 31 38 39 31 34 31 39  5e 15 42 00 14 00 09 01  |61891419^.B.....|
00000130  36 34 38 31 38 33 37 37  31 32 31 33 ce 1d 42 00  |648183771213..B.|
00000140  14 00 0a 01 31 37 32 31  31 31 33 35 34 39 30 36  |....172111354906|
00000150  7e 27 42 00 14 00 0a 01  31 34 31 33 39 37 33 32  |~'B.....14139732|
00000160  32 32 35 36 55 20 42 00  14 00 0a 01 31 37 31 38  |2256U B.....1718|
00000170  31 35 38 33 36 38 30 33  35 09 42 00 14 00 0a 01  |158368035.B.....|
00000180  31 35 30 31 36 37 32 30  32 37 34 32 60 20 42 00  |150167202742` B.|
00000190  14 00 09 01 37 32 35 39  38 38 35 30 37 31 ac 00  |....7259885071..|
000001a0  8b 1b 42 00 14 00 0a 01  32 30 34 34 31 38 31 30  |..B.....20441810|
000001b0  38 32 ac 00 1b 0d 42 00  14 00 0a 01 31 33 33 38  |82....B.....1338|
000001c0  37 39 33 31 32 34 ac 00  2d 1f 42 00 14 00 09 01  |793124..-.B.....|
000001d0  39 33 39 37 31 33 36 34  37 30 ac 00 58 06 42 00  |9397136470..X.B.|
000001e0  14 00 09 01 39 37 32 37  36 36 36 31 32 36 ac 00  |....9727666126..|
000001f0  6c 22 42 00 14 00 0a 01  31 35 32 32 37 31 35 35  |l"B.....15227155|
00000200

Unknown BootLoader on sda2

00000000  d1 d1 5d 80 44 6e 5c d3  81 80 65 da 79 2e 11 07  |..].Dn\...e.y...|
00000010  80 16 c0 3f 5a e7 57 82  11 fb c1 58 ba cf 78 66  |...?Z.W....X..xf|
00000020  1a 00 74 8e bd c9 b6 a3  60 23 bc ca 4d 9a 55 5e  |..t.....`#..M.U^|
00000030  6a 9a 61 20 05 98 52 91  e9 6e 9b 0b eb e8 81 90  |j.a ..R..n......|
00000040  3e 8d 85 05 38 52 04 f0  7e 0a 05 dd 7a 27 de 48  |>...8R..~...z'.H|
00000050  b9 14 74 be c7 a3 55 26  34 74 fe 9d 3e 8a 4c 23  |..t...U&4t..>.L#|
00000060  a3 a3 86 00 f1 e7 a8 0f  40 27 24 4c 19 00 58 00  |........@'$L..X.|
00000070  f4 f7 02 21 cb 81 c8 31  7b de af 00 82 08 62 ea  |...!...1{.....b.|
00000080  fb 47 43 e5 5d 0a 2b 66  82 41 d0 48 54 cd 57 56  |.GC.].+f.A.HT.WV|
00000090  18 2c 55 6e 51 48 18 60  cd 22 27 57 41 04 74 40  |.,UnQH.`."'WA.t@|
000000a0  fe 65 70 57 05 a5 05 b8  99 15 91 d7 a0 be 8d 2a  |.epW...........*|
000000b0  29 a6 8e 8e be 93 4d a3  a2 dd 14 2b e8 a8 92 20  |).....M....+... |
000000c0  ad 0f 53 a7 a6 85 36 14  14 e1 ae 8e b8 d3 c9 69  |..S...6........i|
000000d0  a0 88 a0 f0 50 01 cc 04  6b d6 3c 16 41 66 0c 03  |....P...k.<.Af..|
000000e0  80 23 bc 44 57 05 d0 2e  1e 89 93 88 b0 82 d1 ba  |.#.DW...........|
000000f0  a8 b7 41 5d 65 26 15 86  1d 61 42 78 78 12 c7 c1  |..A]e&...aBxx...|
00000100  30 83 27 4b a8 fc 90 1b  55 69 e1 2a 84 30 cc 10  |0.'K....Ui.*.0..|
00000110  28 92 5e fe b8 1a 47 57  fd f1 e5 4a 5e f0 48 1f  |(.^...GW...J^.H.|
00000120  33 21 f4 a0 c0 50 02 cd  97 24 a1 04 e8 82 d4 23  |3!...P...$.....#|
00000130  25 16 57 62 9a 09 e8 e9  75 c4 b1 47 d1 f4 54 5b  |%.Wb....u..G..T[|
00000140  47 a3 41 1d 71 e3 a9 4d  64 e9 65 50 50 01 cc 02  |G.A.q..Md.ePP...|
00000150  e1 d0 50 3e 01 dd e2 43  04 31 37 ab 7d 13 47 53  |..P>...C.17.}.GS|
00000160  a7 5e e2 2f 36 b6 69 aa  4d 3d 06 42 cd bd c0 b0  |.^./6.i.M=.B....|
00000170  69 b7 9d 18 40 85 9c 03  48 43 ce 0c 87 c0 39 1d  |i...@...HC....9.|
00000180  36 1e c7 1d f9 c3 e3 e1  46 41 38 74 f3 e3 94 80  |6.......FA8t....|
00000190  58 d8 19 5c c5 f3 5f 67  be f4 a8 ca 49 27 4f a5  |X..\.._g....I'O.|
000001a0  26 f4 be c2 20 59 82 de  8f 47 d1 5d 55 ed 53 a7  |&... Y...G.]U.S.|
000001b0  5f 47 5f 55 1a 1b 6c 30  0c ce 24 8d 10 38 00 3b  |_G_U..l0..$..8.;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 c0 68 74 00 00  |............ht..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on ubuntu-vg-root


Unknown BootLoader on ubuntu-vg-swap_1



========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/3150/mounts) leaked on lvs invocation. Parent PID 8032: bash
File descriptor 63 (pipe:[25359]) leaked on lvs invocation. Parent PID 8032: bash
File descriptor 9 (/proc/3150/mounts) leaked on lvchange invocation. Parent PID 8279: bash
File descriptor 63 (pipe:[25359]) leaked on lvchange invocation. Parent PID 8279: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root
  Volume group "ubuntu-vg-root" not found
  Skipping volume group ubuntu-vg-root
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-root: No such file or directory
File descriptor 9 (/proc/3150/mounts) leaked on lvchange invocation. Parent PID 8279: bash
File descriptor 63 (pipe:[25359]) leaked on lvchange invocation. Parent PID 8279: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1
  Volume group "ubuntu-vg-swap_1" not found
  Skipping volume group ubuntu-vg-swap_1
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory
hexdump: /dev/mapper/ubuntu-vg-swap_1: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-04-14__14h03 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
BLKID BEFORE LVM ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda5: UUID="QjGWvu-X50a-jVZS-ODlx-RcQA-Y2NR-bWV9lU" TYPE="LVM2_member"
/dev/zram0: UUID="54590126-0b57-4f92-9441-51e55daa2605" TYPE="swap"
/dev/zram1: UUID="1319662e-ac84-492d-bb0b-cffb12f1f8f4" TYPE="swap"
/dev/zram2: UUID="3b730dd7-9fbf-4ccf-842a-8b051ddb75f9" TYPE="swap"
/dev/zram3: UUID="61ac844c-764d-440c-a0b2-d4da3e1e8581" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/3150/mounts) leaked on vgscan invocation. Parent PID 3189: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "ubuntu-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/3150/mounts) leaked on vgchange invocation. Parent PID 3189: /bin/bash
2 logical volume(s) in volume group "ubuntu-vg" now active
File descriptor 9 (/proc/3150/mounts) leaked on lvscan invocation. Parent PID 3189: /bin/bash
LVSCAN:
ACTIVE            '/dev/ubuntu-vg/root' [911.48 GiB] inherit
ACTIVE            '/dev/ubuntu-vg/swap_1' [19.75 GiB] inherit
File descriptor 9 (/proc/3150/mounts) leaked on lvs invocation. Parent PID 4776: /bin/sh
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda5: UUID="QjGWvu-X50a-jVZS-ODlx-RcQA-Y2NR-bWV9lU" TYPE="LVM2_member"
/dev/zram0: UUID="54590126-0b57-4f92-9441-51e55daa2605" TYPE="swap"
/dev/zram1: UUID="1319662e-ac84-492d-bb0b-cffb12f1f8f4" TYPE="swap"
/dev/zram2: UUID="3b730dd7-9fbf-4ccf-842a-8b051ddb75f9" TYPE="swap"
/dev/zram3: UUID="61ac844c-764d-440c-a0b2-d4da3e1e8581" TYPE="swap"

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA ST31000526SV (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      1049kB  256MB   255MB   primary
2      257MB   1000GB  1000GB  extended
5      257MB   1000GB  1000GB  logical                lvm



                                                                          
Error: /dev/mapper/ubuntu--vg-root: unrecognised disk label


                                                                          
Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA ST31000526SV;
1:1049kB:256MB:255MB:::;
2:257MB:1000GB:1000GB:::;
5:257MB:1000GB:1000GB:::lvm;


                                                                          
Error: /dev/mapper/ubuntu--vg-root: unrecognised disk label


                                                                          
Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdc sdd sde sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout ubuntu-vg uhid uinput urandom usb vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control ubuntu--vg-root ubuntu--vg-swap_1
Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  9.7G  5.2M  9.7G   1% /
udev           devtmpfs   9.7G   12K  9.7G   1% /dev
tmpfs          tmpfs      2.0G  1.2M  2.0G   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      9.7G  8.0K  9.7G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      9.7G     0  9.7G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d50a3

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 978.7 GB, 978694701056 bytes
255 heads, 63 sectors/track, 118986 cylinders, total 1911513088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-swap_1: 21.2 GB, 21202206720 bytes
255 heads, 63 sectors/track, 2577 cylinders, total 41410560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Error: no partitions


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.

---

### Post by sandyd on 2015-04-14
Boot repair shows that
[LIST=1]
[*]There is no boot loader installed on disk
[*]FS is not recognized on both swap and root partitions
[/LIST]

There is possibly file corruption due to the crash. Do you have any backups?

---

