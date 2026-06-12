---
title: "Disable Grub"
date: 2020-10-16
forum: New to Ubuntu
---

### Post by aka-kush on 2020-10-16
Hey, i installed kubuntu. Everything is working fine, the only problem i'm facing is whenever i turn on my laptop grub menu shows up and i've to manually enter to boot into Kubuntu.  (Note: I'm not using any other OS on dual boot)
Can anyone tell me how to remove this grub menu and boot directly into Kubuntu OS.
Thanks in advance!

---

### Post by Impavidus on 2020-10-16
Grub can't be disabled, but the menu can be skipped. And if you only install one OS, the installer is supposed to confige grub to skip the menu. That in turn can be a problem, as it makes it harder to reach the menu, which you may need when something goes wrong. I configured my system to show the menu for 3 seconds before booting the default entry.

Can you show us the contents of your /etc/default/grub?

---

### Post by aka-kush on 2020-10-16
here is the content of /etc/defualt/grub

Grub file contains this txt:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
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



```

---

### Post by aka-kush on 2020-10-16
> **aka-kush said:**
> here is the content of /etc/defualt/grub

Grub file contains this txt:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
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



```


UPDATE:
I was able to boot directly into Kubuntu by changing ```
GRUB_TIMEOUT=5
```   and adding ```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```[SIZE=3][COLOR=#000000] to /etc/default/grub/[/COLOR][/SIZE][COLOR=#000000]
[/COLOR]

---

### Post by Impavidus on 2020-10-16
I assume you read the manual pointed to by the first lines of /tec/default/grub? In any case, if you solved it, can you mark your thread as solved? Thread tools &#8594; mark as solved.

---

