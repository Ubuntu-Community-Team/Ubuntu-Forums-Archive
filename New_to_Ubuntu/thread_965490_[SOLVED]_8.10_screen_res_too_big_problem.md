---
title: "[SOLVED] 8.10 screen res too big problem"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-10-31
I foolishly changed the screen res in the preferences menu to something much larger than my actual screen. Now when it loads up, the opening screen with the ibex is so huge that I can't see, much less click, on any drop-down menu to change it back to normal.

I can get into the root directory by booting to recovery mode. So here I am at root, but I have no idea what command to use to get to the monitor settings. I've tried dpkg-reconfigure xserver-xorg based on advice given in another thread but it only takes me through keyboard settings.

Could someone tell me what to do?

Thanks in advance,
EG

---

### Post by bswilson on 2008-10-31
Since you're in the system as root, you can manually edit the xorg.conf file which controls the resolution.  First, let's back up your configuration just in case:

```
# cd /etc/X11
# cp xorg.conf xorg.conf.BAK
```

Then, you can edit the file and change the resolution.

```
# vi xorg.conf
```

Look for the section that begins with **Section "Monitor"**, and take out the lines that represent a higher resolution than you want.  Save and exit, and you can reboot (or restart the X server).  To restart the X server without rebooting, just do this (as root):

```
# /etc/init.d/gdm restart
```

Good luck!

---

### Post by eatingganesh on 2008-11-01
thanks for the advice B! Unfortunately it didn't work (though it should have). Under the monitor section it basically listed "monitor" with a caveat that in 8.10 system settings can no longer be edited directly, but must be approached through the preferences dialog. 

So I reinstalled the whole deal and now everything is fine. I certainly won't be making that mistake again now that I know that some of the editability has been removed from 8.10.

Thanks for taking the time to help!

---

### Post by Martje_001 on 2008-11-01
Intrepid only let it out because of flexibility. For example: if you buy a new videocard, you don't have to change the driver in xorg.conf, or if you buy an new monitor, the resolution, etc.

---

