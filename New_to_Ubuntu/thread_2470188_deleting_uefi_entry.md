---
title: "deleting uefi entry"
date: 2021-12-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2021-12-21
running 20.04

```
sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-system-image.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-43-generic
Found initrd image: /boot/initrd.img-5.11.0-43-generic
Found linux image: /boot/vmlinuz-5.11.0-41-generic
Found initrd image: /boot/initrd.img-5.11.0-41-generic
Adding boot menu entry for UEFI Firmware Settings
done
here is grub output
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuratio
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/ray/faries/1440-900-84478.jpg"

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

/tks
```

---

### Post by rburkartjo on 2021-12-21
i noticed that this entry  was missing from copy of default grub

GRUB_DEFAULT=0

copy of default grub

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

should i add back to my grub as posted earlier /tks

---

### Post by ajgreeny on 2021-12-21
I am not sure what this query has to do with UEFI as all you show relates to grub and the /etc/default/grub file.

Do you have a problem with either grub or UEFI?

---

### Post by rburkartjo on 2021-12-21
aj want to disable the uefi entry on my grub menu thats all/tks

---

### Post by rburkartjo on 2021-12-21
aj 
when start my computer grub appears and has 3 options
ubuntu
advanced option for ubuntu
uefi firmware settings

this happened when trying to change plymouth themes
just want to remove the last option/tks

---

### Post by rburkartjo on 2021-12-21
also grub menu is one quarter of my monitor and when i select ubuntu i boot up in text mode untill  normal graphic login screen appears. besides that ubuntu runs fine

---

### Post by ajgreeny on 2021-12-22
It sounds as if changing your Plymouth theme may be behind these changes. I'm not sure about the firmware or UEFI option you see or how to remove it as it's something I use and find useful if I forgot that I want to change something but miss it at the first second or two at boot up.
Why do you want it removed; it doesn't slow down grub?

You still have the "quiet splash" option in the config file so should see the splash screen, not a text boot screen.
What Plymouth packages do you actually have installed?

---

### Post by rburkartjo on 2021-12-22
aj even if i change plymouth theme nothing changes. i have a nice background image that i like on my old grub with the uefi optiom. do you think that adding the aforementioned
GRUB_DEFAULT=0

would solve the issue. just want to make sure that adding it would not mess up default grub/tks
want to make sure before i try

---

