---
title: "2 questions, video card and wireless networks."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Naltima on 2008-11-26
I recently installed Ubuntu 8.10 for the first time.  Now I have 2 problems, first of all the wireless networks only show up whenever they feel like it.  I have about 10 different routers in range most of the time all of them will show up, but sometimes like right now for example none of them show up.  Not sure what to do.

The second questions is, I have an Nvidia 8500 graphics card.  I tried to install the drivers by using the drivers that Ubuntu found however I got an error.  I then installed Envy and but whenever I attempted to install the drivers using that I got some sort of an error as well, however it let me uninstall the drivers, and then I was able to install the drivers that were found by Ubuntu.

However, when I reboot the system a screen popped up stating that I can only boot up my system in low graphics mode, or return to my previous settings.  And whenever I go into the Nvidia Setting I get this message.  "YOu do not appear to be using the Nvidia x driver.  Please edit your X configuration file (Just run 'nvidia-xconfig' as root), and restart the x server.  

:confused:

---

### Post by Xiong Chiamiov on 2008-11-27
I can't say anything about the wireless.

NVIDIA drivers were broken in Ubuntu last time I used it, but that was Hardy, so perhaps they're fixed in Intrepid.  If you can tell us what messages you got exactly, then we'll be much more able to help.  All I can tell from your current information is that you did indeed make a change to your xorg.conf, specifically one that enabled the vesa driver (probably), rather than nvidia, which is what you want.

I'd recommend posting your two issues in separate threads, so that they can be dealt with separately, since they are not related.

---

