---
title: "wifi on HP"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by chilimac02 on 2008-10-20
I've got an HP tx1203us it has a broadcom wifi card in it (A/B/G/N plus bluetooth). I can't get Ubuntu to recognize it. I imagine you guys will know what to do within one step...

---

### Post by shifty_powers on 2008-10-20
what version of ubuntu is it?

and what is the output of

```
lspci
```

?

---

### Post by chilimac02 on 2008-10-20
the command yielded:
justin@justin-linux:~$ sudo fdisk -1 
[sudo] password for justin:  
fdisk: invalid option -- '1' 
 
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
justin@justin-linux:~$ cat /boot/grub/menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8) 
#            grub-install(8), grub-floppy(8), 
#            grub-md5-crypt, /usr/share/doc/grub 
#            and /usr/share/doc/grub-doc/. 
 
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
#hiddenmenu 
 
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
# kopt=root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,6) 
 
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
 
title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro quiet splash  
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 
 
title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode) 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 
 
title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro quiet splash  
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 
 
title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode) 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro  single 
initrd		/boot/initrd.img-2.6.24-19-generic 
 
title		Ubuntu intrepid (development branch), memtest86+ 
root		(hd0,6) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
 
# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Windows Vista/Longhorn (loader) 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda3 
title		Windows Vista/Longhorn (loader) 
root		(hd0,2) 
savedefault 
makeactive 
chainloader	+1 
 
 
# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda5. 
title		Ubuntu hardy (development branch) (8.04) (on /dev/sda5) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-12-generic root=/dev/sda5  
savedefault 
boot 


I am using ubuntu 8.10

---

### Post by shifty_powers on 2008-10-20
erm, that was a completely different command ^.^

```
lspci
```  is what i was after...

---

### Post by chilimac02 on 2008-10-20
lspci yields:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)


sorry

---

### Post by shifty_powers on 2008-10-20
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

will help

follow the instructions and you should be able to get it working. used it before...

---

### Post by igknighted on 2008-10-20
BCM43xx is probably far too old for that chipset.  Broadcom has released a new, official driver for that card.  See this thread for details on how to use it on Hardy (8.04).  It is the default and automatically installed on the upcoming 8.10 (Intrepid), so if you are feeling adventurous you are welcome to try that out as well.

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

EDIT: Forget that link, you are already using intrepid (according to your grub.conf file).  Open System->Administration->Hardware Drivers and activate the Broadcom STA driver.  You should be good to go.

---

### Post by chilimac02 on 2008-10-22
thanks man - I just needed a fellow braves fan!!

---

