---
title: "auto-boot ubuntu"
date: 2019-06-11
forum: New to Ubuntu
---

### Post by Mike_Davey on 2019-06-11
Hi,

I've used linux in the past, but haven't been around in years. Just recently bought a mini pc to run as a Plex server, so now I'm back. The mini came with Win10 on it and I guess I don't really want to delete it. Anyway, I installed an M.2 SSD and cloned windows to it so that I can just disregard the embedded mmc drive. The clone worked fine and Win10 works fine. Then I installed Ubuntu 18.10 letting the installer make all choices except for the size of the Files and Ubuntu partitions. Install went great and everything in Ubuntu seems to work fine.

However, I want Ubuntu to be booted automatically. I'm fine with a timeout of 10 seconds, or whatever. It doesn't do this though, just sits on the grub2 page forever and I have to hit enter to load the os.

I did a bunch of searching, both here and internet wide and that led to grub-customizer. I installed grub-customizer and it shows that the first entry (Ubuntu) should boot after 10 seconds, but this does *not* happen. I also set the timeout style to "countdown" in grub-customizer and this also had no effect.

I'm looking for advice on what else to do to fix this if anyone has any ideas. 

Here's the output from sudo parted -l 

```
Model: ATA CT250MX500SSD4 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  134MB   134MB                      msftres
 2      135MB   240MB   105MB   fat32              boot, esp
 3      240MB   63.6GB  63.4GB  ntfs               msftdata           <----- this is Windows
 5      63.6GB  189GB   125GB   ext4                                      <----- this is the FIles partition
 6      189GB   249GB   60.3GB  ext4                                       <----- this is Ubuntu 
 4      249GB   250GB   732MB   ntfs               diag


Model: MMC DA4064 (sd/mmc)
Disk /dev/mmcblk0: 62.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16.8MB               Microsoft reserved partition  msftres
 3      123MB   61.8GB  61.7GB  ntfs         Basic data partition          msftdata
 4      61.8GB  62.5GB  734MB   ntfs         Basic data partition          hidden, diag


Error: /dev/mmcblk0boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mmcblk0boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
```

Thanks in advance,
Mike

---

### Post by Mike_Davey on 2019-06-11
Here's output from efibootmgr

```
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0006,0003,0004,0001,0002,0005,0000
Boot0000* Windows Boot Manager
Boot0001* Windows Boot Manager
Boot0002* UEFI: Built-in EFI Shell
Boot0003* UEFI: CT250MX500SSD4, Partition 2
Boot0004* Windows Boot Manager
Boot0005* Windows Boot Manager
Boot0006* ubuntu
```

---

### Post by Skaperen on 2019-06-11
can you show us what you have in file [FONT=courier new]/etc/default/grub[/FONT]?  if it is too big, try this command:

```
[FONT=courier new]egrep -v '^#' /etc/default/grub|cat -s[/FONT]
```

---

### Post by Skaperen on 2019-06-11
please put contents of files and outputs or screens of commands between code tags.

---

### Post by Mike_Davey on 2019-06-11
Here's the grub output

```
GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="countdown"
GRUB_TIMEOUT="8"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_SAVEDEFAULT="false"
```

Here's the contents of the whole file 

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="countdown"
GRUB_TIMEOUT="8"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

GRUB_SAVEDEFAULT="false"
```

---

### Post by Mike_Davey on 2019-06-11
If I may ask another question that might fix this...I don't need two installs of Win10. I guess I wasn't sure if I could get everything running on Ubuntu since there's a NAS server involved and I'm not great at making linux do what I want, but everything works fine for Plex on Ubuntu. So, if I use gparted to just delete the Win10 install on the SSD, can I then just run a "sudo update-grub" and then all might be well? If so, should I do that from a live-booted-from-usb session?

Thanks again

---

### Post by oldfred on 2019-06-11
What brand/model system?
You show ubuntu as first entry in UEFI, but partition 2 as second. Have not seen that before.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Mike_Davey on 2019-06-12
I decided to just use the SSD for Ubuntu and if I need Win10 then it's still on the eMMC drive. So, I reformatted the SSD to a single partition and did a fresh install of Ubuntu. That seemed to go fine, but it still won't timeout and boot Ubuntu without user input. I did find a way around this, however. In grub-customizer, I unchecked "look for other operating systems" and now after the bios boot screen it shows a blank purple display for about 15 seconds and then boots into Ubuntu. I tried checking "look for other os" again and it reverts back to show the boot menu, but still won't time out. I guess this works as long as I can set it to boot without user input. I can always change it back to show the menu or just boot Win10 from the bios if I want to.

If either of you are curious, here's the current grub file--
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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

#GRUB_HIDDEN_TIMEOUT="0"
GRUB_DISABLE_OS_PROBER="true"
```

And here's the drive list--
```
Model: ATA CT250MX500SSD4 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                  Flags
 1      1049kB  180GB  180GB   ext4
 2      180GB   181GB  537MB   fat32        EFI System Partition  boot, esp
 3      181GB   250GB  69.5GB  ext4


Model: MMC DA4064 (sd/mmc)
Disk /dev/mmcblk0: 62.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16.8MB               Microsoft reserved partition  msftres
 3      123MB   61.8GB  61.7GB  ntfs         Basic data partition          msftdata
 4      61.8GB  62.5GB  734MB   ntfs         Basic data partition          hidden, diag


Error: /dev/mmcblk0boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mmcblk0boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
```

The system is a Pepper Jobs Mini PC. [URL="http://www.pepper-jobs.com/en/shop/product/glk-uc2x"]http://www.pepper-jobs.com/en/shop/product/glk-uc2x
[/URL]
Anyway, I have it working well enough that I can call it good, but if someone does know what the problem is, I'm happy to take your help and see if it can be setup properly.

Thanks, Mike

---

