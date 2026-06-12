---
title: "Problem starting window manager after Nvidia driver installed."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by oldsoulsong on 2008-11-05
Hi everyone

Ive just installed 8.10 on my computer. I'm dual booting via wubi at the moment. I have dual 9600 GT's in my system. Running Sli in windows.   

I installed the Nvidia drivers via the hardware drivers GUI. But when I restart the computer the window manager doesn't load up and it says that its failed to set a resolution that's far too high for my monitor. So I'm stuck in console mode and when I try startx it just comes up with the failed to set resolution thing again. The resolution it tries to set is 1600x1080. My monitor is 1440x900.

Does anyone have any idea what could be causing this

If you need anymore information about my PC just ask 

Thanks in advance

---

### Post by Tamlynmac on 2008-11-05
You may wish to read this:

[http://ubuntuforums.org/showthread.php?t=968405&page=2](http://ubuntuforums.org/showthread.php?t=968405&page=2)

---

### Post by brandoncolorado on 2008-11-05
Usually if x server is not starting you need to reconfigure it. Even on fresh installs.

Try this:

at the prompt type
sudo dpkg-reconfigure xserver-xorg

This will walk you through the configuration. Once you have completed this you need to restart the xserver.

startx

---

