---
title: "Black screen with blinking cursor"
date: 2018-01-06
forum: New to Ubuntu
---

### Post by kamo555 on 2018-01-06
Hello everyone! 
I am newbie.

Today, after turning my pc on i got an unexpected black screen with a blinkin cursor. I can not write anything, the pc just doesnt response. I got an USB-Live, tried to run boot-repair. It didnt help. This is what boot-repair told me: 


Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 2b80aa74-048e-4485-be29-47a7bc7f9aa5 root hd0,gpt4 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

sda: ___________________________________________________________________________

    File system:       
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 1050624 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,250,263,727 1,250,261,680  83 Linux


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 3.7 GiB, 4005560320 bytes, 7823360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *            128     7,823,359     7,823,232   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda                                                           
/dev/sdb1        80083f10-2732-4758-ada4-39fd122d7661   ext3       
/dev/sdc1        1ABD-FAF0                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jan  6 10:18 ata-ADATA_SP900_7E0220019128 -> ../../sda
lrwxrwxrwx 1 root root  9 Jan  6 10:10 ata-PLDS_DVD-ROM_DH-16D3S -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan  6 10:18 ata-WDC_WD6400AAKS-00A7B0_WD-WCASY1810880 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan  6 10:18 ata-WDC_WD6400AAKS-00A7B0_WD-WCASY1810880-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jan  6 10:18 usb-TOSHIBA_TransMemory_5B84070002CA-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jan  6 10:18 usb-TOSHIBA_TransMemory_5B84070002CA-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jan  6 10:18 wwn-0x50014ee1567538ce -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan  6 10:18 wwn-0x50014ee1567538ce-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jan  6 10:18 wwn-0x5707c1800000fe3b -> ../../sda

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/11878/mounts) leaked on lvs invocation. Parent PID 17140: bash
File descriptor 63 (pipe:[49898]) leaked on lvs invocation. Parent PID 17140: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20180106_1018 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
Error: end of file while reading /dev/sda
Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
The primary GPT table is corrupt, but the backup appears OK, so that will be used.
boot-repair is executed in live-session (Ubuntu 16.04.3 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
sda may have broken partition table.

=================== os-prober:


=================== blkid:
/dev/sdb1: UUID="80083f10-2732-4758-ada4-39fd122d7661" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="97759775-01"
/dev/sdc1: UUID="1ABD-FAF0" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/sda: PTUUID="8ac4b65e-628b-4c6a-a761-4271b38f0abb" PTTYPE="gpt"

ls /sys/firmware/efi/vars : UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,USB_POINT-8be4df61-93ca-11d2-aa0d-00e098032b8c,UsbMassDevValid-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824,SR5690ASetup-7e7092f3-0103-4948-a14c-9c2526ce773b,SpdBypassSerial-8be4df61-93ca-11d2-aa0d-00e098032b8c,SpdBypassData-8be4df61-93ca-11d2-aa0d-00e098032b8c,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupCpuFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Setup-80e1202e-2697-4264-9cc9-80762c3e5863,SbNvramVar-393c4833-402f-4bd5-bf5a-1f5cd8681444,S3SS-4bafc2b4-02dc-4104-b236-d6f1b98d9e84,Ps2MouseDetectRecord-09b5c46a-0f41-4cee-84ff-f3660a0b08d6,Ps2KeyboardDetectRecord-5a47386b-4c41-43b6-a140-824b0260ca8d,Profile-3-b05e6b5f-6ed8-4015-b5c5-b1049faf3e5b,Profile-2-b05e6b5f-6ed8-4015-b5c5-b1049faf3e5b,Profile-1-b05e6b5f-6ed8-4015-b5c5-b1049faf3e5b,Profile0-b05e6b5f-6ed8-4015-b5c5-b1049faf3e5b,ProcMitAttrib-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,PreviousMemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,PNP0604_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0604_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0510_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0510_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_1_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_1_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0400_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0400_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,OsIndicationsSupported-8be4df61-93ca-11d2-aa0d-00e098032b8c,OsIndications-8be4df61-93ca-11d2-aa0d-00e098032b8c,OldLegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,OA3MSDMvariable-8be4df61-93ca-11d2-aa0d-00e098032b8c,new_var,NetworkStackVar-d1405d16-7afc-4695-bb12-41459d3695a2,NBMemoryLength-490216c0-076a-44d3-a536-ace05c90e386,MonotonicCounter-01368881-c4ad-4b1d-b631-d57a8ec8db6b,MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23,ModuleVersion-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemRestoreTime-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemRestoreSerialLength-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemRestoreCpuId-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemRestoreConfigId-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,MemoryS3SaveVolLength-0a51b41d-de21-43fe-be27-d6dbc9efd104,MemoryS3SaveVol-0a51b41d-de21-43fe-be27-d6dbc9efd104,MemoryS3SaveNv-b1cfc482-4cb2-4cee-9b00-ce2579ec7186,MemMitAttrib-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,MemContextNv-c3a4e49f-485f-4fd6-a2ea-2bc87455ad4b,MemContext-c3a4e49f-485f-4fd6-a2ea-2bc87455ad4b,LegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,HpcModeBU-8be4df61-93ca-11d2-aa0d-00e098032b8c,HiiDB-1b838190-4625-4ead-abc9-cd5e6af18fe0,FPDT_Variable-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15,EasyVoltageAddress-dd41adf5-4368-4654-b1ca-46a6b98d9e84,EasyTuneSetupAddress-2a64d079-aceb-4ad9-afd5-252e35ba994a,EasySmartFanAddress-dd41adf5-4368-4654-b1ca-46a6b98d9e84,EasyHealthAddress-dd41adf5-4368-4654-b1ca-46a6b98d9e84,DriverHlthEnable-0885f288-418c-4be1-a6af-8bad61da08fe,DriverHealthCount-7459a7d4-6533-4480-bba7-79e25a4443c9,del_var,CpuS3Resume-30b98b95-dfa3-4501-a3ce-e38c186384a0,CoreLevelBU-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c,BiosSetupType-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34,AMIMemInfo-43387991-1223-7645-b5bb-aa7675c5c8ef,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== efibootmgr -v
BootCurrent: 0004
Timeout: 3 seconds
BootOrder: 0000,0004,0002,0003
Boot0000* ubuntu    HD(1,GPT,9c697960-393d-4a1b-9f95-df1aef174218,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0002* Hard Drive     BBS(HD,,0x0)AMGOAMNO........m.A.D.A.T.A. .S.P.9.0.0....................A.........................>..Gd-.;.A..MQ..L.E.7.2.0.0.2.1.0.1.9.8.2. . . . . . . . ......AMBOAMNO........m.W.D.C. .W.D.6.4.0.0.A.A.K.S.-.0.0.A.7.B.0....................A.........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.S.A.1.Y.1.8.8.0.0.8......AMBOAMNO........s.T.O.S.H.I.B.A. .T.r.a.n.s.M.e.m.o.r.y. .P.M.A.P....................A.......................F..Gd-.;.A..MQ..L.T.O.S.H.I.B.A. .T.r.a.n.s.M.e.m.o.r.y. .P.M.A.P......AMBO
Boot0003* CD/DVD Drive     BBS(CDROM,,0x0)AMGOAMNO........m.A.D.A.T.A. .S.P.9.0.0....................A.........................>..Gd-.;.A..MQ..L.E.7.2.0.0.2.1.0.1.9.8.2. . . . . . . . ......AMBO
Boot0004* UEFI: TOSHIBA TransMemory PMAP    PciRoot(0x0)/Pci(0x13,0x2)/USB(2,0)/HD(1,MBR,0x0,0x80,0x775f80)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sdb1    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sdb1.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:64.0GB:scsi:512:512:gpt:ATA ADATA SP900:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:539MB:1049kB:ext2::bios_grub;
4:539MB:55.5GB:54.9GB:ext4::;
3:55.5GB:64.0GB:8552MB:linux-swap(v1)::;

BYT;
/dev/sdb:640GB:scsi:512:512:msdos:ATA WDC WD6400AAKS-0:;
1:1049kB:640GB:640GB:ext3::boot;

BYT;
/dev/sdc:4006MB:scsi:512:512:msdos:TOSHIBA TransMemory:;
1:65.5kB:4006MB:4005MB:fat32::boot;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk          596.2G
sdb1  part ext3     596.2G
sr0   rom            1024M
loop0 loop squashfs   1.4G
sdc   disk            3.7G
sdc1  part vfat       3.7G
sda   disk           59.6G

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sr0      1  0  1 running
loop0    1  1  0         /rofs
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sda      0  0  0 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4052420k,nr_inodes=1013105,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=820288k,mode=755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=5a0881c0dbf8a19e)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13972)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=820288k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext3 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 dvd ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kfd kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdb1 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control
The primary GPT table is corrupt, but the backup appears OK, so that will be used.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     802M  9.4M  792M   2% /run
/dev/sdc1      vfat      3.8G  1.5G  2.3G  40% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      4.0G   77M  3.9G   2% /
tmpfs          tmpfs     4.0G  212K  4.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     4.0G     0  4.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     4.0G  124K  4.0G   1% /tmp
tmpfs          tmpfs     802M   68K  801M   1% /run/user/999
/dev/sdb1      ext3      587G   21G  537G   4% /mnt/boot-sav/sdb1

