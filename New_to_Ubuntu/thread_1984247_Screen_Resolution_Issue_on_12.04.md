---
title: "Screen Resolution Issue on 12.04"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Otto Nascarella on 2012-05-21
Hi there

I have a laptop with hi-res monitor, whose default resolution is 1920x1080.

If my screen was massive, I'd just keep it like that, but it's a 15.6" screen, so things look too tiny. Changing just the font size won't help, specially for browsing the web.

I change my screen resolution to 1600x900 (which I had to add via Xrand) and it's fine...but theres just one caveat: If I need to kill the Xorg server, or just jump to another tty, screen goes black. A couple of 'updates' ago, if I not only that would happen, but also computer crashed. Now at least I can go back to tty7.


Anyone out there has had the same kinda situation and has a suggestion for me?


Thanks in advance,


Otto

---

### Post by sandyd on 2012-05-21
> **Otto Nascarella said:**
> Hi there

I have a laptop with hi-res monitor, whose default resolution is 1920x1080.

If my screen was massive, I'd just keep it like that, but it's a 15.6" screen, so things look too tiny. Changing just the font size won't help, specially for browsing the web.

I change my screen resolution to 1600x900 (which I had to add via Xrand) and it's fine...but theres just one caveat: If I need to kill the Xorg server, or just jump to another tty, screen goes black. A couple of 'updates' ago, if I not only that would happen, but also computer crashed. Now at least I can go back to tty7.


Anyone out there has had the same kinda situation and has a suggestion for me?


Thanks in advance,


Otto
What video card are you using?

If you don't know, click on the Unity Dash, and type in 'terminal'.
Open, and type in 
```
lspci | grep VGA
```

It will return something similar to
```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV635 [Mobility Radeon HD 3650]
```

Post the output by clicking the '#' symbol, and placing the output between the [code] tags.

---

### Post by Otto Nascarella on 2012-05-22
that's my output for: lspci | grep VGA


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)

---

