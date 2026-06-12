---
title: "No Splash"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by snip3r8 on 2011-09-10
Im running natty,I dont get the splash(previously known as usplash but i forgot the new ones name)on boot up,i just get a purple screen,but when i shut down i get one,grub settings maybe?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT="text"
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

### Post by ubudog on 2011-09-11
Could you post a picture of your GRUB config for the relevant Ubuntu option in the menu?  (accessed by pressing 'e' once the selection is highlighted)

Note: It would be best to take a picture and upload it, since you cannot take a screenshot.

Also, do you have any graphics card drivers installed?

---

### Post by fractalman on 2011-09-11
I have a similar problem, on boot i get a purple screen followed by a black screen with the message

mountall failed: could not connect to plymouth
mountall failed : plymouth disconnected

then on shutdown i get the splash screen but its the wrong size and sometimes has system text written all over it.

It started after installing the nvidia drivers and everything i have found online has failed to rectify the solution so i'm just puttin up with it for now

---

### Post by MG&amp;TL on 2011-09-11
There's quite a common bug to do with installing graphics card drivers that causes an ugly plymouth boot screen, or sometimes non at all...

google: 'fix ugly plymouth boot screen' and there's plenty of scripts. But IDK if it's the same problem. So go cautiously, and find a manual form (e.g instructions). Or read what the script is doing, by viewing it in gedit or something.

---

### Post by Frogs Hair on 2011-09-11
I have  tried many of the fixes for the splash screen and this is the only one that has worked for me .[http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/](http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/)

---

### Post by ubudog on 2011-09-11
> **frogs hair said:**
> i have  tried many of the fixes for the splash screen and this is the only one that has worked for me .[http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/](http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/)

+2

---

### Post by fractalman on 2011-09-12
Well i found this thread which had not shown up in any previous google searches, it seems to have done the job for now,  i get the following

black screen with cursor in top left for 2 secs
purple screen for about 2 seconds
complete mess on the screen for about half a second (screen goes black with blocks of colour on the top half)
ubuntu splash screen for 3 secs
log in

[http://ubuntuforums.org/showthread.php?t=1742944](http://ubuntuforums.org/showthread.php?t=1742944)

not a complete fix but better than i had before :)

---

