---
title: "How can I increase screen resolution higher than 800x600"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by steelmole on 2008-08-22
I go to system->preferences->screen resolution and I only have options of 800x600 and lower.  I used to be able to get higher resolutions.  In between I tried to install another graphics card and I have now removed it (ubuntu didn't like dual monitors).  How can I get a full screen resolution on integrated graphics again?

---

### Post by tangibleorange on 2008-08-22
> **steelmole said:**
> I go to system->preferences->screen resolution and I only have options of 800x600 and lower.  I used to be able to get higher resolutions.  In between I tried to install another graphics card and I have now removed it (ubuntu didn't like dual monitors).  How can I get a full screen resolution on integrated graphics again?

go to system -> Administration -> Hardware drivers and see whether the restricted driver is active. also, could you post the output of:

```
xrandr -q
```

---

### Post by mr.moch on 2008-08-22
Try changing your refresh rate.  Mine works with 60Hz, but it may be different.  I have:

1024x768
              Normal <--i think it's rotation
60 Hz

My monitor, according to Windows is "multiple monitors".  However, I only use one monitor.

---

### Post by rockerphil on 2008-08-22
my advice, i know it works for me, run this code, it's to reconfigure resolution and video card driver settings

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

hope it helps,

Phil

---

### Post by alienexplorers on 2008-08-22
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
[COLOR="Red"]    Option         "AddARGBGLXVisuals" "True"
    Option         "metamodes" "1280x1024_65 +0+0"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Set the metamode to what ever screen res you want.  I use 1280 x1024 at 65 hz.

---

### Post by alienexplorers on 2008-08-22
Sorry Double Post

---

### Post by Dave Otter on 2008-08-22
alt + F2 >> sudo  displayconfig-gtk 

  click on Monitor model

---

