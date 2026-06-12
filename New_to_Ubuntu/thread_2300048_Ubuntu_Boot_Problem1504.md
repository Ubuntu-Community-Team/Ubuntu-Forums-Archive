---
title: "Ubuntu Boot Problem1504"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by HDD on 2015-10-23
Hi
     I am new user ,I have installed Ubuntu 15.04,Iam using system 2.20 ghz intel processor and  gb ram ,for quite sometimes my desktop is having booting problem 

Sometimes it shows"Read Error" on the first boot screen,sometimes it shows the screen wherein it asks to select from the following options:-

Ubuntu

Advance options for Ubuntu
Ubuntu-----version30.---generic
Ubuntu-----version30.---upstart
Ubuntu-----version30.---recover
  or

Ubuntu-----version15.---generic
Ubuntu-----version15.---upstart
Ubuntu-----version15.---recovery

MemoryTest----
MemoryTest---

I tried login using installing usb drive with option "Try Ubuntu without installing" and using bot repair utility i got following  

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 30478 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3.7 GiB, 4004511744 bytes, 7821312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             32     7,821,311     7,821,280   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1C1A-3B4C                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 23 09:03 ata-TSSTcorp_CDDVDW_SH-222AB_R8F26GAB803288 -> ../../sr0
lrwxrwxrwx 1 root root  9 Oct 23 09:47 usb-SanDisk_Cruzer_Blade_20060877201696211CDE-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 23 09:47 usb-SanDisk_Cruzer_Blade_20060877201696211CDE-0:0-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5029/mounts) leaked on lvs invocation. Parent PID 9699: bash
File descriptor 63 (pipe:[64146]) leaked on lvs invocation. Parent PID 9699: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-10-23__09h47 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in live-session (Ubuntu 15.04, vivid, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash --- BOOT_IMAGE=/casper/vmlinuz.efi
ls: cannot access /home/usr/.config: No such file or directory

=================== os-prober:


=================== blkid:
/dev/sda1: LABEL="UUI" UUID="1C1A-3B4C" TYPE="vfat"
/dev/loop0: TYPE="squashfs"


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sda: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  4005MB  4004MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:4005MB:scsi:512:512:msdos:SanDisk Cruzer Blade:;
1:16.4kB:4005MB:4004MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE    SIZE LABEL MODEL            UUID
sda   disk           3.7G       Cruzer Blade
sda1  part vfat      3.7G UUI                    1C1A-3B4C
sr0   rom           1024M       CDDVDW SH-222AB
loop0 loop squashfs    1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  1 running
sda1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=1006864k,nr_inodes=251716,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=203824k,mode=755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=34,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=203824k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet hugepages i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vfio vga_arbiter vhci vhost-net xconsole zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  984M     0  984M   0% /dev
tmpfs          tmpfs     200M  9.0M  191M   5% /run
/dev/sda1      vfat      3.8G  1.1G  2.7G  29% /cdrom
/dev/loop0     squashfs  1.1G  1.1G     0 100% /rofs
/cow           overlay   996M   98M  899M  10% /
tmpfs          tmpfs     996M   84K  996M   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     996M     0  996M   0% /sys/fs/cgroup
tmpfs          tmpfs     996M  1.2M  995M   1% /tmp
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     200M   68K  199M   1% /run/user/999

=================== fdisk -l:

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 3.7 GiB, 4004511744 bytes, 7821312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *       32 7821311 7821280  3.7G  c W95 FAT32 (LBA)


Error: no partitions
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems
```



should i go for re installation or how do i repair existing installation
[/INDENT]

HDD

---

### Post by yancek on 2015-10-23
Your boot repair output does not show any internal drive.  All the information is in regard to your 4GB Sandisk flash drive.  So if you have a hard drive it is not being detected.  I would first check the BIOS to see if it is detected there.  Also, check to see if it is securely attached which will necessitate opening the box.  Drive might be dead?

---

### Post by HDD on 2015-10-23
I have checked the BIOS it is detected there,and when occasionally i was able to login i checked it with the tools available there was no problem in the disk,i have already checked the wires they are OK

---

### Post by HDD on 2015-10-24
Hi 
after replacing the Hard Disk cable "read Error" is sorted out,now there are two things

1,While booting the customary ubuntu screen does not come up  the screen shows folowing

 Starting Version 219
 Welcome to Emergency Mode
after logging in,type "journalctl-xb" to view system logs(I have not tried this option yet),"systemctl reboot" to reboot,"systemctl default" or ^D boot into default mode
root@(systemName):*#

2.After logging in and reaching the desktop if i try to "Restart" system following message shows up repeatedly

Some Number-------INFO:task(agetty):782 blocked for more than 120 seconds
Some Number------Not tainted 3-19.0-30 generic#34-Ubuntu
Some Number------echo 0>/proc/sys/kernel/hung-task_timeout_secs"disables this message

this message repeats itself untill i press cntrl-alt-delete

---

