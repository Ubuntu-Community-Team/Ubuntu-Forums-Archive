---
title: "terminal commands"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by 1scorpio on 2008-04-27
New to the terminal

need the command that lists system and the command for listing graphic settings.

TIA
1scorpio

---

### Post by SuperSon!c on 2008-04-27
for hardware:

```
sudo lshw
```

---

### Post by howlingmadhowie on 2008-04-27
what do you mean by listing the system?

to find the resolution and color depth, type alt+f2 and enter "xwininfo". then click on the desktop background

on my computer, this results in the following: 

```

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x1000023 "Bureau"

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1024
  Height: 768
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1024x768+0+0

```

is that what you were looking for?

---

### Post by kavon89 on 2008-04-27
```
sudo lshw -class display
```

Lists display devices, just regular lshw lists all hardware.

---

### Post by bodhi.zazen on 2008-04-27
This is a popular site as well :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by 1scorpio on 2008-04-27
> **bodhi.zazen said:**
> This is a popular site as well :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)
Thank you all for these very helpful answers. Special thanks to you bodhi.zazen this is a great link

---

### Post by slimx3m on 2008-04-27
that link is a really good link if you just started to use linux.  it helps a lot.

---

