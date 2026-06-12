---
title: "Grub not auto booting by default"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by 1danjack on 2011-11-16
I'm running ubuntu 11.10 64bit server edition on a box with no monitor, keyboard, etc., just ssh'ing into it, but i don't want it on 24hours. I've tried to configure grub to just autoboot to the default OS on power up but it doesn't always.

It might be just me but reboots seem to be fine, but prolonged (12hour) power-offs don't autoboot!

Below is the grub, I've read the man but cannot see what's wrong. I would appreciate any sensible input...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
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
```

---

### Post by denpark on 2011-11-18
im having the same exact problem..any suggestions?

any insight would be greatly appreciated.

thanks in advance!

Dennis

-----------------
**System Info**
[LIST]
[*]Dell T105
[*]Operating system: Oneiric Ubuntu Server 11.10 
[*]Kernel: 3.0.0-12-server
[*]Processor: Dual Core AMD Athlon(tm) 4450B; 2.3 GHz, 2x512K Cache,  x86_64
[*]Memory: 4.0 GB
[/LIST]

---

### Post by canbula on 2011-12-28
I have got the same problem

when I shutdown my server with "sudo shutdown -h now" command, it doesn't autostart on next boot

when I shutdown it with "sudo shutdown -P now" command, it starts normally, maybe this command can help you

---

