---
title: "Live cd boot parameters"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Bölvaður on 2008-11-27
Hi I got this 64 bit live cd and want to install on one computer:

I have Nvidia 8800 GTS 320mb and intel's E6700 processor (duo core)// name: pc1
And also Nividia 8800 GT 512mb, with intel's Q6600 processor (quad core)// name: pc2

My final goal is to have it installed on **pc1** but all I get is black screen after the initial boot. So when I take quiet booting off I can see all the normal text, where no instance fails. But after that the screen goes into different mode, kind of very quick flicker and then it is only blank.

That happens only on pc1 but not on pc2. :(

My thoughts have been that 64 bit version some how fail with the motherboard and perhaps video is trying to use the motherboard's integrated graphical card rather than the nvidia one.

Or that VESA isn't being activated.

These are the boot parameters I found suggested on forums there and here and have tried and failed:

```
vga=791
vga=771
vesa
xforcevesa
video=vesa
xdriver=vesa
```

I rather not use gui if it can be avoided as terminal commands are universal and hence should be learned for the sake of knowledge.

---

### Post by theozzlives on 2008-11-27
Try the 64 bit server, it don't have the GUI

---

### Post by Bölvaður on 2008-11-27
> **theozzlives said:**
> Try the 64 bit server, it don't have the GUI

True true, or just try the alternate cd.

But I thought there might be a boot parameter that could enforce VESA as the default driver throught the install. That could be easier than buying more blank cds and then download and burn the alternative cd or server version on it :)

---

