---
title: "Stuck in booting Ubuntu"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by robbinpeng on 2015-11-25
This is the second time I am starting my ubuntu. The first time is after installing the system.

I will get stuck at the message line "Stopping Userspace bootsplash    [OK]", the x window won't show up.

if I type "Ctrl+Alt+F1", I can use my account to login, and type "startX" to start x window.But the difference is my icon on desktop are disappeared, and the system task bar also disappeared, very different from the first time I used Ubuntu.

Anyone could help? 1&#12289;why I am stucked at that line? 2&#12289;why the x-window different from the one I first time used?

---

### Post by T.J. on 2015-12-01
It sounds like your display manager is not configured properly.  It is the program that gives you a login screen.  It is also possible that your install is attempting to use a video driver that does not support the display manager.

As a test, I would install lightdm -* sudo apt-get install lightdm* and then make sure your setup is configured to use it: *sudo dpkg-reconfigure lightdm*.  After that you should reboot, in order to test it.

Lightdm pretty much works with everything, others like ssdm or gdm (gnome) tend to be very sensitive to changes.  GDM is known not to work at all if you are using the AMD Catalyst driver, because AMD's drivers do not support the EGL graphics standard.

---

