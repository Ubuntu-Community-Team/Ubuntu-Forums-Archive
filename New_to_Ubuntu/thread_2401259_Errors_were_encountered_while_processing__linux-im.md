---
title: "Errors were encountered while processing:  linux-image-4.15.0-1006-oem"
date: 2018-09-15
forum: New to Ubuntu
---

### Post by kevinkrmn on 2018-09-15
Hi all 
I'm not able to install any software and keep getting this error
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  python-appindicator python-gobject recordmydesktop
The following packages will be REMOVED
  linux-image-4.15.0-1006-oem
The following NEW packages will be installed
  gtk-recordmydesktop python-appindicator python-gobject recordmydesktop
0 to upgrade, 4 to newly install, 1 to remove and 0 not to upgrade.
5 not fully installed or removed.
Need to get 179 kB of archives.
After this operation, 7,309 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu bionic/universe amd64 recordmydesktop amd64 0.3.8.1+svn602-1ubuntu5 [47.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu bionic/universe amd64 gtk-recordmydesktop all 0.3.8-4.1ubuntu1 [121 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic/universe amd64 python-gobject all 3.26.1-2 [2,620 B]
Get:4 http://archive.ubuntu.com/ubuntu bionic/universe amd64 python-appindicator amd64 12.10.1+18.04.20180322.1-0ubuntu1 [7,820 B]
Fetched 179 kB in 1s (194 kB/s)                 
(Reading database ... 239181 files and directories currently installed.)
Removing linux-image-4.15.0-1006-oem (4.15.0-1006.9) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-1006-oem
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: usbhid.quirks=0x1B1C:0x1B09:0x0x20000408: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-4.15.0-1006-oem (--remove):
 installed linux-image-4.15.0-1006-oem package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-1006-oem
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I have already tried all solution suggested in the forum and other websites. 
Whatever command I run end with the same error.
here is output of  sudo dpkg --configure -a

```

Setting up linux-image-4.15.0-1018-oem (4.15.0-1018.21) ...
Processing triggers for man-db (2.8.3-2) ...
Setting up grub-pc (2.02-2ubuntu8.4) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: usbhid.quirks=0x1B1C:0x1B09:0x0x20000408: not found
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 127
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is not configured yet.


dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-gfxpayload-lists:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2); however:
  Package grub-pc is not configured yet.


dpkg: error processing package grub-gfxpayload-lists (--configure):
 dependency problems - leaving unconfigured
Processing triggers for linux-image-4.15.0-1018-oem (4.15.0-1018.21) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-1018-oem
/etc/kernel/postinst.d/zz-update-grub:
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: usbhid.quirks=0x1B1C:0x1B09:0x0x20000408: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-4.15.0-1018-oem (--configure):
 installed linux-image-4.15.0-1018-oem package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 grub-pc
 grub-efi-amd64-signed
 grub-gfxpayload-lists
 linux-image-4.15.0-1018-oem



```

any little help is appreciated :)

---

### Post by oldos2er on 2018-09-15
Is this a new install?

---

### Post by Impavidus on 2018-09-16
It might help if you told us what command gave that first block of terminal output. I see you try to remove some non-standard kernel. Is this a computer that came preinstalled with Ubuntu?

Anyway, there is a problem with updating grub after removing a kernel. Show us the contents of /etc/default/grub:```
cat /etc/default/grub
```
It may also be good to know what packages are partially installed:```
dpkg --list | grep -v '^ii \|^rc '
```

---

### Post by kevinkrmn on 2018-09-16
It kinda is, actually the laptop (xps 13) came with ubuntu installed

---

### Post by kevinkrmn on 2018-09-16
here is out of cat
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" usbhid.quirks=0x1B1C:0x1B09:0x0x20000408
GRUB_CMDLINE_LINUX="mem_sleep_default=deep "


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
GRUB_DISABLE_OS_PROBER=true

```

and here is dpkg --list
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                              Architecture Description
+++-=============================================-====================================-============-=============================================================================================
iU  grub-efi-amd64-signed                         1.93.5+2.02-2ubuntu8.4               amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
iU  grub-gfxpayload-lists                         0.7                                  amd64        GRUB gfxpayload blacklist
iF  grub-pc                                       2.02-2ubuntu8.4                      amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
iH  linux-image-4.15.0-1006-oem                   4.15.0-1006.9                        amd64        Signed kernel image oem
iF  linux-image-4.15.0-1018-oem                   4.15.0-1018.21                       amd64        Signed kernel image oem
ic  unattended-upgrades                           1.1ubuntu1.18.04.5                   all          automatic installation of security upgrades



```

appreciate your help :)

---

### Post by Impavidus on 2018-09-16
I'm not familiar with the usbhid.quirks=... boot option, but it seems the syntax of your /etc/default/grub is wrong. It's simply sourced from the grub.mkconfig shell script, but won't work this way. I think that line should read```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x1B1C:0x1B09:0x0x20000408"
```That is, the last double quote character should be moved to the end of the line. I don't know how this got changed or whether this was already wrong when you got that computer. You can use a text editor with root permissions to change this, for example```
sudo nano /etc/default/grub
```Edit the file, save and exit. nano shows instructions at the bottom of the screen: control-x to save and close. That is, unless that boot option shouldn't be there at all, in which case i hope somebody will tell you right away.

After you fixed your /etc/default/grub, **sudo dpkg --configure -a** should be able to fix your broken packages.

---

### Post by kevinkrmn on 2018-09-17
Yay, That fixed and error gone away. its now working fine.
Thanks a lot for the help :)

---

