---
title: "Screen Resolution Problem"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ultblad1 on 2008-11-03
Hi all, I just recently installed Ubuntu 8.10 (Intrepid Ibex) on my computer alongside with Vista Home Basic, and I'm experiencing some problems with Ubuntu.

My screen resolution with Ubuntu is a mere 800 by 600, and under System>Preferences>Screen Resolution the only two choices I am given for screen resolution is 800x600 and 640x480. Also, it says that my monitor is unknown.

I am currently using an Acer Aspire M1640 Desktop with the X193W LCD monitor that came with it. Vista displayed my graphics card as being the NVIDIA GeForce 7050/NVIDIA nForce 620. On Windows, the appropriate graphics driver was installed as well, and there were many selections for screen resolution.

I was running Vista with 1440x900, and would like Ubuntu to run that resolution as well. I have tried sudo gedit /etc/X11/xorg.conf and added the subsection part as shown in:

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Modes "1280x1024" "1024x768"
    EndSubSection
EndSection

Would anyone happen to know how to get Ubuntu to run 1440x900?
Much thanks!

-Toby

---

### Post by Crafty Kisses on 2008-11-03
Have you tried installing the graphics driver through "Hardware Drivers"?

---

### Post by ultblad1 on 2008-11-03
There are two options under Hardware Drivers:

NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version 177) [Recommended]

Which one should I install?

-Toby

---

### Post by slinkey1981 on 2008-11-03
Typically, I install the recommended drivers.

---

### Post by ultblad1 on 2008-11-03
Would you happen to know how to change my computer's default server? It's set to the Canadian one, but recently that one has been down. How would I change it to another one?

Thanks, Toby

---

### Post by gizmobay on 2008-11-03
I had problems with screen resolution, screen shift and google earth wouldn't work until I downloaded envyng-core from the repo. This package downloads the latest drivers for your card, compiles, and installs them.

---

