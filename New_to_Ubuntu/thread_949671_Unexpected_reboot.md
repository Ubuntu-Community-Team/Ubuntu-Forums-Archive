---
title: "Unexpected reboot"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Maupertus on 2008-10-16
Hey guys,

once in a while my system shuts down unexpectedly and I have no idea why. I used to think it was because of flash or heavy javascript, as I've had problems with flash/firefox/64-bit before.

But when I look into my log it gives the following lines:

[quote=syslog]Oct 16 18:32:39 matthijs kernel: [18303.711221] compiz.real[8468]: segfault at 547be rip 40fecf rsp 7ffff6a3f930 error 4

Oct 16 18:32:39 matthijs gdm[8260]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 [/quote]

Does anyone have idea what this is?
I can leave my computer one for days at a time, and nothing happens, and sometimes when I just browse using firefox I get a shutdown.

---

### Post by NESFreak on 2008-10-16
it's an issue related to compiz, try turning off your desktopeffects. This should solve the rebooting problem, though leaving you without your nice effects. As for an actual fix: what videocard are you using? If you'd like you could post a bugreport.

---

### Post by Maupertus on 2008-10-16
> **NESFreak said:**
> it's an issue related to compiz, try turning off your desktopeffects. This should solve the rebooting problem, though leaving you without your nice effects. As for an actual fix: what videocard are you using? If you'd like you could post a bugreport.

ATI HD2600pro AGP 512MB, drivers installed through envy.
Strange though as I didn't have any problems with my very old crappy Nvidia GforceFX5200 128.

---

### Post by NESFreak on 2008-10-16
this thread appears to be about a somewhat similar issue:
[http://ubuntuforums.org/showthread.php?t=781312](http://ubuntuforums.org/showthread.php?t=781312)

There appear to be lots of ati related problems (even though there drivers are improving, so I've heard, only had nvidia cards myself including the fx5200 (which worked great under ubuntu 5.10(seems like ages ago))(and one 3dfx still lying around somewhere)). Are there any new ATI drivers made available? Try upgrading to one of them.

---

