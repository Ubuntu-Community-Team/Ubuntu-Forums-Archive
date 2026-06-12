---
title: "Unable to boot with no terminal attached"
date: 2022-11-06
forum: New to Ubuntu
---

### Post by macbates on 2022-11-06
I installed the latest version of Ubuntu on a stick PC (Atom x5-Z8350, 4 GB memory), and although it's a puny little guy, Ubuntu runs nicely for what I intend to do with it. The problem I'm having is that if I do not have a monitor attached, Ubuntu will not boot. I can disconnect the keyboard and it will boot fine, but if the monitor is not connected to the stick PC's HDMI port, Ubuntu will not boot. I've tried both Ubuntu desktop and server, and the problem is the same with both. Kind of surprising, since I assumed that a server really doesn't need a monitor, but in my case, it clearly does. I don't think it's a BIOS issue since the stick PC used to run Windows 10 Pro in a remote configuration, and booted and ran just fine with no attached monitor or keyboard, and there's nothing in the BIOS that relates to keyboard or monitor connectivity.

So, any ideas of what I can look for or change to get this thing to boot in a headless more. I've looked at the boot log that failed and can't find anything, but I have no clue what to look for. I uploaded the log file of the failed boot to [this Dropbox folder]("https://www.dropbox.com/s/xua62l8dqu5b7yd/failedboot.txt?dl=0"), if anyone wants to take a look at it. The end goal is to have this PC running headless as a network monitor, and I'm hoping that I can use Ubuntu to do this. It runs fine with a monitor attached, but that's not my goal.

Thanks in advance for any help or advice,

---

### Post by MAFoElffen on 2022-11-06
To run headless, without a monitor, ensure the BIOS does not have a BIOS setting requiring a keyboard is present... Run Server Edition, with a grub file (/etc/default/grub) like this...

Remove "quiet splash" and make these changes:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]-- nomodeset 3[/COLOR]"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
[COLOR=#ff0000]GRUB_TERMINAL=console[/COLOR]

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
Then after modified and saved:
```

 sudo update-grub 

```

---

### Post by macbates on 2022-11-06
Thanks! Easy, once you know how to do it (which I didn't).

---

