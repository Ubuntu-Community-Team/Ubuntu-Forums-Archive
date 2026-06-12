---
title: "fglrx"
date: 2011-08-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-08-14
My compliments to Alberto fglrx is at last working on my system,I tried amd beta no luck I tried other alternatives but no luck today all ok thank you Alberto maybe patience is a virtue
regards Ron

---

### Post by TrueJournals on 2011-08-14
? Do you have Unity 3D working with fglrx? What are you referencing here?

---

### Post by rbrick49 on 2011-08-14
> **TrueJournals said:**
> ? Do you have Unity 3D working with fglrx? What are you referencing here?
unity unity2d and gmome shell are all working

---

### Post by TrueJournals on 2011-08-14
Without [the black box bug](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144)? Did you do anything special, or are you just lucky? :P

---

### Post by rbrick49 on 2011-08-14
> **TrueJournals said:**
> Without [the black box bug](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144)? Did you do anything special, or are you just lucky? :P
penGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6900 Series 
OpenGL version string:  4.1.10907 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
the only thing I have noticed when logging in to unity2d is it scrolls white ,green down the screen and then launches unity2d
no black box on unity and gnome shell is ok except for top task bar very hard to see text
regards ron
just got lucky after a full reinstall
I started reinstall from kernel version 3.0.0.3

---

### Post by rbrick49 on 2011-08-15
I didnt get all that lucky unity 3d is not working compiz wants to uninstall unity

---

### Post by P-I H on 2011-08-15
I made a new amd-64 installation with daily-build 14-Aug-2011 08:49 and installed fglrx by use of Additional Drivers.
I got this fglrx status

- working with Ubuntu 2D login. Steam is working and I can play Torchlight. Problem with curser movment in the lower right corner.

- working with Gnome login, but Steam and Torchlight is not working. When starting Steam, several Steam windows are shown. In Torchlight the screen is heavily corrupted and flickers. The Nautilus meny is shown in the upper panel. The curser behaves strange in the lower right corner. The font used to explain use of some buttons are in italic and too big.

- not working with Ubuntu login. I have the #819144 bug.

---

### Post by rbrick49 on 2011-08-15
> **P-I H said:**
> I made a new amd-64 installation with daily-build 14-Aug-2011 08:49 and installed fglrx by use of Additional Drivers.
I got this fglrx status

- working with Ubuntu 2D login. Steam is working and I can play Torchlight. Problem with curser movment in the lower right corner.

- working with Gnome login, but Steam and Torchlight is not working. When starting Steam, several Steam windows are shown. In Torchlight the screen is heavily corrupted and flickers. The Nautilus meny is shown in the upper panel. The curser behaves strange in the lower right corner. The font used to explain use of some buttons are in italic and too big.

- not working with Ubuntu login. I have the #819144 bug. i just shot the lot out the window with some updates

---

