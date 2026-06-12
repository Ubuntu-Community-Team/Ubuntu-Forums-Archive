---
title: "Ubuntu Live CD Hanging - Weird Graphics Problem"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by Omegaham on 2012-08-29
Hey guys,

I'm currently running Windows 7 on my computer. I've been trying to install Linux for a while, but I'm running into a roadblock.

When I start up the computer, it boots from CD to GRUB. There isn't the typical Ubuntu startup; it only gives three options - Try Ubuntu, Install Ubuntu, and Check Disk for Defects.

If I choose any of these options, it then hangs and gives me this weird scrambled graphics. I can see purple in it, so it looks like some version of the Ubuntu splash screen, but I'm not sure.

Sorry for blurry pictures; I can't take screenshots for obvious reasons.

Any help would be appreciated!

---

### Post by Quackers on 2012-08-29
Try the nomodeset boot option explained in the thread below

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Omegaham on 2012-08-29
Thanks! That worked, and now it's installed.
One more hiccup. When it boots now, it does the same thing. How do I change the boot options so that nomodeset happens in the default boot as well?

---

### Post by 9OnVar on 2012-08-29
You would have to change your GRUB file to include the nomodeset option(as explained in the thread below.)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

