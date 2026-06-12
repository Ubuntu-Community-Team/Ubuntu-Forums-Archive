---
title: "Problem not boot text mode"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by jigonzalezrodrigue on 2015-02-15
good morning


I have a problem with my OS Ubuntu Server 12.04.5 i386 version: I installed a light graphical environment but try to configure / etc / default / grub follows:


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
# GRUB_TERMINAL=console


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





I run sudo update-grub command and rebooted, but still starts the graphical environment and does not start in text mode


Please i need your help because I've tried several configuration but not work.


Sorry for my English. Thank you very much. A greeting.

---

### Post by v3.xx on 2015-02-15
From what I have read, that should also work.  I do it a bit different, but it still takes me to console and the startx command can be used to take me to gui.
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
```

This yields the same result.
```
sudo bash -c 'echo "manual" >> /etc/init/lightdm.override'
```
[http://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode](http://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode)

---

### Post by jigonzalezrodrigue on 2015-02-15
hello

I have not installed LightDM, beccause I have installed as follows:

```
sudo apt-get install x-window-system-core gnome-core
sudo apt-get install xorg gnome-core
sudo apt-get install language-pack-es
sudo apt-get install language-pack-es-base
sudo apt-get install language-pack-gnome-es
sudo apt-get install language-pack-gnome-es-base
sudo apt-get install language-selector
sudo apt-get install language-support-es
sudo apt-get install gksu
sudo apt-get install gnome-system-tools gnome-nettool
sudo update-grub
sudo reboot
```

And always, althought modify the file /etc/default/grub starts in graphical mode

---

### Post by v3.xx on 2015-02-15
But you have installed gdm.  So maybe disable it.

[http://packages.ubuntu.com/trusty/gnome-core](http://packages.ubuntu.com/trusty/gnome-core)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+gdm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+gdm&sa=Search&cof=FORID:9)

---