=================== fdisk -l:
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8AC4B65E-628B-4C6A-A761-4271B38F0ABB

Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M EFI System
/dev/sda2    1050624   1052671      2048    1M BIOS boot
/dev/sda3  108341248 125044735  16703488    8G Linux swap
/dev/sda4    1052672 108341247 107288576 51.2G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/sdb: 596.2 GiB, 640135028736 bytes, 1250263728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x97759775

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1  *     2048 1250263727 1250261680 596.2G 83 Linux




Disk /dev/sdc: 3.7 GiB, 4005560320 bytes, 7823360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *      128 7823359 7823232  3.7G  b W95 FAT32


No OS or WinEFI system

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the boot.




Any ideas how to help me?

---

### Post by leunam12 on 2018-01-06
black screen with blinking cursor means that no bootable
device was found. It could mean problems with the filesystem,
corrupt boot record or damaged hard drive. The first step in the
diagnostic process is to Boot the USB again and
run the 'Disks' utility and check the SMART sections for problems on
your hard drive.

---

### Post by RobGoss on 2018-01-06
You may also want to use the **code tags** when posting output results please this here for details [https://ubuntuforums.org/misc.php?do=bbcode](https://ubuntuforums.org/misc.php?do=bbcode)

The **Boot Info Summary **should have provided a link for you to share your boot information here

---

