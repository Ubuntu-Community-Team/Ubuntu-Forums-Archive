---
title: "More Nvidia problems."
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-07-15
Alright then.

I'm posting this as a contiuation of this thread, since it's been marked as solved:

[http://ubuntuforums.org/showthread.php?t=1804394](http://ubuntuforums.org/showthread.php?t=1804394)

The solution to the problem was to blacklist the Nouveau driver in "/etc/modprobe.d/blacklist.conf". However, this solution did not work for me. After blacklisting, the Nouveau driver still loaded, and when in Jockey GTK, the Nvidia driver is listed as "activated but not currently in use".

Also, whenever the Nvidia driver is installed, I am booted back to Unity 2D. When I uninstall, Unity 3D is used under Nouveau.

I'm not sure what the problem is.

---

### Post by vhaarr on 2011-07-15
Have you tried uninstalling the nouveau driver, then reinstalling nvidia - making sure initramfs is regenerated?

---

### Post by sparker256 on 2011-07-15
> **vhaarr said:**
> Have you tried uninstalling the nouveau driver, then reinstalling nvidia - making sure initramfs is regenerated?
I have tried that and after a reboot still boots into Unity 2d.

Bill

---

### Post by PhantmKllr on 2011-07-15
> **sparker256 said:**
> I have tried that and after a reboot still boots into Unity 2d.

Bill
Same here, I just get Unity 2D (which sucks, btw).

---

### Post by PhantmKllr on 2011-07-18
Anyone know if this problem is still going on?

I switched back to 11.04 for the time being (because I can't live without my accelerated graphics! :D ), but I'd really like to see what's been happening with Oneiric.

---

### Post by mc4man on 2011-07-18
Have you tried forcing unity to start to see what happens?

To do so add this line to /etc/environment and then reboot
```

UNITY_FORCE_START=1
```
I don't need to but to show - (from .xsession.errors
> Loading X session script /etc/X11/Xsession.d/99x11-common_start
Warning: UNITY_FORCE_START enabled, no check for unity or compiz support.
Make sure you know how to remove/revert if need be

---

### Post by sparker256 on 2011-07-18
> **PhantmKllr said:**
> Anyone know if this problem is still going on?

I switched back to 11.04 for the time being (because I can't live without my accelerated graphics! :D ), but I'd really like to see what's been happening with Oneiric.
I reinstalled a alpha 2 and all fine again after the updates.

Bill

---

### Post by PhantmKllr on 2011-07-19
> **sparker256 said:**
> I reinstalled a alpha 2 and all fine again after the updates.

Bill

Glad that you got everything worked out! :D

Your post prompted me to re-install 11.10 as well (upgrade from 11.04), yet, alas, after the upgrade process was completed, the problem persisted.

> **mc4man said:**
> Have you tried forcing unity to start to see what happens?

To do so add this line to /etc/environment and then reboot
```

UNITY_FORCE_START=1
```
I don't need to but to show - (from .xsession.errors

Make sure you know how to remove/revert if need be

I tried this and sadly, it didn't work.

I'm tempted to go crying back into the arms of the Narwhal, but I really don't want to wipe my hard drive again, so... Yeah.

Anyone else still having this problem??

---

### Post by VinDSL on 2011-07-19
Hate to be a pity-party-pooper, but...

Why don't just run Nouveau drivers and forget nVidia??!!?

That's what I did, and The Borg is treating me very nicely.

```

$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Tue Jul 19 02:09:16 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-5-generic
unity 4.2.0
nvfx_screen_get_param:94 -  Warning: unknown PIPE_CAP 29
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 7.11-devel

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

Unity supported:          yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/


```

---

### Post by PhantmKllr on 2011-07-19
> **VinDSL said:**
> 
Why don't just run Nouveau drivers and forget nVidia??!!?


I suppose I don't really have a choice.

But I'm not marking the thread as solved just yet... :popcorn:

---

### Post by VinDSL on 2011-07-20
> **PhantmKllr said:**
> I suppose I don't really have a choice.

But I'm not marking the thread as solved just yet... :popcorn:
I don't blame you.  I keep waiting for the nVidia payoff too...

I dunno.  I've been running the latest nVidia drivers for years.

nVidia is always promising to do something tomorrow.  Tomorrow comes, but you're left with nothing but an empty promise.

Nouveau, on the other hand, doesn't promise you anything.  And, that's what you traditionally get - nothing - same as nVidia.

The thing is...

In the last month or so, Nouveau must have gotten lucky.  Even a broken clock is right, twice a day!

On this aging machine (see sig) Nouveau drivers have suddenly displayed as much 3D goodness as the latest nVidia drivers - with 1/3 the RAM usage.

My attitude is:  Hurray for Nouveau (the underdog) & F* nVidia (and their lies)!  :D

BTW, if you decide to test Nouveau drivers for a while, make sure to install "libgl1-mesa-dri-experimental" & "nouveau-firmware".

Makes a difference, but I cannot tell you why.  It just does - I promise you... just like nVidia.  ;)

---

### Post by BigSilly on 2011-07-20
Sorry to barge into your discussion. I'm not running Oneiric, but I am keeping an eye on things as I'm an Nvidia user too, but had no end of Nvidia-related issues with Natty that led me ultimately to switching distros after years of happy Ubuntu use. Unity is fantastic, but there are so many bugs that I simply could not use it. This greatly saddened me.

But I have found generally, that almost every distro I've tried other than Ubuntu works fine with the proprietary driver. I'm not sure why this should be, just a general observation but very clear. I'm currently running both openSUSE 11.4 with Gnome 3, and PCLinuxOS 2011 KDE4, both with Nvidia's own driver, and both trouble free.

That said, I am extremely pleased to read that the Nouveau driver is improving. Would you say that it is now capable enough to run some native 3D gaming (I'm thinking Penumbra, Amnesia, World of Goo), and stable? I would love to move back to Ubuntu soon to replace my Windows 7 install, but as it stands I just can't. The Nouveau driver represents my best chance of being able to run Ubuntu again, I fear.

Thanks. :)

---

### Post by PhantmKllr on 2011-07-20
> **VinDSL said:**
> 
I don't blame you.  I keep waiting for the nVidia payoff too...

I dunno.  I've been running the latest nVidia drivers for years.

nVidia is always promising to do something tomorrow.  Tomorrow comes, but you're left with nothing but an empty promise.

Nouveau, on the other hand, doesn't promise you anything.  And, that's what you traditionally get - nothing - same as nVidia.

The thing is...

In the last month or so, Nouveau must have gotten lucky.  Even a broken clock is right, twice a day!

On this aging machine (see sig) Nouveau drivers have suddenly displayed as much 3D goodness as the latest nVidia drivers - with 1/3 the RAM usage.

My attitude is:  Hurray for Nouveau (the underdog) & F* nVidia (and their lies)!  :D

BTW, if you decide to test Nouveau drivers for a while, make sure to install "libgl1-mesa-dri-experimental" & "nouveau-firmware".

Makes a difference, but I cannot tell you why.  It just does - I promise you... just like nVidia.  ;)


Don't get me wrong, I'd rather use the open source alternative anyway...

...and you're right, Nouveau has improved, but it's still not as good as the Nvidia drivers.

> **BigSilly said:**
> 
Sorry to barge into your discussion. I'm not running Oneiric, but I am keeping an eye on things as I'm an Nvidia user too, but had no end of Nvidia-related issues with Natty that led me ultimately to switching distros after years of happy Ubuntu use. Unity is fantastic, but there are so many bugs that I simply could not use it. This greatly saddened me.

But I have found generally, that almost every distro I've tried other than Ubuntu works fine with the proprietary driver. I'm not sure why this should be, just a general observation but very clear. I'm currently running both openSUSE 11.4 with Gnome 3, and PCLinuxOS 2011 KDE4, both with Nvidia's own driver, and both trouble free.

That said, I am extremely pleased to read that the Nouveau driver is improving. Would you say that it is now capable enough to run some native 3D gaming (I'm thinking Penumbra, Amnesia, World of Goo), and stable? I would love to move back to Ubuntu soon to replace my Windows 7 install, but as it stands I just can't. The Nouveau driver represents my best chance of being able to run Ubuntu again, I fear.

Thanks. :)


IDK, perhaps there is something wrong with your graphics card (or it's not supported by the Nvidia driver), because I have worked with Nvidia cards and Ubuntu for a while, and I've never had any problems.

As to your gaming inquiry; I had Red Eclipse ([http://www.redeclipse.net/]("http://www.redeclipse.net/")) installed before upgrading to Oneric. Running under Natty, with the latest available Nvidia drivers, the average FPS ranged from 175-200 (and that's with all graphics settings set to high :cool: ). Under Oneric, with Nouveau and Experimental 3D enabled, FPS ranges from 135-180 (same settings as under the Nvidia drivers), and the graphics are somewhat distorted, such as textures flashing on and off, etc.

So as you can see, Nouveau is making some progress, but it has still a long way to go.

---

### Post by PhantmKllr on 2011-07-23
As of the final 3.0 kernel release, the Nvidia drivers are now working again. :D

---

### Post by VinDSL on 2011-07-23
> **PhantmKllr said:**
> As of the final 3.0 kernel release, the Nvidia drivers are now working again. :D
First impression:  Ask the OP to define "working".

Second impression:  Test the theory yourself.  :D

Okay, here goes nothing.  Wish me luck!

---

### Post by VinDSL on 2011-07-23
Okay, part-1 out of the way:

```

$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Sat Jul 23 00:51:47 MST 2011
Ubuntu oneiric (development branch)
**[COLOR="Red"]Linux 3.0.0-0300-generic[/COLOR]**
unity 4.4.0
nvfx_screen_get_param:94 -  Warning: unknown PIPE_CAP 29
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B
OpenGL version string:  2.1 Mesa 7.11-devel

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

Unity supported:          yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

Which nVidia drivers did you use?!?!?

---

### Post by VinDSL on 2011-07-23
Harry recommends 280.04 X-Swat, so that's what I installed:

```

$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Sat Jul 23 01:18:50 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-0300-generic
unity 4.4.0
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  **[COLOR="Red"]2.1.2 NVIDIA 280.04[/COLOR]**

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

Unity supported:          yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

```

nVidia is indeed working, but...

RAM usage went from 288MB (Nouveau) to 688MB (nVidia) - sitting idle at my desktop, sooo...

Guess I'll tough it out, for a day or two, but I have a feeling I'll be reverting to Nouveau drivers...  ;)

---

### Post by PhantmKllr on 2011-07-23
> **VinDSL said:**
> First impression:  Ask the OP to define "working".

Second impression:  Test the theory yourself.  :D

Okay, here goes nothing.  Wish me luck!
:lolflag:

By "Working", I meant that the Nouveau drivers are no longer hijacking my video card before the Nvidia drivers could load.

And I installed nvidia-current (I always install nvidia-current ;) ).

Also, I noticed the spike in RAM consumption as well, but I have 8gb, so I don't really care that much. :)

---

