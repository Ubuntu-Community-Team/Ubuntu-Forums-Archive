---
title: "Fujitsu H270"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by opabert on 2014-03-05
Hello,

Iam total beginner with Ubuntu.
Fujitsi H270 High_End Laptop 3 years old
New blank HDD
Install from DvD

All versions Below 9.0  are possible to install / startup.

All versions Up from 9.0 to 12.04.4,
wil not install / startup at all.

Where do i go wrong ?

---

### Post by phidia on 2014-03-05
In the failed attempts to install what feedback/error messages or other troubleshooting worthy symptoms do you get?

---

### Post by Vladlenin5000 on 2014-03-05
According to this [http://globalsp.ts.fujitsu.com/dmsp/Publications/public/ds-CELSIUS-H270.pdf](http://globalsp.ts.fujitsu.com/dmsp/Publications/public/ds-CELSIUS-H270.pdf) it has a NVIDIA® Quadro FX 770M - it might need the "nomodeset" option...

---

### Post by opabert on 2014-03-05
Versions 8.04.4  runs OKE

Versions above 8.04.4  
The screen keep stuck  
UBUNTU with 4x Red dots.
Must, unplug DC power to get the laptop running again

No messages.

---

### Post by ajgreeny on 2014-03-05
When you boot to the DVD hit any key, then choose language, then F6 to show you various boot options.

Select nomodeset then Esc to the previous screen and allow it to boot, hopefully to a GUI.

---

### Post by Mark Phelps on 2014-03-05
If the red dots keep changing, it's not "stuck", instead, it's very slow.

When you're in there editing boot parameters to add "momodeset", remove the one that says "quiet".  That is suppressing progress messages, which prevents you from seeing what is going on behind the scenes.

---

### Post by opabert on 2014-03-06
Iam a complete beginner with Ubuntu.
So please a step by step info will be great.

In first the RED DOTS changing left to right.

After a while it stop for ever the 3 dots in RED.... i keep it there for 15 minutes waiting.
Also try Ubuntu 14.4 give same problem.

Only Ubuntu 8.04.4 the install runs fast and its working.
What is different between 8.04.4 and later versions.

I try/see if i get the nomodeset

---

### Post by nunecas123 on 2014-03-06
Your motherboard might be causing your problem. Try the nomodeset option when you boot from the DVD and tell us what you've got.

---

