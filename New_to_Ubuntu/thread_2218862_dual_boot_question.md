---
title: "dual boot question"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by windowsfree on 2014-04-22
Hi,  I just installed **14.04** in a dual boot setup.  how do i edit the menu so that I can have more time to choose what OS I want to boot into?


Thanks,

---

### Post by Elfy on 2014-04-22
Open /etc/default/grub as root for editing.

Mine is like 
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**[COLOR="#FF0000"]GRUB_TIMEOUT=3[/COLOR]**
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

Change the timeout line - I do the opposite - less time to choose :)

If you want it to sit at the grub menu until you choose - set it to -1

Save the file and then run 

```
sudo update-grub
```

---

### Post by windowsfree on 2014-04-22
Thank you, I will attempt this later today.

---

