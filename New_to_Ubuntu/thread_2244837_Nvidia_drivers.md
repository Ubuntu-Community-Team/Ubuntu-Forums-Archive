---
title: "Nvidia drivers"
date: 2014-09-19
forum: New to Ubuntu
---

### Post by Sjogun on 2014-09-19
So, I did the system update to 14.04, and I am having some of the same problems I had while trying to install nvidia drivers in 12.04.  I have to boot in failsafe graphics mode, which I'm perfectly happy with.  It seems to not have all the features, but the stuff I need it to do works(media server).  I don't understand why in failsafe mode I am still using the nvidia driver 304.117 and the display looks great on my hdtv.  When I boot normally I get a blank screen, with no keyboard functions, and I know it's not fully booting because my squeezebox does not wake up.  I've heard there's some issues with 14.04 and nvidia card, is nvidia coming out with new drivers for 14.04?  For now I'll just leave it in recovery mode, because it seems to be the same. The only difference I see is I don't have the 4 screen workspace(cool but I can live without it). Any information would be very appreciated.  
Thanks

---

### Post by grahammechanical on 2014-09-19
Can you please make something clear. Are to loading in failsafeX mode or are you using Recovery>Resume? The two are different. I have found failsafeX to be broken. Although I have not tested it for awhile. Anyway, it is only meant to be used to get us to a desktop where we can fix the problems with the video driver.

Recovery>Resume will load Ubuntu using an open source video driver call llvmpipe. Its main purpose is to give an approximation of the Unity 3D user interface when a graphic adapter cannot do hardware 3D acceleration. But it is also used when we choose Recovery>Resume. This is useful for when there are problems with a proprietary video driver.

If you open About This Computer the Details page will say if you are using llvmpipe. My advice would be to use System Settings>Software and Updates>Additional Drivers tab to activate another video driver. First try the full open source video driver (Nouveau). If that loads to a desktop without using Recovery mode then try a proprietary video driver.

Regards.

---

### Post by Sjogun on 2014-09-19
Yes, dirty failsafex doesn't work.  I'll look at my settings tonight.  Anyone have nvidia 304.117 working properly on 14.04?

---

### Post by Sjogun on 2014-09-20
I looked in software> additional drivers my geforce 6200 was using the 304.117(recommended) drive.  Changed to nouveau driver, restarted and it booted up.  I still don't know if it booted fully or back to recovery mode, but it didn't go to grub automatically.  Did ubuntu do away with the 4 screen desktop feature?   I guess I'll keep it like this until I hear if a updated driver from nvidia.

---

