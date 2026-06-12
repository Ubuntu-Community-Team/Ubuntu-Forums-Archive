---
title: "Easy way to increase fonts in 2D session?"
date: 2011-08-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-08-02
Many of you know that my vision is rather poor and I'm now doing some of my iso-testing on a box that lacks 3D support so I have to run unity/ubuntu-2D.

I commonly change my resolution from 1680x1050 to 1440x900 and then change all fonts to 11 with a dpi of 106 so I can see what I'm doing.

I'll be dogged if I can find a way to change the fonts in a 2D session. Anyone know how to do that?

---

### Post by kansasnoob on 2011-08-02
Well oddly if I just let the box boot into the "Ubuntu" session things look much better.

Could someone remind me of the command to see what session is actually running?

I know in Natty this P4M800 would default to the classic DE w/o effects.

---

### Post by MacUntu on 2011-08-02
Two ways:
1. the trash launcher item looks different in Unity 2D (line art), and
2. You cannot drag launcher items outside of the launcher in Unity 2D.

On the command-line you could probably just check if "pgrep "unity$"" returns something (then you are using Unity).

As for the fonts: you shouldn't change the DPI setting. The DPI setting is used by the font renderer to create pretty fonts for your screen resolution/screen size and therefore should match those. Just change the font size instead (plus, AFAIK there is no DPI setting in GNOME 3, just a scaling factor, see below).

To do this in Unity(-2D) I'm still using "dconf-editor" from the "dconf-tools" package.

Keys to change are under "org.gnome.desktop.interface" (there you'll also find the font scaling factor called "text-scaling-factor").

---

