---
title: "blank screen at login , mode not supported"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-19
I can boot up to desktop login(s) screen , but when I login to either gnome or kde I get this message "Mode not supported" and a blank screen.
I have been working on xorg.conf to get a decen resolution on my new TV . And I do until I login to gnome or kde.
I am no expert but if I get this far then the x-server has no issues , and the xorg.conf must be OK? 
So I'm thinking what happens when gnome or kde start to change the video settings ? and how do I stop it or make gnome use the same as the x-server?

Or am I on completely the wrong track?

---

### Post by islandstone on 2008-11-19
contents of .xsession-errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/island-desktop:/tmp/.ICE-unix/6457
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Initializing nautilus-share extension


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
seahorse nautilus module initialized
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...none found
11
Throttle level is 0

** (nautilus:6557): WARNING **: Unable to add monitor: Not supported
evolution-alarm-notify-Message: Setting timeout for 9818 1227139200 1227129382
evolution-alarm-notify-Message:  Thu Nov 20 00:00:00 2008

evolution-alarm-notify-Message:  Wed Nov 19 21:16:22 2008

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by islandstone on 2008-11-19
tried removing compiz , no change

sudo apt-get remove --purge compiz*

---

