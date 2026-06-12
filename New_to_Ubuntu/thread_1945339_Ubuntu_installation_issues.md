---
title: "Ubuntu installation issues"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by hahnbrad25 on 2012-03-23
Ok, so I have a older hp dv6000 with AMD Sempron that I upgraded the processor to a AMD Athlon 64 and also installed 2gb of ram. If any of that matters. Anyway, it's ran fine with windows 7 for a long time, but I decided to try and wipe windows off and install Ubuntu 11.10.  I have burning the image to a DVD first and then a USB via the USB loader on the website. I restarted and chose to just not run Ubuntu along with windows but instead just replace windows entirely. So it prompts me that the installation is complete so I restarted it and it was extremely slow as far as loading goes and it prompts me to log in and I do. It accepts it and kind of freezes for a minute then it just turns to a solid colorful screen then wherever I click it turns black. It doesn't show any programs or anything so a real glitchy blank screen. I have tryed multiple different times with 32 bit and 64 bit and the same thing happens. I have dual booted with windows before no problem, but I can't figure this one out. Any ideas would be greatly appreciated. Thanks

---

### Post by Perfect Storm on 2012-03-23
It may be a video/driver issue.
Which card do you have?

---

### Post by mastablasta on 2012-03-23
does it work in live boot mode? 
 
What kind of graphics card do you have? did you install the proprietary drivers?
 
have you tried booting using some of the  boot options? [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by wildmanne39 on 2012-03-23
Hi, I have one like your but mine does run nvidia card for sure.

I have not tried to put unity on it I run 10.04 xubuntu, it would b my guess that you need a boot parameter.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by hahnbrad25 on 2012-03-23
It will boot with the USB drive in, but not without it. Even though it does boot up it still doesn't act right. It has an nvidia graphics chiP. with the drive in everything looks normal but when you try and open anything the screen will go black and glitchy. Then it just acts as if it is freezing up. Really weird. I just don't see it being a video card issue because when I was running windows it was fine.

---

### Post by Quackers on 2012-03-23
If you try the nomodeset boot option you will find out if it's a video problem or not
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by hahnbrad25 on 2012-03-23
Ok, I finally got it. When I went to log in I hit the settings tab and changed graphics from Ubuntu to Ubuntu 2d and that then allowed me to get full usage and then install the nvidia drivers and now it runs great.

---

### Post by Quackers on 2012-03-23
Excellent :-) Enjoy!

---

