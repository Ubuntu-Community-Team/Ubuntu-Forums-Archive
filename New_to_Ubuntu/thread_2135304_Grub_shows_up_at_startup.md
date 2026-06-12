---
title: "Grub shows up at startup"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by jdwaugh on 2013-04-13
After a recent update it seems that when I boot the machine Grub loads and asks what I OS I want to launch.  However, there are no other OS on the machine and it just launched Ubuntu previously.  How do I edit the file so it will just launch ubuntu and not wait for timer to run out, or for the user to select?

Thanks.

---

### Post by DuckHook on 2013-04-13
I don't normally recommend adding PPAs to the base repositories for new users, but *grub customizer* is a special case that has been around for years and has been tested and used by thousands without security incidents. This app will not only allow you to get rid of the selection screen, but also tweak *grub* in other ways, like adding background images and getting rid of the startup sound. Instructions for installing are [here]("http://ubuntuforums.org/showthread.php?t=1664134").

---

### Post by claracc on 2013-04-14
You can also edit your /etc/default/grub file and put the line GRUB_HIDDEN_TIMEOUT=0

You will have to edit the grub file as root in a xterm:

gksudo gedit /etc/default/grub

after putting a 0 in the forementioned line you will have to save and close the file, in this way the selection menu for booting OS won't appear. Then you have to upgrade grub with the order:

sudo update-grub

---

### Post by jdwaugh on 2013-04-14
OK, I figured I would just edit the test file since this is a one time thing.  However, the GRUB_HIDDEN_TIMEOUT=0 is alread set.  Here is the contents of the file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi="
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

So what now?  THanks for all the help.

---

### Post by nerdtron on 2013-04-14
After editing the grub configuration file, save it (of course! :D), then you should always update grub to let it know the changes. Here is the command
```
sudo update-grub
```

---

### Post by claracc on 2013-04-15
You also has to put:
GRUB_TIMEOUT=0

---

### Post by Locus Kiesselbachi on 2013-04-15
Nr1. Try suggestions, given here before!
Nr2. If you have tried all suggestions said before here and nothing helps then:
Go [here]("http://ubuntuforums.org/showthread.php?t=2134968")! That is about changeing grub timeout to 0, zero.
Good luck!

---

### Post by jdwaugh on 2013-04-15
Thanks, setting timeout=0 fixed it.  How do I change it to "solved"

---

### Post by Locus Kiesselbachi on 2013-04-16
> **jdwaugh said:**
> Thanks, setting timeout=0 fixed it.  How do I change it to "solved"

[Here!]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ([COLOR=#333333][FONT=Ubuntu Beta]How to mark your thread as SOLVED[/FONT][/COLOR])

---

