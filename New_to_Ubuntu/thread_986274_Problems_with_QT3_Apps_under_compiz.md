---
title: "Problems with QT3 Apps under compiz"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-11-18
TexasRanger wrote 15 hours ago: (permalink)

My symptom:
With Ubuntu Visual Effects set to "Normal" or "Extra", OpenOffice menu text disappeared.

After several days of experimentation, I can report the following:
- I am running Ubuntu 8.04 LTS with Ubuntu release of OpenOffice 2.4.1 and Nvidia driver 96.43.09-0ubuntu1 graphics card driver.

- When I enabled Compiz Normal or Extra Visual Effects, the menu text in all OpenOffice apps disappeared, replaced thin horizontal lines. Problem does NOT occur with Visual Effects set to "None". No other apps displayed the symptom, only Oo.

- After experimenting, I found that Oo fonts could be restored by disabling "antialiasing" checkbox in the Oo Tools/Options/View submenu. Of course, this made the menu text fonts look very pixel-y.

- Problem solved (for me) by running "sudo dpkg-reconfigure fontconfig-config" and selecting "Autohinter", "Always" (for subpixel rendering on my LCD display), and "No" for Enable bitmapped fonts. Then, I changed Ubuntu System/Preferences/Appearance/Fonts to "Subpixel" smoothing. Viola! Problem solved.

---

