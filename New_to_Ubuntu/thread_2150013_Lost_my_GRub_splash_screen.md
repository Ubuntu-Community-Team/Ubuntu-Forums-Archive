---
title: "Lost my GRub splash screen"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by Ridgerunrbunny on 2013-05-30
I have a triple boot os, windows, hackintosh, and ubuntu. Recently upgraded to 12 point what ever it is and the splash screen was there. All of a sudden it disappears. Don't ask me when or why, it's just not there. Goes from push the button right into ubuntu bypassing the choices screen. Asked sudo what was up and sudo said everything is fine, it's all there. uh huh. OKay so whata ya suggest?
I use things in every OS just not all the time. Please be gentle, I'm pushing 70 and can barely remember the dogs names much less all this computer stuff. 

Bunny

---

### Post by newb85 on 2013-05-30
What is the output of 
```
 cat /boot/grub/grub.cfg 
```

---

### Post by newb85 on 2013-05-30
Edit: Hmm... actually, it would be more helpful if you gave the output of
```
cat /etc/default/grub
```

instead

---

### Post by grahammechanical on 2013-05-30
There is usually a default 10 second delay until Grub boots into the OS at the top of the menu list. Set the delay to zero and we lose the Grub menu. Press Shift while the machine is loading and the Grub boot menu should appear and you can make your selection.

To put that delay back in you will have to edit a Grub configuration file. Are you the only person using this machine? Does someone else have administrator privileges? Who changed the default setting?

If you do look in /etc/default/grub you should see this

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

but if you see this

> GRUB_TIMEOUT=0

Then that is what you need to change but you need to edit the file with administrator privileges. Note this comment

> # If you change this file, run 'update-grub' afterwards to update

Otherwise, nothing will change.



Regards.

---

### Post by Ridgerunrbunny on 2013-05-31
It's exactly as you have it. I'll try the shift. I'll be back. Thank you in advance.

---

### Post by Ridgerunrbunny on 2013-05-31
Nope. No menu. Black screen says grub loading hdo4 ext3.

---

### Post by kinglear333 on 2013-05-31
Like @grahammechanical said, you need to change that file with admin priviledges. Your login in Ubuntu does not have admin priviledges, I believe.

Try to first "sudo -s" into root and then modify the grub.conf file. After modifying, run "upgrade-grub" or "upgrade-grub2" and reboot.

Btw, the TIMEOUT value should be greater than 0 as it denotes the amount of time Grub should wait before proceeding with the boot process.

---

### Post by Ridgerunrbunny on 2013-05-31
This is what is in there:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
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

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]Ridgerunrbunny; Hi !

