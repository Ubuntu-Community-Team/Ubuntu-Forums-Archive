---
title: "Pixelated video in VLC and Totem"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by ECUPirate on 2008-10-26
I installed ubuntu 8.04 on my htpc Friday as a dual boot with xp media center. Everything works great with the exception of the video being very pixelated when using VLC or Totem. I have a gigabyte ga-ma69gm-s2h mobo with onboard ati1200 series graphics and I installed the proprietary ati drivers.

Thank you.

---

### Post by SuperSonic4 on 2008-10-26
I assumed you rebooted after installing the ATI drivers :p

What is the video resolution that you're trying to play?

---

### Post by ECUPirate on 2008-10-26
I did reboot. the computer is connected to a 32" lcd with the resolution set at 1280x768. Everything is very clear except when I go to play the video.

---

### Post by SuperSonic4 on 2008-10-26
What resolution is the video itself at? You could get pixellation if you're playing a small video on a big screen

---

### Post by Amazona aestiva on 2008-10-26
Greetings

As for VLC, you can choice the video device(driver) to use.
Go to settings->settings, now tick the advanced stuff at the bottom right hand corner and navigate to Video->Output Module Try choosing annother one.

Regards

---

### Post by ECUPirate on 2008-10-26
Good call, in totem the video dimensions are shown in the properties as 720x480. This is ripped dvd content that plays perfectly clear in xp media center on the same box/monitor same settings of 1280x768. Is there a way to change this in totem?

---

### Post by Amazona aestiva on 2008-10-26
> **ECUPirate said:**
> Good call, in totem the video dimensions are shown in the properties as 720x480. This is ripped dvd content that plays perfectly clear in xp media center on the same box/monitor same settings of 1280x768. Is there a way to change this in totem?

Regardless to those numbers Totem should produce better quality.

Well I don't use Totem, but you might try installing the xine backend of it. It could help if the problem is releated to its codecs.

Regards

---

### Post by ECUPirate on 2008-10-26
Thanks for the tip, i'm a complete noob to ubuntu, how would I install the xine version?

---

### Post by Amazona aestiva on 2008-10-26
> **ECUPirate said:**
> Thanks for the tip, i'm a complete noob to ubuntu, how would I install the xine version?

Just copy and paste this into your terminal:
```
sudo apt-get install totem-xine
```
It doesn't have a quicklunch icon as the one with gstreamer so start it from terminal:
```
totem-xine
```
BTW, the default one is:
```
totem-gstreamer
```

Regards

---

### Post by SunnyRabbiera on 2008-10-26
> **ECUPirate said:**
> Thanks for the tip, i'm a complete noob to ubuntu, how would I install the xine version?

go to synaptic by going to system> administration> synaptic package manager
search for totem-xine
Installation should be easy, but if you have totem gstreamer its best to remove it.
I find the xine version is better as gstreamer isnt that great, you may also want to check out medibuntu as well to get extra codecs as gstreamer doesnt cover everything that well

---

### Post by Amazona aestiva on 2008-10-26
> **SunnyRabbiera said:**
> go to synaptic by going to system> administration> synaptic package manager
search for totem-xine
Installation should be easy, but if you have totem gstreamer its best to remove it.
I find the xine version is better as gstreamer isnt that great, you may also want to check out medibuntu as well to get extra codecs as gstreamer doesnt cover everything that well

I agree, and that's why I prefer VLC. (It has built-in codecs)

---

### Post by ECUPirate on 2008-10-26
Thank you very much. I'll post the results.

---

### Post by ECUPirate on 2008-10-26
I uninstalled gstreamer and installed xine. Pixelation is better, but still not as good a picture as media center. Now I'm getting flicker in the video though.

---

### Post by Amazona aestiva on 2008-10-26
> **ECUPirate said:**
> I uninstalled gstreamer and installed xine. Pixelation is better, but still not as good a picture as media center. Now I'm getting flicker in the video though.

I think that must be an ati driver issue, or something like that, because it's hardly possible to have three different error with these players.

How did you install your graphics card? Have you used envyng?

---

### Post by ECUPirate on 2008-10-26
When I installed ubuntu it prompted me to install the proprietary drivers for ati. the original install of the onboard graphics was done when i built the computer and installed the drivers from the ati website.

---

### Post by Amazona aestiva on 2008-10-26
> **ECUPirate said:**
> When I installed ubuntu it prompted me to install the proprietary drivers for ati. the original install of the onboard graphics was done when i built the computer and installed the drivers from the ati website.

Well, if I were you I would try out EnvyNG too. There are people who love it.

Regards

---

