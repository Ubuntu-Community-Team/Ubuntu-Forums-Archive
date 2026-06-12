---
title: "GRUB Issues"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by eamonn on 2011-12-19
Hello all,

I'm running 11.04 and decided to spend my winter break tweaking Grub until I could boot directly into tty1 and I got turned around somewhere.

I still boot into tty7 but I have two new problems. 

The first is, while Ubuntu is loading, instead of the Ubuntu logo or any information about what processes are being started, I get a flashing cursor in the top left of my screen. The graphical login from tty7 will eventually load up but, until it does, all I can see if the flashing cursor.

The second problem that I have is the screen resoluton on my other tty's has been changed. It looks like it's about 640 x 48. I believe that it had been around 1280 x 720 before.

At this point, I'm just interested in returning Grub to the default settings that existed when I installed 11.04. 

Here's a copy of my Grub configuration for reference.

> # If you change this file, run 'update-grub' afterwards to update
# /boot/brug/grub.cfg
# For full documentation of options in this file see:
# info -f grub -n 'Simple confuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='lsb_release -i -s 2> /dev/null || echo Debian'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"
GRUB_CMD_LINE=" vga=775 splash"

#Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernal that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567, 0xfefefefe,0x89abcdef,0xefefefef"

#Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command 'vbeinfo'
# GRUB_GFXMODE=640x480

#Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

#Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

#Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

I also have this information from the startup:

> setparams 'Ubuntu, with Linux 2.6.38-13-generic'

recordfail
set gfxpayload=$linux_gfx_mode
insmod par_msdos
insmod ext2
set root='(dev/sda,msdos5)'
seach --no-floppy --fs-uuid --set=root 4153ea84-7423-49a3-8eb80-4007a4326dda
linux /vmlinux-2.6.38-13-generic root=UUID=914b61f6-c063-4df1-a0c3-99e4b6022b7 ro vga=775 splash quiet splash ipv6.disable=1 vt.handoff=7
initrd /initrd.img-2.6.38-13-generic


---

### Post by ajgreeny on 2011-12-19
Try deleting the vga=775 from the **GRUB_CMD_LINE=" vga=775 splash"** line to leave [B]GRUB_CMD_LINE="splash"

[/B]The default contents of that file are
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

