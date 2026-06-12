---
title: "Problem with fonts"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by CrewDK on 2013-02-08
I installed ubuntu on an old computer. At first sign everything was installed properly. However, the system have strange problems with fonts.

Every time I reboot PC some letters, different every time, is crossed out (stricked?). I tried to reinstall a few times, even tried different distributive version (12.04, 12.04.1, 12.10), but each time the problem is the same.

It may be any language, any letter and even in terminal window there is such problem! For example on my screenshot there is problem with russian letter "&#1080;" in words "&#1055;&#1086;&#1080;&#1089;&#1082;" (find), "&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;" (Download) etc.

In what could be the problem?

PS: BTW when i'm booting ubuntu from Live CD\USB this problem also exist. But only on this PC. Could it be some sort of problem with hardware?

---

### Post by grahammechanical on 2013-02-08
It could be an issue with the video card not being able to render the screen image correctly. How much memory does the video card have?

It could an issue with the video driver. If you are on 12.04 then open Additional Drivers utilty and activate another driver.

If you are on 12.10 go to System Settings>Software Sources>Additonal Drivers tab and activate another driver from there.

Regards.

---

### Post by badhat on 2013-02-08
From that screenshot, maybe it is your language/locale settings, not fonts. Either way, I'd try changing settings: language, locale and system fonts. (I'm not using the Unity desktop, so I can't give you details further than that.)

---

### Post by CrewDK on 2013-02-10
> **grahammechanical said:**
> It could be an issue with the video card not being able to render the screen image correctly. How much memory does the video card have?

It could an issue with the video driver. If you are on 12.04 then open Additional Drivers utilty and activate another driver.

If you are on 12.10 go to System Settings>Software Sources>Additonal Drivers tab and activate another driver from there.

Regards.

Thanx for reply. As I said earlier this is a rather old motherboard with integrated video. 
ASUS P5GC-MX/1333

Yesterday, I decided to look for solutions to my problem specifically with the name of the board and found a couple of clues. So tomorrow I will try them. If there is something clear, I'll write it here. 

As a fallback - I found in my old stocks AGP video card, so I will try to install it. Let's hope it still works :)

> **badhat said:**
> From that screenshot, maybe it is your language/locale settings, not fonts. Either way, I'd try changing settings: language, locale and system fonts. (I'm not using the Unity desktop, so I can't give you details further than that.)

I do not think it's a problem with the settings of the system. This is most likely a problem with the installation hardware or drivers for it. This problem appears even during boot from LiveCD\LiveUSB with ubuntu.

---

### Post by CrewDK on 2013-02-14
So, in the end, I couldn't find a solution to this problem. So now I had to leave WinXP on the machine. :(

---

