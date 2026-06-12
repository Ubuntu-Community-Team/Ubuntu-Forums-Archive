---
title: "Video card not working."
date: 2012-02-20
forum: New to Ubuntu
---

### Post by P-rench on 2012-02-20
I installed a new video card in my computer and when I booted up the color was all off ( mainly like blues and greens were the only present colors) and ubuntu told me I had some video card issues, most likely drivers. So I went into low graphics mode and downloaded the drivers, restarted, but still no luck, colors are still all messed up. Is there some setting I have to change in the BIOS? Or something I'm doing wrong with the video card installation in ubuntu? My motherboard has onboard video as well so one other guess I have is that perhaps there is some kind of interference between the onboard video and the video card, possibly a setting in BIOS? Any help would be greatly appreciated.

---

### Post by grahammechanical on 2012-02-20
What type of connection are you using between the computer and the monitor? VGA, DVI, or HDMI? 

Have you considered that the fault may be due to a damaged cable? Some of the wires in the cable carrying the colour signal information. If one of them gets broken then that colour is absent from the mix and the other colours predominate.

Another thing to consider. If you are using proprietary drivers than they come with their own settings manager. You can use that to Detect Displays to make your that the monitor is being run at the correct settings. You may even be able to make some adjustments to the video signal.

My Nvidia X-Server Settings utility has a setting for X Server Colour Correction and I can correct each of the three colours. I have never messed around with this so I can not says what the results will be.

Regards.

---

### Post by P-rench on 2012-02-20
Booya! Changed the cable and now everything works! Thanks!

---

