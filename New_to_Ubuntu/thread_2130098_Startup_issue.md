---
title: "Startup issue"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by ers11121 on 2013-03-28
Good morning,
I have a startup question, when I first boot the computer with 12.04 it brings up a screen for me to choose what system to boot, I have to hit the enter key to advance to the login screen. There is only one system on this laptop. I have installed other version of Ubuntu in the past and not has this issue, they would go right to the login screen. I have followed instruction found to enable "quiet boot" but still have the same issue. I'm hoping someone has a suggestion.
thanks in advance,
Ed

---

### Post by JRV on 2013-03-28
The easiest way to control the behavior of grub is to install grub-customizer, like this:

```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```

To remove the grub menu :

Run the program, click on the General Settings tab, and uncheck Show Menu.

---

### Post by Bashing-om on 2013-03-28
ers11121; Hi !
Alternately/additionally to JRV's advise; perhaps edit /etc/default/grub file to obtain that result.
Post your file and we will see;
```
 cat  /etc/default/grub
```[INDENT=2]
one more way

[/INDENT]

---

### Post by bwallum on 2013-10-07
I would like to see my GRUB 2 menu at boot up. What do I need to do to the configuration please?

Here is my etc/default/grub file:-

[QUOTE]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
#GRUB_INIT_TUNE="480 440 1"[QUOTE]

---

### Post by Dennis N on 2013-10-07
Change **GRUB_TIMEOUT=10** to **GRUB_TIMEOUT=-1**

Then the system will always display the grub menu and stop and wait for you to make a choice, even if there is only one operating system installed.

---

