---
title: "LibreOffice Icon Descriptions Blank"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-10-20
A while back I started having a small problem with LibreOffice. I figured it was some weird little something I tweaked accidentally and that it would be fixed when I upgrade to Oneiric. Well it hasn't gone away so here it is. In the LibreOffice apps (only tested this in Writer and Draw) when you mouse over an icon in a toolbar, the is supposed to be a description/title that appears in a little box underneath it. The box appears, but the problem is that the boxes are solid black (see attached screen dump). I've messed with settings and things but nothing seems to have any affect on it. Any body know how to fix this issue or any ideas for troubleshooting?

---

### Post by putt1ck on 2011-10-21
Me too - maybe is a bug? I'm also getting a generic X for the LibreOffice application icon on the task manager while before upgrade I had the proper icon.

---

### Post by dniMretsaM on 2011-10-22
> **putt1ck said:**
> Me too - maybe is a bug? I'm also getting a generic X for the LibreOffice application icon on the task manager while before upgrade I had the proper icon.

I have this too.

---

### Post by dniMretsaM on 2011-10-23
Bump.

---

### Post by Rhizoid on 2011-10-23
Quick test: Try changing your appearance theme.

---

### Post by dniMretsaM on 2011-10-23
It does it on both the Air and Oxygen themes.

---

### Post by dniMretsaM on 2011-10-25
Bump.

---

### Post by vasa1 on 2011-10-25
> **dniMretsaM said:**
> A while back I started having a small problem with LibreOffice. I figured it was some weird little something I tweaked accidentally and that it would be fixed when I upgrade to Oneiric. Well it hasn't gone away so here it is. In the LibreOffice apps (only tested this in Writer and Draw) when you mouse over an icon in a toolbar, the is supposed to be a description/title that appears in a little box underneath it. The box appears, but the problem is that the boxes are solid black (see attached screen dump). I've messed with settings and things but nothing seems to have any affect on it. Any body know how to fix this issue or any ideas for troubleshooting?

My **guess** is that this has to do with the theme you've chosen for the OS and nothing to do with LibO *per se*.

The tooltips **for LibreOffice** are affected by the gtkrc settings. Suppose you are using the Ambiance theme(s) both for Window theme and GTK+ theme (with reference to GNOME tweak aka "Advanced Settings"), you would find the gtkrc here:
/usr/share/themes/Ambiance/gtk-2.0/gtkrc
Right at the top of that file there's a (long line) something like this:
```
gtk-color-scheme = "base_color:#555555\nfg_color:#600000\ntooltip_fg_color:#555555\nselected_bg_color:#333333\nselected_fg_color:#555555\ntext_color:#000\nbg_color:#555555\ntooltip_bg_color:#222222\nlink_color:#32fbe5"

```
You could try playing with the stuff in bold.
My tooltip looks like this:

Edit: bold doesn't show within code tags. So I'd suggest you play with "bg_color:#555555\ntooltip_bg_color:#222222" just near the end of the code (before the link_color)
2nd Edit: and maybe it's all worthless since you're using Kubuntu (which I didn't notice)

---

### Post by vasa1 on 2011-10-25
Just to mention that I'm on vanilla Ubuntu 11.10 (Unity 3D) and installed gnome-tweak-tool aka "Advanced Settings" from the USC. I have no idea how this goes with the KDE world and Kubuntu.

---

### Post by dniMretsaM on 2011-10-25
I figured out that this is a bug with the [FONT=courier new]libreoffice-kde[/FONT] package so I submitted a bug report which you can find [here]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/881740").

---

### Post by vasa1 on 2011-10-26
> **dniMretsaM said:**
> I figured out that this is a bug with the [FONT=courier new]libreoffice-kde[/FONT] package so I submitted a bug report which you can find [here]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/881740").

You can look at [this work-around]("http://www.wilderssecurity.com/showpost.php?p=1961191&postcount=1")

(and it _is_ for Kubuntu)

---

### Post by dniMretsaM on 2011-10-26
Ah, thank you! I'll add that to the bug report (it works btw).

EDIT: Added to the bug report.

---

### Post by vasa1 on 2011-10-26
> **dniMretsaM said:**
> Ah, thank you! I'll add that to the bug report (it works btw).

EDIT: Added to the bug report.

You're welcome but the thanks go to "Ocky" :)

---

### Post by dniMretsaM on 2011-10-26
> **vasa1 said:**
> You're welcome but the thanks go to "Ocky" :)

But you pointed it out to me, so you get some credit too.

---

