---
title: "USB Boots to Terminal not 11.10"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-30
I have 11.10 on a USB flash.

The PC boots to a full black screen "terminal' mode.

Is there a command to switch to purple Ubuntu?

Getting close.....

---

### Post by daslinkard on 2012-04-30
I'm throwing this out there as I'm not 100% positive this would work but what about updating the grub?  A possible update command through the terminal would be:

```
sudo update-grub
```

This is a possible solution but I want to leave this for others to feed off of too....thoughts?

---

### Post by oldfred on 2012-04-30
Is this the installer or a full install on a flash drive?

It probably is a video issue.
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/](http://blog.bodhizazen.net/)
simply edit “syslinux.cfg” 

If nVidia:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

