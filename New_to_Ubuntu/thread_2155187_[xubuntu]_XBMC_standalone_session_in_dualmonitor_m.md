---
title: "[xubuntu] XBMC standalone session in dualmonitor mode"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by grimy55 on 2013-06-17
Hi all,

This is my first post in this forum, and I hope to be clear and concise enough in describing my issue.

[B]What I have:
[/B]A ION3D running on xubuntu 13.04 as a media center with XBMC. It is connected both to a small touchscreen and a video-projector. Everything works fine when I use XBMC within the xubuntu session with monitors set in mirror mode by using the nvidia-settings app.

**What I would want:**
To optimize the sytem, I would want to lauch XBMC at startup in its own session.

**What I did:**
Tried first to create a XBMC-standalone session with the following files:

/usr/share/xsessions/XBMC.desktop

```
[Desktop Entry]
Name=XBMC
Comment=This session will start XBMC Media Center
Exec=/usr/bin/runXBMC_standalone
TryExec=/usr/bin/runXBMC_standalone
Type=Application

```

/usr/bin/runXBMC_standalone

```
#!/bin/bash

# Enable nvidia settings
nvidia-settings --load-config-only
# Enable touchscreen functionalities
export SDL_MOUSE_RELATIVE=0
# Launch XBMC
exec /usr/bin/xbmc --standalone

```

**Issue:**

The XBMC session can be launched smoothly with only one problem: Only the primary monitor get an image, the other one is black. By looking around the web, I understood there is something with X window that need to be launched at the beginning of the session for nvidia-settings to be applied, but I don't know what command line should I use. I tried "startx" but, obviously, Gnome is not found, and with "startxfce4" I have a full desktop environment, that I would want to avoid.

Thanks for your help !

---

### Post by newb85 on 2013-06-17
I don't have much experience with it, but I think OpenBox is more along the lines of what you're looking for.

---

### Post by grimy55 on 2013-06-17
Thanks fo replying. Actually, I spent so much time to find a Linux working fine with my touchscreen without to much configuration, I do not intend to change mine. OpenELEC and XBMCbuntu are not touchscreen friendly so far. I did not know OpenBox.

Any other suggestions ?

---

### Post by newb85 on 2013-06-17
OpenBox can be installed on your Xubuntu system and set up as an option. It's the window manager used by Lubuntu, but it can be installed without the full LXDE interface.

---

