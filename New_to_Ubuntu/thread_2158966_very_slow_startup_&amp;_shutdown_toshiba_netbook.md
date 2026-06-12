---
title: "very slow startup &amp; shutdown toshiba netbook"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by jim3008 on 2013-07-01
recently i've installed lubuntu 13.04 on my old toshiba netbook.  loved the ov erall experience. it's smooth and problem free most of the time.  however, it generally, takes 5-10 mins for every startup & shutdown.  what gives?

ps Netbook Toshiba Mini NB305 specs:

[TABLE="width: 389"]
[TR="bgcolor: #FFFFFF"]
[TD][FONT=inherit]Processor[/FONT][/TD]
[TD="align: center"][LEFT][FONT=inherit]1.6 GHz Intel Atom N450[/FONT][/LEFT][/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD][FONT=inherit]Memory[/FONT][/TD]
[TD="align: center"][LEFT][FONT=inherit]1GB, 800 MHz DDR2[/FONT][/LEFT][/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD][FONT=inherit]Hard drive[/FONT][/TD]
[TD="align: center"][LEFT][FONT=inherit]250GB 5,400rpm[/FONT][/LEFT][/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD][FONT=inherit]Chipset[/FONT][/TD]
[TD="align: center"][LEFT][FONT=inherit]NM10[/FONT][/LEFT][/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD][FONT=inherit]Graphics[/FONT][/TD]
[TD="align: center"][LEFT][FONT=inherit]Intel GMA 3150[/FONT][/LEFT][/TD]
[/TR]
[/TABLE]

---

### Post by dino99 on 2013-07-01
you can see the startup & shutdown comments (verbose mode) if you remove "quiet splash" inside /etc/default/grub, then update grub to take effect on the next boot

into a terminal, run:
> sudo gedit /etc/default/grub  and do the tweak, then
> sudo update-grub
and finally , reboot

---

### Post by jim3008 on 2013-07-01
> **dino99 said:**
> you can see the startup & shutdown comments (verbose mode) if you remove "quiet splash" inside /etc/default/grub, then update grub to take effect on the next boot

into a terminal, run:
  and do the tweak, then

and finally , reboot


well, that's easy and fast.

thanks for your reply. i'll try it out

edit: i'd just tried your suggestions.  the shutdown time is fast (~20seconds). however, the startup time still took 7mins.  is there any other ways to speed things up a bit? 

i guess i don't quite understand how to 
[COLOR=#000000]
 remove "quiet splash" inside /etc/default/grub,

when i type:
[/COLOR]> [COLOR=#000000][I]sudo gedit /etc/default/grub
[/I][/COLOR][COLOR=#000000][I]
i get
> [/I][/COLOR][COLOR=#000000]*sudo: gedit /etc/default/grub: command not found*[/COLOR][COLOR=#000000][I]
[/I][/COLOR][COLOR=#000000][I]
[/I][/COLOR]

---

### Post by kennerc on 2013-07-01
Try to replace "gedit" with "leafpad".
This isn't to make things faster, but to see what is slowing the boot.

---

### Post by jim3008 on 2013-07-01
> **kennerc said:**
> Try to replace "gedit" with "leafpad".
This isn't to make things faster, but to see what is slowing the boot.

so this is what's in grub file, i just don't know how to remove the "quiet splash".

> # If you change this file, run 'update-grub' afterwards to update
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
#GRUB_INIT_TUNE="480 440 1"


---

### Post by zrdc28 on 2013-07-01
sudo leafpad   /etc/default/grub then enter your password.
remove "quiet splash"  then "sudo update-grub"  next you might want to reboot.

When you reboot look for the problem that is stopping the bootup and then you can correct it,

I am using lububtu on the asus eeepc 901 and it boots in under 1 minute. 
It has the atom 1.6 processor and 1g memory.

---

### Post by kennerc on 2013-07-02
Just to make things clear, you should remove "quiet splash" form the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
So it will look like this:
GRUB_CMDLINE_LINUX_DEFAULT=
On the boot you will see a text screen instead of the blue screen from the Lubuntu, this screen will show what is loading, and probably some errors in some process, you should analyse the boot screnn.

---

