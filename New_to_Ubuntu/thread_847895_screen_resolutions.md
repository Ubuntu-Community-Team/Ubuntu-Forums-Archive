---
title: "screen resolutions"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gunner ra on 2008-07-03
Hi Everyone I am not only new to your forum, but a novice in all things computer related; so I hope you will forgive me if my post's are inane. I have installed ubuntu 8.04 within windows, while I try to lean it. However I am stuck at the first hurdle, my screen resolutions only offer's 640x480 or 320x240 ?. Any ideas why this is so please. Thanks Gunner RA

---

### Post by iaculallad on 2008-07-03
What video card are you using?

To get the value, drop to your terminal and execute the command below:

```
lspci | grep VGA
```

---

### Post by kattman on 2008-07-03
Try coing to System > Preferences > Screen resolution , and see if you can change the Refresh rate higher!

---

### Post by JacoLouw on 2008-07-03
Try installing Envy and let it install your graphics drivers for you. It only support Nvidia/ATI based cards though.

---

### Post by gunner ra on 2008-07-03
Hi iaculallad I tried the command you posted. My graffics card is an Nivida gfx 550? Yours Gunner RA

---

### Post by iaculallad on 2008-07-03
Try installing the appropriate driver for this video card.

System->Administration->Restricted Drivers

---

### Post by mailtwogopal on 2008-07-03
Hi,

 May i know were u landing at desktop properly after booting. if so, try system - preferences - screen resolution and set the desired resolution and a popup window ask you whether to keep changed settings or to keep original settings. Click "keep new settings" and close. U may get it. hope am not wrong if u landed to desktop properly. keep posted.

---

### Post by SunnyRabbiera on 2008-07-03
Also try in a terminal gksu displayconfig-gtk

---

### Post by gunner ra on 2008-07-04
Hi Guys Thank you all for your help. I have tried all the suggestions; how-ever non worked? The command lspci | grep VGA found the correct graphics card. I tried to download Envy EN which I belive is the correct on for the Hardy Heron, but it would not worh: although Envey would allow me to download? Thanks again the Gunner

---

### Post by gunner ra on 2008-07-09
Hi Guys Sorry it has taken me so long to get back: I have spent days on line looking for a answer to my screen resolution problem. The good news is I have resolved it. Now I can start leaning about this great application? Thank you all for you're input, much appreciated Gunner Ra:)

---

### Post by jjocsak on 2008-07-09
> **gunner ra said:**
> Hi Guys Sorry it has taken me so long to get back: I have spent days on line looking for a answer to my screen resolution problem. The good news is I have resolved it. Now I can start leaning about this great application? Thank you all for you're input, much appreciated Gunner Ra:)

What was the resolution?

Jeff

---

