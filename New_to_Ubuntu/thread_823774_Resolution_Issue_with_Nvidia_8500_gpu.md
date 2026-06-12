---
title: "Resolution Issue with Nvidia 8500 gpu"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by GotEmRunnin on 2008-06-09
Hey guys I'm looking for some help.  I recently installed ubuntu on my pc.  I have a nvidia 8500gt and after installtion of the os I was able to update all the drivers correctly.  However after reboot my res is stuck at 640x480.  I think the problem is ubuntu can't recognize my monitor.  how do I fix this?

Thanks for the help

---

### Post by cprofitt on 2008-06-09
I had a similar problem though it was with a dual monitor setup. The problem was the monitor's refresh rate not being recognized and thus the default resolution was 'forced' and I could not change it.

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: **1280x1024_60** +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The critical part is in bold above... this is what forced the refresh rate and allowed me to change the resolution on that monitor.

---

### Post by GotEmRunnin on 2008-06-10
Got it.  thanks a lot.  Huge difference.  If only I could do majority of my gaming on ubuntu I wouldn't have any desire to dual boot. :)

---

### Post by cprofitt on 2008-06-10
Not a problem -- glad to be of help.

---

