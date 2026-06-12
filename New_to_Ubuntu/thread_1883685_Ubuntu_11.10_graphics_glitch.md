---
title: "Ubuntu 11.10 graphics glitch?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by thelastbiscuitinthetin on 2011-11-19
I installed 11.10, everything works great, generally, and I'm one of the people who do like it. I've installed my graphics driver & 3d acceleration. Everything was fine until yesterday, when I start up, on my desktop, there are little speckles of glitch, like black dots that shift around. Then Ubuntu logs me out. When I log back in it's gone.

This happens in about 9 out of 10 startups. Any ideas what's going on? Thanks for your help ahead of time.

---

### Post by Denver Dave on 2011-11-20
I've only tried twice on my desktop, Compaq XP Presario and while 11.04 works fine (in classic mode), 11.10 does not.  11.10 is working on my Windows 7 Acer Laptop.   Might be a driver issue on the desktop, I did have an NTFS write issue with 11.10 on the laptop which has been resolved.

Not a big deal for now on the Desktop, I'm just staying with 11.04 for now.

---

### Post by thelastbiscuitinthetin on 2011-11-20
Thanks for the reply.

I'm wondering if maybe I did something by accident. I was messing around with attempting to get games to work but ultimately gave up, slapped a secondary hard drive into the computer and now I dual boot Windows. It was sometime during the last couple of days that I was doing that, that that started happening. But I can't imagine what it could be that I did. Most of what I did just involved wine.

---

### Post by thelastbiscuitinthetin on 2011-11-28
This is still occurring, I have no idea how to fix it, it's getting a little bit annoying. It's like something is crashing when I startup and it has to log out/back in to reset it. Anyone?

---

### Post by lolpenguin on 2011-11-29
Look in Xorg.log and note all the messages marked (EE) and (WW)

---

### Post by thelastbiscuitinthetin on 2011-12-02
> **lolpenguin said:**
> Look in Xorg.log and note all the messages marked (EE) and (WW)

You're speaking Greek to me. I tried to Google it but I don't know how to do that. Can you give me the command?

---

### Post by thelastbiscuitinthetin on 2011-12-07
Still happening. Afraid I might have to reinstall.

---

### Post by editheraven on 2011-12-07
Do this in terminal and post the output

```
 grep '(EE)' /var/log/Xorg.0.log && grep '(WW)' /var/log/Xorg.0.log
```

---

### Post by thelastbiscuitinthetin on 2011-12-09
Um... so that output doesn't look good.

```
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.150] (EE) Failed to load module "nv" (module does not exist, 0)
[    19.150] (EE) Failed to load module "vboxmouse" (module does not exist, 0)
[    20.036] (EE) Failed to load module "vboxmouse" (module does not exist, 0)
[    20.036] (EE) No input driver matching `vboxmouse'
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.063] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.063] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.063] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.063] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.063] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.150] (WW) Warning, couldn't open module nv
[    19.150] (WW) Warning, couldn't open module vboxmouse
[    19.151] (WW) Falling back to old probe method for vesa
[    19.151] (WW) Falling back to old probe method for fbdev
[    20.036] (WW) Warning, couldn't open module vboxmouse
[  2191.736] (WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)

```

---

