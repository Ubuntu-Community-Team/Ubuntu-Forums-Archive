---
title: "Ati drivers and Xv."
date: 2006-02-19
forum: Outdated Tutorials &amp; Tips
---

### Post by theD3viL on 2006-02-19
I searched today every thread about this..but didnt find anything. So, if you have problems with Xvideo (multimedia system selector tester dont work, or mplayer xv dont work), you must append this to xorg.conf at section Device:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Driver          "fglrx"
        BusID           "PCI:2:0:0"
[I][B]    Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"[/B][/I]



Hope it will work..it works for me \\:D/ 



Have a nice day :)

---

### Post by Turgon on 2006-03-21
Thank you, that solved my videoproblem:D

---

### Post by danhm on 2006-03-21
Does that disable OpenGL?

---

### Post by zi99y on 2006-03-25
thanks, this is very useful - enabled me to use KXMame in XV Fullscreen mode. 

cheers

---

### Post by lazyd2 on 2006-03-26
More info [http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

---

