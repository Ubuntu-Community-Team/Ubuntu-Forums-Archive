---
title: "Need Help Setting Up New Monitor / Video Output"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by nina_aoki on 2008-04-26
Hi guys --

I need some help in setting up my system to work with my new monitor.

I just added a 20" Widescreen Flat-Pannel display to my Ubuntu rig but I cannot seem to get the resolution above 1024 x 768 (which is where it was running with my old CRT monitor)

The video board is an ATI Radeon X300 SE - which is working fine, and I believe it should be capable of higher resolutions.  I have desktop effects enabled and working with Envy and the driver seems to be functioning without any problems -- but rather than being able to get the maximum resolution possible, I have what seems to be more like a really wide stretched out display.  

I'm using standard VGA-out of the video board to the VGA-in on the monitor.

Would someone be able to help me out with this or point me in the right direction?  I tried to use the 'Detect Displays' option on the Monitor Resolution control, but all I'm seeing is something which says "Cloned Output"  :eek:

Thanks so much.

- nina

---

### Post by Steve H on 2011-05-02
Sometimes the proprietary driver can incorrectly detect the available resolutions.

What do you get when you type the following in terminal:

```
xrandr output
```


EDIT: Addition

Also have a look [here]("http://ubuntuforums.org/showthread.php?p=8595940"). Hope that helps

---

