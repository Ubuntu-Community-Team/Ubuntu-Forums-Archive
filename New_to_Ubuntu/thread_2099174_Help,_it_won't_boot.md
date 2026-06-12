---
title: "Help, it won't boot"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Nottawa Newbie on 2012-12-28
I upgraded to 12.04 LTS a few days ago and everything seemed to be running just fine.  Today I had to use windows 7 for something and when I tried to come back to Ubuntu, it would not boot.  I get to the grub page and pick my os.  It makes some motions towards booting but then just stalls.  On 2 occaisions it has given an message that it is booting with low resolution graphics.  When you click on ok it comes to a screen with 4 options ( do it this one time, reboot, and I forget the others) but I am unable to choose anything as there is no mouse pointer and the keyboard will not move the highlighted selection and the enter key will not start the computer moving again.  Please help!!  Thanks.

---

### Post by Bucky Ball on 2012-12-28
Try this. When you get to the list of OSs at boot, choose the Ubuntu kernel, hit 'e' to edit, find the kernel line, it will have 'splash' or 'quiet' or 'quiet splash' or something like it.

To the end of that line, after a space, add 'nomodset'. Follow the instruction at the bottom of the screen to save changes and boot.

If that worked, we can take it from there and make it permanent (this change will be erased on restart).

Good luck.

PS: I'm presuming this is the first time you've restarted Ubuntu 12.04 LTS since the upgrade?

---

### Post by oldfred on 2012-12-28
Do you get that same recovery mode screen with the second option in the grub menu.

Did you upgrade anything before rebooting, like a video driver?

From grub menu if recovery mode does not work try nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

