---
title: "[SOLVED] ubuntu ultimate 1.4 problems"
date: 2007-09-21
forum: Other OS Talk
---

### Post by offroad64 on 2007-09-21
When I turn on desktop effects the title bar on any window is missing.
Any one have any suggestions?

---

### Post by acowboydave on 2007-09-21
Have you tried googling "desktop effects ubuntu no title bar" several posts on the subject.

---

### Post by obscur156 on 2007-09-21
Probably the author of ubuntu ultimate can help you.
You can ask him on is own thread of ultimate,this guy is always willing to help.

[http://ubuntuforums.org/showthread.php?t=461378&highlight=ubuntu+ultimate]("http://ubuntuforums.org/showthread.php?t=461378&highlight=ubuntu+ultimate")

Good luck best regards.

---

### Post by ayenack on 2007-09-21
If you have an Nvidia card try this.

Make a backup of xorg.conf. In terminal. Make sure to use capitol "X" in all instances of "X11".

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**

**gksudo gedit /etc/X11/xorg.conf**

When xorg.conf opens add **Option         "AddARGBGLXVisuals" "True"** into the file at section screen. Like so.

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "DELL M770"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x350" "640x480"
    EndSubSection

Reeboot your comp.That should work. If this does not work you can restore xorg.conf like this. Good idea to write this down somewhere.

**sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf**

Good luck. ayenack.

---

### Post by Armadillo Kilr on 2007-10-03
if beryl is on, make sure the window manager is beryl and metacity

---

### Post by Jimmyfj on 2007-10-03
Did you remember to install the Emerald Decoration Manager? You'll find that in Synaptic.

---

### Post by K.Mandla on 2007-10-03
Moved to Other OS Talk. ;)

---

