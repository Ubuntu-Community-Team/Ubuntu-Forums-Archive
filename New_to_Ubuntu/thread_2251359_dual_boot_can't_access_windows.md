---
title: "dual boot can't access windows"
date: 2014-11-03
forum: New to Ubuntu
---

### Post by kicma on 2014-11-03
I installed Ubuntu 14.04.1 LTS on a PC with Windows 7 and now I can't enter windows any more. Windows are on SSD and Ubuntu on HDD. Please tell me what else info do I need to provide for you to help me.
[h=2][/h]

---

### Post by oldfred on 2014-11-03
First try this in terminal in Ubuntu:
sudo update-grub

If that does not work is this a new system that may have both UEFI & BIOS boot modes and you did not install in same boot mode.

Post this: 
sudo fdisk -lu
sudo parted -l

---

### Post by kicma on 2014-11-04
sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51270004

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   117227519    58510336    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7b1be85

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   782372497   391185225    7  HPFS/NTFS/exFAT
/dev/sdb2       782372862   976771071    97199105    5  Extended
/dev/sdb5       897515520   960112639    31298560   83  Linux
/dev/sdb6       960114688   976771071     8328192   82  Linux swap / Solaris
/dev/sdb7       782372864   897515519    57571328   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a4e3a4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064     7935999     3963968    b  W95 FAT32

sudo parted -l

Model: ATA Corsair Force LS (scsi)
Disk /dev/sda: 60,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   60,0GB  59,9GB  primary  ntfs


Model: ATA ST500DM005 HD502 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  401GB  401GB   primary   ntfs            boot
 2      401GB   500GB  99,5GB  extended
 7      401GB   460GB  59,0GB  logical   ext4
 5      460GB   492GB  32,0GB  logical   ext4
 6      492GB   500GB  8528MB  logical   linux-swap(v1)


Model: TOSHIBA TransMemory (scsi)
Disk /dev/sdc: 4063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  4063MB  4059MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by oldfred on 2014-11-04
Standard BIOS boot with MBR(msdos) partitioning on both drives.

When you installed did you install grub to the hard drive seen as sdb? You only get that option with Something Else or manual install. If so you should still have the Windows boot loader in sda, the SSD and can select it with one time boot key or from BIOS.

You can reinstall a Windows boot loader to sda, and reinstall grub boot laoder to sdb with Boot-Repair. Do  not use its auto fix as that just installs grub to every drive. In advanced you can choose system and drive to install boot loader. Then set BIOS to boot hard drive or grub/Ubuntu.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If still issues post the link to the summary report from Boot-Repair.

---

### Post by kicma on 2014-11-04
I have UEFI, not BIOS. Boot-Repair didn't help me, don't know what I'm doing wrong.

[http://paste.ubuntu.com/8820266/](http://paste.ubuntu.com/8820266/)

---

### Post by d4m1r on 2014-11-04
Which operating system did you install first?

I assume you had Windows 7 already on your **desktop PC** and then using a DVD you wanted to install Ubuntu on it as well?

During the installation process, Ubuntu asks how you want to install it....It asks if it is the only OS or if there is Windows (or something else) already installed before it begins...

Do you remember what you selected at that screen? Ubuntu is intuitive to get a dual boot scenario going in 99.99% of cases (unlike Windows 7 installer), but only if you slow read and read the messages along the way :)

---

### Post by kicma on 2014-11-04
Yes I had Windows first. I don't remember...Should I reinstall? How do I do that?

---

### Post by oldfred on 2014-11-04
You may have newer system that is UEFI, but both Windows & Ubuntu are on MBR drives.
Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR drives with BIOS/CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

If system is both UEFI & BIOS, then how you boot installer is how it installs. 

You also show a wubi install in sdb and grub4dos files in sda, which is usually used by EasyBCD.

But you have grub installed to the MBR of both drives. Best to keep grub on sdb, but install a Windows boot loader to sda.

If you select sdb to boot from, does not Ubuntu boot?
And grub shows both sda1 & sda2 as boot options. Boot-Repair usually copies bootmgr to main Windows install to give another way to boot as many users delete the 100MB boot not realizing it is essential. But then grub2's os-prober finds both partitions as boot able.

But I would still use Advanced mode in Boot-Repair, Select Windows and the Windows drive to install a Windows type boot loader. Then you can boot with grub from sda and if issues with grub still use one time boot key to directly boot Windows from sda.

Best to remove the grub4dos and related info. With two drives that is not required.

---

### Post by kicma on 2014-11-04
When I open boot repair I have following options:

