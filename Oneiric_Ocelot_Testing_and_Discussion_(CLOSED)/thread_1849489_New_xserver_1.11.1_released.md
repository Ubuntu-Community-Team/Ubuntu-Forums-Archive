---
title: "New xserver 1.11.1 released"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-24
The new point release came quite fast this time.
The xserver 1.11.1 fixes some major bugs.
After this, nvidia proprieatary drivers can be expected to work better.

The announcement:
[http://lists.freedesktop.org/archives/xorg-announce/2011-September/001736.html](http://lists.freedesktop.org/archives/xorg-announce/2011-September/001736.html)

So, waiting for xorg-edgers to build this one.):P

---

### Post by VinDSL on 2011-09-24
> **Harry33 said:**
> So, waiting for xorg-edgers to build this one.):P
Thanks, Harry!  This is good to know.

I miss xorg-edgers.  :(

Maybe, Unity will work with it installed, on the next go-round...

---

### Post by Harry33 on 2011-09-26
The new xserver 1.11.1 is now in Xorgs-Edgers PPA.

If you are using xserver 1.11, you should upgrade to this bug fix version.

> 
**== Description ==**

xorg-server 1.11.1 contains two brownbag fixes for issues found in 1.11.0.
With this release, we are "resetting" the standard 6 week release cycle.
1.11.2 RC1 will be out in 3 weeks, and the branch is open for nominations for
general bug fixes.  See the wiki (link below) if you are unfamilair with the
process.

**== Changes since 1.11.0 ==**

Aaron Plattner (2):
      xfree86: Bump extension ABI version to 6.0
      fb: Rename wfbTriangles and wfbTrapezoids
Jeremy Huddleston (1):
      configure.ac: Version bumped to 1.11.1


---

### Post by dino99 on 2011-09-26
installed from edgers:

- xserver 1.11.1
- nvidia 285

X fail to start: need to add "IgnoreABI" "true"

then jockey cant activate the driver: so from FF, switching tabs, scrolling make it freezing for a while

So i downgrade again.

---

### Post by Harry33 on 2011-09-27
> **dino99 said:**
> installed from edgers:

- xserver 1.11.1
- nvidia 285

X fail to start: need to add "IgnoreABI" "true"

then jockey cant activate the driver: so from FF, switching tabs, scrolling make it freezing for a while

So i downgrade again.

Try purging Jockey, that application really isn't necessary at all. It has a lot of issues, anyway.
I installed nvidia-current 285.03 (edgers PPA) by manually downloading it and then
    sudo dpkg -i *.deb.
I do not have probelms with FF.
Occasionally booting does not start Gnome-shell, but gnome-panel (fallback),
but then a reboot helps.

---

### Post by dino99 on 2011-09-27
> **Harry33 said:**
> Try purging Jockey, that application really isn't necessary at all. It has a lot of issues, anyway.
I installed nvidia-current 285.03 (edgers PPA) by manually downloading it and then
    sudo dpkg -i *.deb.
I do not have probelms with FF.
Occasionally booting does not start Gnome-shell, but gnome-panel (fallback),
but then a reboot helps.

Ok will try again, thanks

---

### Post by Harry33 on 2011-09-27
Those planning to use Unity with xserver 1.11.1,
please look into this bug (860707) report:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707)

---

### Post by VinDSL on 2011-09-27
> **Harry33 said:**
> Those planning to use Unity with xserver 1.11.1,
please look into this bug (860707) report:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/860707)
Thanks, Harry!  I submitted a "Me Too"...  ;)

Also, I just posted this is 'the other thread':

> **VinDSL said:**
> I tried the new Xserver 1.11.1, last night, and still no joy!

As usual, no panels in Unity, and now GS is acting janky too.

For instance, doing a Search in the GS Dash Home (Activities or whatever they call it) results in an unresponsive desktop.  I have to Crtl-Alt-F1 out & reboot.

Xserver 1.11 was working far better (for me) than 1.11.1, but there have been 100's of changes to Oneiric since last week, soooo... those changes might have goofed things up.

Heh!  I think I'm getting too far ahead of the curve, dabbling with Xserver upgrades.

Might as well add it to this thread too...  :)

---

