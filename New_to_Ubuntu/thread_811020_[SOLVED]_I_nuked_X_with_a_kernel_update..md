---
title: "[SOLVED] I nuked X with a kernel update."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by neurostu on 2008-05-28
So I got a kernel update (or something like that) in my update manager. I installed the update and now X is totally nuked.

At first it was booting in low graphics mode, but after I couldn't get that working I then disabled the nVidia driver under the Restricted Drivers Manager.  Then X wouldn't start at all.

I then booted into recovery-mode and ran dpkg-reconfigure xserver-xorg, and X still won't start.

I really don't know what to do next, I've tried reading around on the forums but nothing has worked....

---

### Post by Zwalther on 2008-05-28
What works pretty good for me is to move the existing xorg.conf out of the way. That way X will try to automatically pick the right resolution.
Boot into recovery mode again and do (as root or with sudo in front) 
   mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

After that you can try to use the restricted drivers manager again.

---

### Post by neurostu on 2008-05-28
So when I remove xorg.conf, or when I replace it with a previous working version I just get a blank screen. It's entirely non-responsive. I can't switch to a virtual terminal, I can't use cntl+alt+backspace to kill X. I have to power cycle to reboot.

---

### Post by neurostu on 2008-05-28
I got my hands on the latest nvidia binary driver, installed that and that did the trick. I would have prefered to get it working with driver supplied by ubuntu but I couldn't get that working...

---

### Post by starcannon on 2008-05-28
Latest Binary is almost always better than the official repo ones anyway. Once in awhile a latest binary will bite me, but when that happens I just re-install the previous.

Great job getting it fixed though.

---