Have you got five hard drives in that box ? (hd"?"4) indicates so ??? 
If so, Have you changed the boot priorities in your bios setup ?
and yeah looks like it is time to do as Mr.(?)[/COLOR][COLOR=#000000]newb85 initially indicated:
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cat /boot/grub/grub.cfg[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

This be small steps, and one at a time, but we get there[/FONT][/COLOR]

---

### Post by Ridgerunrbunny on 2013-06-01
No, I have 3 hard drives. The one referenced is partition. I have many partitions. Each hard drive has at least one storage for the OS installed.
This problem has nothing to do with the bios. I have lost my grub splash screen.  I don't know what happened to the remainder of my post but the Menu1st has no splash screen. So says sudo.
I wish I had the program I had before upgrade deleted it, the one that allowed me to change the boot time and choose the boot splash screen.


Here is one problem I just ran across: 

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=26bd3e73-a09f-4a82-8b95-53c35b7838c6

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

title		Ubuntu 12.04.2 LTS, kernel 3.5.0-23-generic
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.5.0-23-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro quiet splash 
initrd		/boot/initrd.img-3.5.0-23-generic
quiet

title		Ubuntu 12.04.2 LTS, kernel 3.5.0-23-generic (recovery mode)
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.5.0-23-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro  single
initrd		/boot/initrd.img-3.5.0-23-generic

title		Ubuntu 12.04.2 LTS, kernel 3.2.0-43-generic
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.2.0-43-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro quiet splash 
initrd		/boot/initrd.img-3.2.0-43-generic
quiet

title		Ubuntu 12.04.2 LTS, kernel 3.2.0-43-generic (recovery mode)
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.2.0-43-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro  single
initrd		/boot/initrd.img-3.2.0-43-generic

title		Ubuntu 12.04.2 LTS, kernel 3.0.0-12-server
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.0.0-12-server root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro quiet splash 
initrd		/boot/initrd.img-3.0.0-12-server
quiet

title		Ubuntu 12.04.2 LTS, kernel 3.0.0-12-server (recovery mode)
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.0.0-12-server root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro  single
initrd		/boot/initrd.img-3.0.0-12-server

title		Ubuntu 12.04.2 LTS, kernel 3.0.0-12-generic
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro quiet splash 
initrd		/boot/initrd.img-3.0.0-12-generic
quiet

title		Ubuntu 12.04.2 LTS, kernel 3.0.0-12-generic (recovery mode)
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro  single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 12.04.2 LTS, kernel 2.6.38-8-generic
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic
quiet

title		Ubuntu 12.04.2 LTS, kernel 2.6.38-8-generic (recovery mode)
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=26bd3e73-a09f-4a82-8b95-53c35b7838c6 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/grub/core.img

title		Ubuntu 12.04.2 LTS, memtest86+
uuid		26bd3e73-a09f-4a82-8b95-53c35b7838c6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



This does not show my windows partition nor my Mac partition and has multiple kernels. Grub is certainly confused.

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]Ridgerunrbunny; Hey ....

I may be out in left field -> but that last out put looks to me to be old "grub" even prior to the grub legacy" . It has been my experience that getting old/version new/version is a trial to get to "play" nicely together.  Don't even want to go there unless there is no other recourse,

What to do, what to do......OK, for starters let's see what your system setup is like.
```
sudo fdisk -lu
sudo blkid
```
How many operating systems do you have installed and where ? Which do you want as the "primary" operating system ?
Show the output - from each operating system - of :
```
sudo grub-install -v
``` so we know what versions of grub we are relating with.

And then let's look at possible changes you have made to the boot process - from your "primary" operating system:
```
ls -la /etc/grub.d/
``` to indicate where to look at next.

Here is  most excellent guides for starters on grub that are fairly up-to-date for your info as to what is happening:
[/COLOR][http://www.dedoimedo.com/computers/grub-2.html#mozTocId703454](http://www.dedoimedo.com/computers/grub-2.html#mozTocId703454)
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)[COLOR=#000000]
[/COLOR][https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)[INDENT]
we be look'n

[/INDENT]

---

### Post by Ridgerunrbunny on 2013-06-02
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c22e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   390967246   195483592   af  HFS / HFS+
/dev/sda2       390967290   781934473   195483592   af  HFS / HFS+
/dev/sda3       781934517  1101728684   159897084    b  W95 FAT32
/dev/sda4      1101737698  1953520064   425891183+   5  Extended
/dev/sda5   *  1101737700  1312365914   105314107+  83  Linux
/dev/sda6      1312365978  1574139903   130886963   83  Linux
/dev/sda7      1929759993  1953520064    11880036   82  Linux swap / Solaris
/dev/sda8      1574141952  1929758719   177808384   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   151569085    75784511+   7  HPFS/NTFS/exFAT
/dev/sdb2       151570430   234420479    41425025    f  W95 Ext'd (LBA)
/dev/sdb5       225279558   234420479     4570461   82  Linux swap / Solaris
/dev/sdb6       151570432   216891391    32660480   83  Linux
/dev/sdb7       216893440   225277951     4192256   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa3d6e76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     7903979     3951958+  83  Linux
/dev/sdc2         7903980   241264169   116680095    b  W95 FAT32
/dev/sdc3       241264170   488392064   123563947+   7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$

---

### Post by Ridgerunrbunny on 2013-06-02
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="c85ad425-2847-3d81-b3b9-0ef4a50c5ce3" LABEL="OS X" TYPE="hfsplus" 
/dev/sda2: LABEL="Storage" UUID="329B-5005" TYPE="vfat" 
/dev/sda3: LABEL="WIN XP" UUID="851D-15DB" TYPE="vfat" 
/dev/sda5: UUID="179d3c61-d787-4de8-a70d-3d4e260aca8b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="4ac69a6d-5e97-4430-8d6b-8cb332a8c8e7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="3fdc1590-85b8-4ce8-b78f-a3f9eb61d4ce" TYPE="swap" 
/dev/sda8: UUID="2cf70372-7584-4887-a09b-483fe4f56fe0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS amd64" TYPE="iso9660" 
/dev/sdb1: UUID="E2E46ABAE46A9099" TYPE="ntfs" 
/dev/sdb5: UUID="be33b168-3376-4e7e-8b90-cd995de46944" TYPE="swap" 
/dev/sdb6: UUID="a5996bde-f901-47ee-962e-30868166cd53" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="172cbd08-b49c-4e8f-9ce0-09d98cfd5cda" TYPE="swap" 
/dev/sdc1: UUID="ebcd636d-fcde-407c-b240-a4079d615c70" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: UUID="41BA-14D1" TYPE="vfat" 
/dev/sdc3: UUID="73EC56972CF589C2" TYPE="ntfs" 
ubuntu@ubuntu:~$

---

### Post by Ridgerunrbunny on 2013-06-02
ubuntu@ubuntu:~$ sudo grub-install -v
grub-install (GRUB) 1.99-21ubuntu3
ubuntu@ubuntu:~$

---

### Post by Ridgerunrbunny on 2013-06-02
ubuntu@ubuntu:~$ ls -la /etc/grub.d/
total 38
drwxr-xr-x 2 root root  180 Apr 25  2012 .
drwxr-xr-x 1 root root  580 Jun  2 13:22 ..
-rwxr-xr-x 1 root root 6715 Apr 17  2012 00_header
-rwxr-xr-x 1 root root 5522 Apr 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7399 Apr 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17  2012 40_custom
-rwxr-xr-x 1 root root   95 Apr 17  2012 41_custom
-rw-r--r-- 1 root root  483 Apr 17  2012 README
ubuntu@ubuntu:~$

---

### Post by Ridgerunrbunny on 2013-06-02
I tried to reinstall ubuntu this A.M. all I get is an error 15.  sorry for all the reply's.
Bunny

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]Ridgerunrbunny'

Let me get caught up on other things - to focus properly on this - and update this status .. and I get back with ya,
Mean while ...check and make sure in bios that the boot priority is set to boot from the hard disk containing your primary operating system.
[/COLOR][INDENT=2][COLOR=#000000]
'till I get back[/COLOR][/INDENT]

---

### Post by Ridgerunrbunny on 2013-06-02
that is the first thing I check.  I have no doubt I duplicate boots and the os is confused. I went through each and every partition and reinstalled and formated and still got error 15. The media it is attempting to boot is unknown to me, I don't recognize the number.

---

### Post by Bashing-om on 2013-06-02
bunny ; I am back.

I have a good notion of how to proceed. First though see my last,,, FYI I have just recently got my grub working triple booting. # weeks of going a-round and around with getting it to work properly. after a clean install of 13.04. I was not able to get grub to install properly, thought finally that my Master Boot Record must have been corrupted being unable to generate a device.map file for grub to use.
A colleague suggested I change my bios booting order - for years I had thought my boot priority was my first hard drive, ran this system for years with no apparent problem ..till that new install over an existing install - and changing my boot priority resolved all my issues // 3 weeks of chasing my tail !
-------------
To the issue at hand:
I see that the first hard drive should be your Primary operating system;
I suggest that "grub" be your only boot loader, as it will load any operating system.
As a linux distro is installed on all 3 drives, we want grub installed to the MBR of each drive and focus on getting the first drive (sda) to boot. Grub is highly customize able, once one knows how; we should be able to change the menu presentations at a later time to meet your expectations.
--------
1. What version of linux do you presently have installed on that first hard drive ? 
2. Can you now boot up to any linux operating system - the only system I care to work with/from - installed on your hard drives ?
3. (re-)installing, not known at this time the state of the old install -> need to have a look at your partitions from liveDVD in ubuntu's GParted utility in order to proceed further.

Booting from an install involves one process;
Booting from a liveDVD involves an altered process to achieve installation of grub onto the hard disk.

Once we have grub installed on each drive we can chainload the other operating systems to boot from ubuntu grub. That is the way I see it.... You got a different thought ? It is your system, we will do it the way you want to.[INDENT=2]
with all due respect

[/INDENT]

---

### Post by Ridgerunrbunny on 2013-06-02
My Tbite has Mac and Ubuntu on it. There is a Mac storage partition. Ubuntu has home, root and usr in separate partitions. There is a 250 G where I have NTFS and linux storage. Then there is a small windows partition. I don't use windows much anymore but I don't mess with that partition as it contains valued videos I produced once upon a time, ditto any ntfs storage areas. I only use Ubuntu or have for the last several years. I've tried most of them. 12.04 is installed. I'll bet the MBR in windows is messed up but for the life of me I cannot recall where the dam thing was located to go see. I don't think I have looked at it for 10 years. Gettin late, shuttin down.

---

### Post by Bashing-om on 2013-06-02
bunny;
I do NOT anticipate any problems using grub to "chainload" windows to enable booting windows;
I "hope" there is no problems doing the same for the Mac install.. I personally have not touched a Mac system in way too many years past;

Error 15, I have heard of such a thing ..but I don't know ..would have to research ..will do if needed.

(re-)install is a means of last resort, I hope the installer had not started, and the initial installation remains intact.

A quick looksee..to look at current disks partitioning =>
boot the liveDVD -> "try ubuntu" mode
Key combo ctl+alt+t yields a terminal: enter terminal codes:
```
sudo fdisk -lu
sudo parted /dev/sda unit s print

``` "assuming" that -sda- is the primary booting disk AND that the ubuntu to be booted is on sda5.

As an aside, I had meant to comment earlier, that I see where that "old" grub code I was pointing out originated from. We will have to deal with that prior to updating the grub installation- I need to keep that in mind ![INDENT=2]
good night, we pick this up in your time. [/INDENT]

---

### Post by Ridgerunrbunny on 2013-06-03
reinstall was over and done. I place all personal stuff in a separate partition and any installs only require minimal redoing. I threw an old copy of super grub in the dvd/cd and booted from sdc completely not shown in sudo as containing the boot loader. I am very frustrated about that and sitting here with 3 separate computers. Writing this from my laptop. Just put away an old windows 95 trying to find the mbr there. (no luck, no remember) Looking at desktop to my left with god only knows what in it/on it.  Seriously considering formatting all the linux partitions, resizing and upgrading to 13.04.  Is it any good? the Error 15 means grub is not recognizing the mbr. Learned this earlier and tried all the web's advice on it to no avail.  I have learned not all advice works on all computers as claimed.

---

### Post by Bashing-om on 2013-06-03
bunny, My goodafternoon to ya.

I understand your frustration with grub booting,, as I have just came out of that situation.
My experience, I installed 13.04 as a MINIMAL install and from that very very minimal I am building the current system I am operating from. I am very happy with what I have put together. - and continue to add to only what I want on this system.
Now case at hand.... let us start all over fresh as it it getting confusing keeping up with what is/ what if/ what may be ...
to that end, here is how triple booting with installing that 3rd operating system (speaking from recent experience):

Grub is installed to the MBR on the hard drives containing a linux install
When 13.04 is installed it becomes by default the PRIMARY operating system, which ever hard drive this new install is installed onto requires that the bios boot priority be set in accordance.
Now on the first boot-up into the new install -> make this primary grub aware of all the operating systems on all the disk and all these partitions with the terminal command:
```
sudo update-grub
```
this command initiates several scripts, among which is "os-prober" which finds ALL the operating systems and the boot menu gets built...

now go back into each "linux" install - is what I did - and run "sudo update-grub"
revert back to the new install that is the primary install and run "sudo update-grub" once more to insure that any changes to the grubs on the other installs are picked up and the adjustments are made on this primary install.

For now, make sure that the file "[COLOR=#000000]-rwxr-xr-x 1 root root 6335 Apr 17 2012 20_linux_xen" located at /boot/grub.d/ from which ever install it existed at, is no longer in existence -or- it has been marked as non-executable. In order for grub2 (the current grub version) to operate that file must not be executed.

In respect to documentation: It will drive one insane ! I have learned that one has to differentiate old info from new.
reason: linux/ubuntu is evolving at a tremendous rate, in this process many things change at the operating level.
Introduction of grub from lilo as a bootloader - big change
introduction of upstart from sysV for startup - big change
introduction of grub1 from grub(legacy - as now known)  - big change
Now comes UNITY - huge change
then introduction of grub2 ....more change
 
this is but a few of the growth spurts !  So what I am relating is one has to discriminate with the huge amounts of documentation that is available, how and what it applies to and where. Thousands of programmers are constantly the world over reworking this code, and providing the documentation on what has been done. The ONLY resource that attempts to only keep relevant info to what is current is ubuntuforums... and that effort is still in infancy --any and all help is desired and appreciated [see the link in my sig]

Off my soap box now and attention on your present situation.

With the above in mind, remind me of your current status of installed systems and what/how you intend to install the new operating system. ("sudo fdisk -lu" works great)
[/COLOR][INDENT=2][COLOR=#000000]
I am trying to help

[/COLOR][/INDENT]

---

### Post by Ridgerunrbunny on 2013-06-04
When you say installed systems, do you mean upgrades of ubuntu? Other than the windows and mac partitions that is all I would have. Ubuntu since 8 something. I keep /home the same no matter what, without formatting. This saves all my programing or maybe I should say goodies.  Windows mbr can be corrupted and I have experienced this causing problems. For some reason or another neither my laptop nor desktop would recognize burning a 13.04 on a dvd so I had to have significant other burn it on his Windows computer.  What does sudo fdisk -lu list? Will be getting to that later today.

---

### Post by Bashing-om on 2013-06-04
Bunny, Hi ...

We want to know what is installed and where/what on each partition on your system and the command "fdisk"  relates a lot of details.
Here is Cavsfan's advice on a means to "keep track" of what is on what partition. Believe me it does help !
 > 
Labelling the partitions
When you install a 2nd Ubuntu for example, it will install that Ubuntu's version of Grub and that will be the one that displays. 
If you wish to use the Grub on another Ubuntu, boot into that system and in Terminal enter 
sudo grub-install /dev/sdx where x is a, b or which ever hard drive it is installed on. sudo blkid will tell if you don't know.


Also, labelling your partitions makes things a lot easier as you can tell by the sudo blkid above. 
Not only do they display in terminal, they display as labelled in Ubuntu, which makes it a lot easier than perhaps displaying a UUID. 
Here is the command to label your partitions: 
sudo tune2fs -L "Precise" /dev/sda5 
sudo tune2fs -L "Quantal" /dev/sda6 
sudo tune2fs -L "Raring" /dev/sda8 


Example: sudo tune2fs -L {label} {devicename} 


Just change the sdax to match your partition. 
You do not need to label anything other than ext4 file systems.

Here is what my system looks like, easily identified what I have where:
> 
sysop@1304mini:~$ sudo blkid
/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1304mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1304mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1304mini:~$


Also see the "manual" for full disclosure: Terminal command:
```
man fdisk
man blkid

```

What happens many times in installing ubuntu's grub, it gets installed ontop of Window's Boot code - wiping Windows' code out - IF "update-grub" is not ran in a timely manner, that code can be lost. - one has to be aware of what is installed where ! as well as have a plan on how they intend to boot in a multi-system environment- 
Now that is what we are working on getting the bootloader (grub) installed properly in accordance with what is set in bios for the primary boot device.

There exist many "bootloaders" I always see that "grub" is the more recommended "bootloader" mostly due to it's versatility. Grub is the one that I am more familiar with, and what I work with.

Once we know were "root" is for each instance of "linux"('buntu) and what drive is primary, we can determine where to install grub and in what order, to the final goal to boot any of the operating systems or versions that are on your system.

**I hope I am clear with my explanations...advise is welcome so that we are "on the same page" to get you booting.[INDENT=3]
regards
 [/INDENT]

---

### Post by Ridgerunrbunny on 2013-06-05
My bios can be adapted to IDE or sata (ide compatible) I can choose any hard drive or device as priority boot device. None of them works to boot linux. I got into windows yesterday but I think it fixed the mbr there when I used super grub to enter.  Once in there I located the boot and there were about a dozen boot updates which I have not had a chance to look at.  I have 13.04 on a stick and am looking at that on the desktop at present. I checked each and every partition, save mac, to try and locate the primary. To no avail, there are boot/grub folders in each partition but mostly all of them are blank except the one that I designate as boot.  I decided to back up home somewhere and format the linux parts and reinstall the new version. I'm not into doing this much work and I don't even know if formating will work either, nothing seems to. I keep eyeballing windows, it is usually the culpert.
bunny

---

### Post by Ridgerunrbunny on 2013-06-05
Oh this is cute. I went into the bios on boot up set everything to boot the sata drive where ubuntu is continued, windows opened. shut down. removed the stick, went into the bios and WHAT? the hard disk  drives were changed back to have the IDE boot first. Windows is controlling my bios, what the frack? I've had windows fudge with the bios before but this is really new. Went back into bios and disabled the ide drives to boot ubuntu disk.

---

### Post by Ridgerunrbunny on 2013-06-05
Did a fresh install of 13.04.  I had some of what I had backed up but not everything. What I thought was going into the home folder wasn't so I lost a lot of cutsie stuff, oh well, never used them anyway.  After all is said and done, I think the original grub was in the beginning of the hda, which just didn't make any sense to me at the time of frustration because the beginning of hda contains Mac and I never, never touch Mac, ever.  Both Windows and Mac remain unscathed. I did delete a lot of boot logs from the windows partition.  I sure thank you for your help, now to go and clean up the leftover mess, and reinstall a few programs I liked. By the way we are in S.E. Missouri, I noticed you were from Ark. 

A neighbor.

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]Ridgerunrbunny; Hey ;

Sounds like you ARE making good progress.

Keep in mind, simpler is better; maybe only one grub install on the primary hard drive, removing all others grubs.
If you can boot the primary ubuntu, remove all traces of grub on one of the other installs, re-boot into the primary and update grub's grub.cfg files;

reboot and see if the primary grub has picked up the system that had grub removed ??? If so, repeat untill you are at simplest terms:
1 grub booting all the linux installs, Windows and Mac.
In theory That should work. I have not tried it as I want to be able to boot up any of my installs independently of any other... I mess about a lot and it does happen that I mess things up to the point I can not boot the OS I just messed up. I want to have quick access to another OS; so I have grub installed to the MBR of each linux install drive. For me in my applications this arrangement works great. I have grub set to boot as default my primary OS that is also bios' 1st boot priority. Changing the boot priority in bios, I can boot the OS on any of my drives.

If removing grub from one of the linux installs causes a bad "situation" one can always (re)install grub from another OS or a liveMeDium.

If this can be done to have only one grub controlling the booting of all operating systems, sure would simplify things !
[/COLOR][INDENT=2][COLOR=#000000]
it's ubuntu, where there is a will, there is a way

[/COLOR][/INDENT]

---

### Post by Isamu715 on 2013-06-06
This looks like a GRUB Legacy *menu.lst* instead of the current GRUB's *grub.cfg*. It seems that menu hiding is enabled:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
Put a # before the *hiddenmenu* line and see if it fixes your issue. It should look like this:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
It's still strange that you're not using GRUB2.

---