GRUB location - OS to boot by default 
sdb5(The OS now in use - Ubuntu 14.04.1 LTS)
sdb7( Ubuntu 14.04.1 LTS)
Windows (via sdb5 menu)

Place GRUB:
sdb
sda
sdc

You say install a Windows boot loader to sda, how do I do that? No matter what I choose I can't enter Windows.

---

### Post by yancek on 2014-11-04
If you use UEFI, an EFI partition is created and usually the windows and Ubuntu boot files for efi are on that partition.  You may have a UEFI capable computer but there is no sign in the boot repair output of an EFI partition nor are there any efi files for windows or Ubuntu.  It also appears you installed Ubuntu twice(?) on sdb5 and sdb7.  Not sure if you meant to do that?   When you set sdb, the second drive to first boot priority in the BIOS, are you able to boot Ubuntu (asked above).  If you can that will make it a lot easier.

---

### Post by kicma on 2014-11-04
In BIOS I can choose to boot from SSD and HDD and from both I enter Ubuntu.

---

### Post by oldfred on 2014-11-04
That is because you have grub installed to the MBR of both drives.

But can you boot Windows from grub menu?

---

### Post by kicma on 2014-11-04
This may be stupid question, but how do I enter grub menu? I tried pressing shift but no success.

---

### Post by yancek on 2014-11-04
Do you see a boot menu with different options for Ubuntu or does it just boot directly to Ubuntu?  If you see a number of entries for Ubuntu, use the down arrow key to get to the end of the menu.  You have entries for windows in your grub.cfg file on both sda5 and sda7 so it should show.  If you don't see a menu on boot for Ubuntu, that's a different problem.

---

### Post by kicma on 2014-11-05
I don't see menu, it just boots directly to Ubuntu.

---

### Post by oldfred on 2014-11-05
To get menu, you have to hold shift key from BIOS until menu appears. If UEFI (which you are not booting with) then you press escape key.

In Ubuntu run this first from terminal.
sudo update-grub

Does it show Windows as last or near last entry in update. then it should be at bottom of menu.
If not it may mean it cannot see the Windows partition correctly. Grub only boots working Windows and you may need your Windows repair CD or install DVD, or flash drive.

Did you choose Windows in Boot-Repair and install it to sda? 

Post summary report and we may be able to see what issue is, but Boot-Repair can only do very minor repairs to Windows & NTFS.

---

### Post by kicma on 2014-11-05
I can't enter boot menu by holding shift or pressing escape.
sudo update-grub shows this

sudo update Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 14.04.1 LTS (14.04) on /dev/sdb5
done

and after choosing Windows and sda this is report 
[http://paste.ubuntu.com/8843103/](http://paste.ubuntu.com/8843103/)

---

### Post by oldfred on 2014-11-05
You show two Windows boot entries. 

Boot-Repair copies the bootmfg file into the main partition as a backup. Too many users deleted the Windows 100MB boot partition as they did not know what it was.
But now grub2's os-prober sees both partitions with boot files and will offer to boot from either.

With grub seeing more than just Ubuntu you should automatically get grub menu.

Or did you change grub configuration to totally hide menu or timeouts to zero so menu will not show?

Post this:
       cat /etc/default/grub

---

### Post by kicma on 2014-11-05
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by oldfred on 2014-11-06
Your grub.cfg looks standard and should work.

I did just see in another thread where they changed this:
GRUB_HIDDEN_TIMEOUT_QUIET=true

 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub

Change to =false
and run 
sudo update-grub

---

### Post by kicma on 2014-11-06
I tried that now but no improvement.

---

### Post by oldfred on 2014-11-06
As soon as BIOS is done, press down arrow 7 times. Grub sees presses and Windows is 7th setting.

Did you reinstall a Windows boot loader to sda with Boot-Repair?
Then can you boot from one time boot key.

You can also use Windows repairCD or flash drive to run a Windows repair and it will install a new Windows boot loader to your sda drive. You may have to run Windows repairs 3 times. or manually run fixMBR from command line in Windows repair.

You can also manually install other boot loaders to sda that work just like Windows. Boot-Repair uses syslinux, but you also can use lilo but with both you only want the part that is in MBR as Windows has to have its boot code in the Windows partition.

You also still have grub4dos in Windows and wubi. You need to update the BCD to fix entries in BCD and remove wubi. Make sure you have backed up any data in wubi first.

You want grub2's boot loader only in sdb.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by kicma on 2014-11-08
Ok I managed to get into windows by pressing arrow 5 times. Thank you for your help

---

