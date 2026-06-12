---
title: "Xubuntu 12.04 boots to terminal not desktop or hangs during boot"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by thepreacherswife on 2013-10-17
Since my kernel was updated from 3.2.0-49, xubuntu does not boot to the desktop, but only to the terminal.  The xubuntu splash screen shows for a moment, then the terminal login.  Currently 3.2.0-54 is the default kernel in grub.

Sometimes I don't get to the terminal at all and the system hangs somewhere in the boot process.  If I press ctrl-alt-delete during the boot process once things hang, the next thing I see is something like: 
```
ascpid: exiting
Stopping Name Server Cache Daemon: nscd
```
then a bunch of other stuff before reboot commences.

If I get to the terminal I have tried to start lightdm but it hangs somewhere in the process.  Also tried to reconfigure and then reinstall lightdm but still no good.

I can select the 3.2.0-49 kernel in grub and get the xfce desktop but I imagine there's something that needs fixing, maybe something to do with the nvidia display driver?

Per lspci | grep VGA, I have an NVIDIA NV441A GeForce 6200 (rev a1) installed.

[COLOR=#b22222]edit: Fixed by purging the nvidia-* packages, removing  /etc/X11/xorg.conf, then reinstalling xubuntu-desktop, nvidia-current, and nvidia-settings.[/COLOR]

---

