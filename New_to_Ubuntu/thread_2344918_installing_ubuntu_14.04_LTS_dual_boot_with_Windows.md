---
title: "installing ubuntu 14.04 LTS dual boot with Windows 7"
date: 2016-11-29
forum: New to Ubuntu
---

### Post by ahmed11ber on 2016-11-29
Hi

I am installing ubuntu 14.04 LTS dual boot with ;y windows 7. I have an HP pavillion g6 RAM 4GB and DD 500GB but I have encouter severals problems when installing.
1- the grub does t start after installing. its starts directly on ubuntu
2-  When I issue the command sudo fdisk -l its give a partition problem from a live cd

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd5f2444c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      131071       64512    7  HPFS/NTFS/exFAT
/dev/sda2          131072   294088703   146978816    7  HPFS/NTFS/exFAT
/dev/sda3       294088704   703698943   204805120    7  HPFS/NTFS/exFAT
/dev/sda4       703700991   976771071   136535040+   f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       703700992   762292223    29295616   83  Linux
/dev/sda6       762294272   770105343     3905536   82  Linux swap / Solaris
/dev/sda7       770107392   976771071   103331840   83  Linux

Please. can some one give me an assistance to terminate the process of installation. Thanks a lot.

---

### Post by ahmed11ber on 2016-11-29
In addition when i saw the partition table it give this results from a live CD

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  67.1MB  66.1MB  primary   ntfs            boot
 2      67.1MB  151GB   151GB   primary   ntfs
 3      151GB   360GB   210GB   primary   ntfs
 4      360GB   500GB   140GB   extended                  lba
 5      360GB   390GB   30.0GB  logical   ext4
 6      390GB   394GB   3999MB  logical   linux-swap(v1)
 7      394GB   500GB   106GB   logical   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by Mark Phelps on 2016-11-29
If GRUB does not know about the presence of any other OSs, it defaults to booting directly into Ubuntu.

To tell GRUB about the other OSs, boot into Ubuntu, open a terminal, and enter "sudo update-grub" (without the quotes).

Then watch as it scans for the other OSs.

If this works, when you reboot, you will be presented with a GRUB menu with entries for Windows and Ubuntu.

Good Luck

---

### Post by kingneutron on 2016-11-29
--I would highly recommend installing the grub-customizer package, it gives you a lot of options for booting.

[https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)

--However, long story short, you can edit /etc/default/grub - mine always shows the menu with a 7-second countdown and looks like this:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="7"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_CMDLINE_LINUX_DEFAULT="nosplash"

```

--Standard disclaimer, you should make a backup first of any file you edit ;-)
' cp -v /etc/default/grub /root '

---

