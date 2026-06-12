---
title: "Intel Video Card problems"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by crowverte on 2008-10-03
When I run the hardware test, my video card 'fails' it.  Along with that I can not change visual effects from no effects to normal or extra effects. Not crucial problems, but I would still like to fix them. I have an integrated graphics card: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller 
Could any one help?
Thanks!

Edit//
So i ran 'compiz' in the terminal and got this:
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by eternalnewbee on 2008-10-07
Hi there.
I've this happen on other computers as well.
Have you tried enabling your hardware driver from System> Administration> Hardware Drivers?
If that failed then your Graphics card probably doesn't support hardware acceleration..

---

### Post by overdrank on 2008-10-07
Thread closed duplicate [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=938394)
Please do not create multiple threads on the same issue.

---

