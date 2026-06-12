---
title: "Help Me Please"
date: 2019-04-07
forum: New to Ubuntu
---

### Post by tanapon2519 on 2019-04-07
How to fix hdmi with more screen solutions 1080p to set at 1080p, but if less than 1080p, set to 720 on Ubuntu. Thank You.

---

### Post by wildmanne39 on 2019-04-07
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by RedDirtDog on 2019-04-08
I don't understand your question.  Can you clarify?

---

### Post by poorpockets-mcnewhold on 2019-04-08
I´ve understood from him the following:
How can make Ubuntu set himself automatically to the monitor resolution ?

In that case, I suppose this should help you. [https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en](https://help.ubuntu.com/stable/ubuntu-help/look-resolution.html.en)

> 
[LIST]
[*=left][FONT=inherit]Open the [COLOR=#808080][FONT=inherit][Activities]("https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en#activities")[/FONT][/COLOR] overview and start typing [COLOR=#808080][FONT=inherit]Settings[/FONT][/COLOR].[/FONT]
[*=left][FONT=inherit]Click on [COLOR=#808080][FONT=inherit]Settings[/FONT][/COLOR].[/FONT]
[*=left][FONT=inherit]Click [COLOR=#808080][FONT=inherit]Devices[/FONT][/COLOR] in the sidebar.[/FONT]
[*=left][FONT=inherit]Click [COLOR=#808080][FONT=inherit]Displays[/FONT][/COLOR] in the sidebar to open the panel.[/FONT]
[*=left][FONT=inherit]If you have multiple displays and they are not mirrored, you can have different settings on each display. Select a display in the preview area.[/FONT]
[*=left][FONT=inherit]Select the resolution or scale, and choose the orientation.[/FONT]
[*=left][FONT=inherit]Click [COLOR=#808080][FONT=inherit]Apply[/FONT][/COLOR]. The new settings will be applied for 20 seconds before reverting back. That way, if you cannot see anything with the new settings, your old settings will be automatically restored. If you are happy with the new settings, click [COLOR=#808080][FONT=inherit]Keep Changes[/FONT][/COLOR].[/FONT]
[/LIST]


---

### Post by TheFu on 2019-04-09
If this isn't just working automatically, then there are lots of possible issues.
* Unsupported GPU
* Unsupported Monitor
* Bad/failing HDMI cable
* Some adaptor/converter getting in the way
* Some KVM device getting in the way

A few months ago, I built a new machine.  The Quattro GPU wasn't supported any longer by nvidia legacy drivers with the newer kernels and the F/LOSS video driver wouldn't support the resolutions I wanted.  

In the end, I bought a newer GPU which should be supported 7+ yrs.  That was just the start of my problems. The new GPU didn't have VGA out, so it wouldn't work directly with my KVM switch.  I needed an active converter for DVI-D to VGA - fine - $8 and I got one that claimed to support 1200p resolution.  But it wouldn't work higher than 1080p. DVI-D wants to query the monitor for EDID information which provides all the horizontal and vertical sync timings and supported resolutions, but between the adaptor, KVM, and VGA, nothing was getting through to the GPU.  Using another machine, I manually pulled the EDID data and stored it into a binary file, transferred it over.
Finally, I had to setup an xorg.conf file from scratch to know about the monitor, the GPU, the drivers, the "modelines", and force the driver to ignore the lies being told about EDID from the DVI-D converter and use the settings I'd pulled.  It took me a few days, once I got into it.

So, if this isn't _just working_ already, here's hoping the solution isn't even 10% as hard as mine.

Which, exact, monitor and which exact video card is involved?   **sudo lshw -C video** will help, to begin.

---

