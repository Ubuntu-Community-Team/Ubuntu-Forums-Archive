---
title: "Format not supported"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Blue Gene on 2012-03-08
I burned the 11.10 iso onto my cd. The cd works perfect I have used it on two different computers.
But on my other desktop computer it has
Windows Server 2000
X86 Family Model 8 Stepping
10
At/At Compatible
523824,Kb Ram
When the 11.10 iso cd boots it does the loading... for about 2-5 minutes then it goes black and a screen comes up with Format Not Supported.
Any ideas on how to surmise this issue?

---

### Post by papibe on 2012-03-08
Is it "Family 4" or "Family 6"?

If it's 4 (80486DX4), I'm afraid it is not supported. In that case, you may need to find a different distribution.

Regards.

---

### Post by Blue Gene on 2012-03-08
X86 Family Model 8 Stepping

it is family 6

---

### Post by Blue Gene on 2012-03-08
Any ideas?

---

### Post by pavi_elex on 2012-03-09
copy it in pen drive and try to use usb boot. 
if you are still facing the problem, it means that iso is not written well.

---

### Post by forrestcupp on 2012-03-09
I'd say the type of media you burned the iso to isn't supported in the optical drive you're trying to load it from. Did you burn it to a DVD? Or maybe you used a CD+R or CD-R media, and that drive is old enough that it only supports one or the other. Also, a lot of old drives that are not CD writers will not support rewritable CDs (CD+RW), so you may need to use a write-once CD (CD+R) instead, if that's what you used.

If it has a USB port, then try the Pen Drive option. If you can't boot to USB, then you need to figure out what types of media your drive supports, and use that kind.

---

### Post by 3rdalbum on 2012-03-09
> **Blue Gene said:**
> I burned the 11.10 iso onto my cd. The cd works perfect I have used it on two different computers.
But on my other desktop computer it has
Windows Server 2000
X86 Family Model 8 Stepping
10
At/At Compatible
523824,Kb Ram
When the 11.10 iso cd boots it does the loading... for about 2-5 minutes then it goes black and a screen comes up with Format Not Supported.
Any ideas on how to surmise this issue?

It sounds like your monitor is trying to tell you that Ubuntu is feeding it a screen resolution that the monitor can't handle. Quite a rare problem actually. What graphics card is in this computer? Is the monitor hooked up via VGA (D-Sub), DVI or HDMI?

I haven't had to use it for years, but I believe there are special booting options you can use on the Ubuntu CD. At the first purple screen with a picture of a keyboard and a man at the bottom, press the space bar and you'll get a boot menu. From this menu you can press the F-keys (F1, F2 etc) to look at special boot options; I think there's one about VGA, which is a resolution that all monitors should handle.

If you use this special boot option Ubuntu should boot in low graphics mode on your computer and the monitor will display an image.

---

