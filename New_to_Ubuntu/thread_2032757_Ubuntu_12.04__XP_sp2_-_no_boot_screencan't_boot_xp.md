---
title: "Ubuntu 12.04 | XP sp2 - no boot screen/can't boot xp"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by sine wave on 2012-07-24
I installed Ubuntu 12.04 next to an already existing XP. I ran Boot-Repair. What would I be able to do to fix this? Thanks for any help/wisdom!

[http://paste.ubuntu.com/1108790/](http://paste.ubuntu.com/1108790/)

---

### Post by oldfred on 2012-07-24
Welcome to the forums.

Script looks normal. Are you getting grub menu or grub> or grub rescue> ?

Or is it just the black screeen and you have nVidia video card?

If black screen try nomodeset in place of splash quiet in grub menu. Use the e for edit command at meu.
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sine wave on 2012-07-24
> **oldfred said:**
> Welcome to the forums.

Script looks normal. Are you getting grub menu or grub> or grub rescue> ?

Or is it just the black screeen and you have nVidia video card?

If black screen try nomodeset in place of splash quiet in grub menu. Use the e for edit command at meu.
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On restart, holding down shift- there's a blank grey screen for a second, then boots up into ubuntu :confused:
is there anything in [COLOR="Gray"]/etc/default/grub[/COLOR] that needs to be changed?

> 
# If you change this file, run 'update-grub' afterwards to update 
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


---

### Post by oldfred on 2012-07-25
Is not Windows the last entry on the grub menu? Or when you click that does it not boot?

Then you may need to run chkdsk on the Windows NTFS partition from a XP disk or other Windows repairCD.

---

### Post by sine wave on 2012-07-25
I ended up fixing it by changing these lines-

> 
[COLOR="DimGray"]GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false[/COLOR]

& uncommenting
[COLOR="DimGray"]#GRUB_GFXMODE=640x480[/COLOR]


Grub menu now displays upon restart :)
Thank you

---

