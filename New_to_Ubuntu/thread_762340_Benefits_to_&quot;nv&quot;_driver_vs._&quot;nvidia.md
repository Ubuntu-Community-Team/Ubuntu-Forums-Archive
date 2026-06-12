---
title: "Benefits to &quot;nv&quot; driver vs. &quot;nvidia&quot; driver in xorg.conf"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by meditatingfrog on 2008-04-22
Hi all:

I've spent some time on getting my Geforce2 GTS card working with the nvidia legacy driver.  It seems the only driver that works is the nv driver.  I tried envy, I also tried downloading and installing the driver from Nvidia's website.  I get the cryptic message "Failed to load the NVIDIA kernel module!" in the log file when I change the driver from "nv" to "nvidia" in the xorg.conf file...

My question is, what are the benefits of using the nvidia driver over the nv driver?  Will there be 2d acceleration?  Less CPU utilization during "regular" tasks, like web browsing? Or is this an option for games and other opengl programs?

I appreciate the help, and I'm enjoying the software :).

---

### Post by Kingsley on 2008-04-22
nv doesn't support 3D acceleration, but nvidia does.

---

### Post by HyperHacker on 2008-04-22
I believe I heard nv has trouble with multi-monitor setups, but don't quote me on that. nvidia does it fine, once you get it working (tip: run nvidia-settings).

---

### Post by Barney Oatmeal on 2010-06-04
Pardon, old thread, I know, but where can I find the "NV" driver, please?

---

