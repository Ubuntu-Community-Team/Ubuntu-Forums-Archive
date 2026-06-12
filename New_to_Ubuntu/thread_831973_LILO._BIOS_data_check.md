---
title: "LILO. BIOS data check?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-06-17
I am using LILO as my bootloader, and I have good reason.

When I boot, it says```
LILO 22.8 loading linux
``` Then the screen fills up with full stops (.). then it says bios data check succesfull and finishes the boot normally. The problem is, it takes nearly 1 and a half minutes for full stops to finish appearing. if you combine that with the normal boot time, it takes for ever. short of never shutting down my laptop, how can I make is stop doing this.

Thanks in advanced.

---

### Post by Ripfox on 2008-06-17
Just out of curiosity what is this reason you use LILO instead of GRUB?

---

### Post by barbedsaber on 2008-06-18
I was having trouble with grub, it was causing my CD/DVD drive to be undetected, in ubuntu or windows. (It took a lot of dective work to come to this conclusion, but with the windows bootloader, the cd drive worked, with LILO it works, and I can boot from it [which is before GRUB did anything anyway]) (notice the incredible over use of brackets. Oh, and bump.

---

### Post by N.N. on 2008-06-18
Please post the contents of your lilo.conf file.

Haven't tried using LILO to boot Ubuntu, but I currently use it to boot CRUX Linux on my laptop, and there the part of the boot process you have described only takes one second.

---

### Post by barbedsaber on 2008-06-18
```
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
#root=/dev/sda3

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=1

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#	prompt
#	delay=1
#	timeout=1

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1
	append="root=/dev/sda3  "
	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2
	append="root=/dev/sda3  "
	initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
```

---

### Post by N.N. on 2008-06-18
Offhand, I can't say for certain what part of your lilo.conf file causes the loading to take such a long time. I'll hazard a guess, however: it's due to use of the initrd facility and/or the kernel append option.

Since your disk follows the /dev/sdx naming convention, it's probably a SATA disk or SCSI device. It seems, however, that support for SCSI disks isn't compiled into your kernel image, so in order for your distribution to boot, the kernel must load the SCSI driver module. This is done by means of the initrd facility, which first sets up a temporary file system in a RAM disk containing the driver module and then loads the module and mounts the real root filesystem. I guess this process is more time-consuming than a regular boot, but I'm not sure whether it's the sole cause of the long loading time. Regardless, you should be able to avoid use of the initrd facility by recompiling your kernel with support for SCSI disks.

Another possible cause of the long loading time is the string that you're passing to the kernel by means of the append option. Do you deliberately pass the string "root=/dev/sda3  " to the kernel by means of the append option instead of just specifying the kernel option root=*root-device*? If that's the case, then why do you do it that way?

An image section for regular Linux on an IDE drive might look as follows: ```
## Image section: Regular Linux
image=/boot/vmlinuz
   label=linux
   root=/dev/hda2
   install=/boot/boot.b
   map=/boot/map
   read-only
```
As appears from this example, using simply root=/dev/hda2 instead of append="root=/dev/hda2" should work. Perhaps that's only for IDE drives, however?

A simple fix you might try is to remove the two spaces in the append="root=/dev/sda3  " option. I'm not sure whether that'll have any effect at all, but it's worth a try.

Remember to run the following command after making any changes to the .conf file: ```
sudo lilo
```

---

### Post by barbedsaber on 2008-06-18
> **N.N. said:**
> 

A simple fix you might try is to remove the two spaces in the append="root=/dev/sda3  " option. I'm not sure whether that'll have any effect at all, but it's worth a try.

Remember to run the following command after making any changes to the .conf file: ```
sudo lilo
```

I tried that, ti didn't work. I rally don't like the idea of recompiling a kernel, but if you think it could work, could you please point me in the right direction.

---

### Post by N.N. on 2008-06-18
I'm not sure that it'll solve the problem. In fact, if you didn't experience the problem when you used GRUB, then it almost certainly won't.

Recompiling the kernel in Ubuntu does look a bit laborious, so, on second thought, I won't advise you to try it. Instead I'll advise you to get a second opinion on the matter.

Seeing as this thread hasn't got a lot of attention in this subforum, you should try asking it again in one of the more specialised subforums, perhaps in ["Installation & Upgrades"]("http://ubuntuforums.org/forumdisplay.php?f=333").

Should you decide to have a try at recompiling the kernel, remember to backup your essential data beforehand, and remember to update your lilo.conf file afterwards. There is [an entry]("https://help.ubuntu.com/community/Kernel/Compile") in the community documentation on how to recompile a custom kernel but, again, consider it a last resort.

Good luck.

---

