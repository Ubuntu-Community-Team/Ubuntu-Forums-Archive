---
title: "software center wont open with custom distro"
date: 2014-11-04
forum: New to Ubuntu
---

### Post by Louis_Levene on 2014-11-04
hello everyone! i just recently finished creating a custom distro with some of my favorite apps installed, and it is all working fine, apart from the fact that i cant open the software center because i changed the lsb-release file so the grub dosent call my distro "ubuntu" and now the software center dosent recongnize the name of it? any ideas at all ive been searching the web for about five hours and still have nothing...

---

### Post by pissedoffdude on 2014-11-04
Hi,

What do you mean by custom distro?  If you just added packages to Ubuntu but changed the lsb-release file, you can edit /boot/grub/grub.cfg or /etc/default/grub so that it reflects your distro's name.

That's probably the safer route if you're planning on just adding a few packages, as I'd assume many of Ubuntu's components rely on it.

But if you must edit the lsb-release file, either download Ubuntu Software Center's deb file or browse all its installed files in synaptic so you can pinpoint the file that specifies Ubuntu in lsb-release

---

### Post by Louis_Levene on 2014-11-05
thank you so much i will give this a go and see what happens! :D

---

### Post by Louis_Levene on 2014-11-05
what would i change in my grub config file this is what is says... # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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

also i changed this file before but i dont remember what i did but what file would i change if i wanted to change where it said "try ubuntu" and "install ubuntu" when you boot the live cd to something else? thanks

---

### Post by pissedoffdude on 2014-11-06
You'll want to change this line: GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` to
```
GRUB_DISTRIBUTOR="Your Distro"
```
and then run ```
sudo update-grub 
```

Per [http://askubuntu.com/questions/43942/how-to-change-ubiquity-release-name](http://askubuntu.com/questions/43942/how-to-change-ubiquity-release-name) edit Your iso> .disk > info  and change Ubuntu to your distro's name so you'll see try 'your distro' or install 'your distro'

---

### Post by Louis_Levene on 2014-11-06
alright thanks a bunch!

---

### Post by Louis_Levene on 2014-11-06
everything is working fine now except for the name of it during the installation itself... when it says install alongside windows, replace windows, or something else, or when its finished is says you have now installed and then the name what file would i go to to change that...

---

### Post by pissedoffdude on 2014-11-06
According to [https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/232384](https://answers.launchpad.net/ubuntu/+source/ubiquity/+question/232384), there's a python script you can edit in /usr/lib/ubiquity/frontend.  It's most likely called unity_ui.py but I don't have an Ubuntu iso nor installation to confirm, so you'll have to find it yourself.  If there's multiple scripts in that director, you probably want the one that ends in ui.py

---

### Post by Louis_Levene on 2014-11-06
i checked all of them nothing where i can change the name of the distro.... on the desktop where the option to install the distro is the name is correct and its only during the installation the name is screwed up... im trying to call it mbuntu os however in the installer it only calls it mbuntu
i know this has something to do with ubiquity but dont know what

---

### Post by Louis_Levene on 2014-11-11
alright i got it all working now thanks for all the help

---

