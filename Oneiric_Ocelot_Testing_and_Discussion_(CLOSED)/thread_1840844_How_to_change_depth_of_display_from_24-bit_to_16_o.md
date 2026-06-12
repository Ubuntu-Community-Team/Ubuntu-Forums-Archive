---
title: "How to change depth of display from 24-bit to 16 or 32?"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nutznboltz on 2011-09-08
I am testing Oneiric on QEMU guests and they default to 24-bit X display.

How can I change that to 24-bit to 16 or 32 for testing?

Current tickets:
[https://bugs.launchpad.net/bugs/843448](https://bugs.launchpad.net/bugs/843448)
[https://bugs.launchpad.net/bugs/844764](https://bugs.launchpad.net/bugs/844764)

Thanks

---

### Post by nutznboltz on 2011-09-09
Used to be there was a "-bpp" option to X

Now there is:

```
sudo X -help 2>&1 | egrep 'bpp|depth'
-pixmap24              use 24bpp pixmaps for depth 24
-pixmap32              use 32bpp pixmaps for depth 24
-depth n               set colour depth. Default: 8
-fbbpp n               set bpp for the framebuffer. Default: 8

```

I really do not believe the part about the default color depth being 8.

Maybe setting

xserver-command="X -depth 32"

But I haven't determined if "xserver-command" supports spaces and command arguments or not.

---

### Post by nutznboltz on 2011-09-09
The X server can be started from the console window command line  with

sudo X -depth 16

I tried "-depth 32" but this particular graphics hardware does not support that.

Adding
xserver-command="X -depth 16"
to /etc/lightdm/lightdm.conf fails by not starting X at boot.

Adding
xserver-command="X"
fails the same way too.

Maybe they should call it lightondocuemenationandsupportdm?

---

### Post by nutznboltz on 2011-09-09
I took the quotes out and it just worked!

in /etc/lightdm/lightdm.conf

```
xserver-command=X -depth 16
```

---

### Post by seeker5528 on 2011-09-09
> **nutznboltz said:**
> I am testing Oneiric on QEMU guests and they default to 24-bit X display.

There is no 32 bit color setting, color is 24 bit, If your video hardware and driver supports it the drivers also use 8 bits for alpha, 24+8=32.

There used to be some settings to enable/disable the +8 for some of the drivers but you probably have to look at the configuration options that are specific to your hardware/driver to find that out.

It seems unlikely any of the drivers these days would fail to do the +8 when set to 24 bit color with the possible exception of the VESA and VGA drivers, since they are generic, or you are using some old video hardware that didn't support it, but that's going back a ways.

Later, Seeker

---

