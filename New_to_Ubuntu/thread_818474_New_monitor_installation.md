---
title: "New monitor installation?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Fakename McGrew on 2008-06-04
I have upgraded to a new TFT monitor after over 5 years of loyal service from my CRT. However, according to xorg.conf, I am still using my old monitor. As such, I am stuck in 1024x768 and am unable to change to a higher resolution using the Screen Resolution program in the System/Preferences menu. My new monitor is an Acer AL1716, which has a native resolution of 1280x1024.

In Ubuntu 7.10, there was an option to manually select the make and model of one's monitor. I know this because just a few hours ago I tried using the new monitor in 7.10, only to be told that it was a "Plug & Play" model. I searched for the Acer AL1716 model, but the list only went as high as AL1715 before moving on to the next designation. I assumed that upgrading to the latest version of Ubuntu (which I had been holding off) would provide the latest monitor drivers, but when the installation finished, I found to my horror that there was no such program that allowed me to select which monitor I have at all. How do I get hold of such a program, and/or how can I get Ubuntu to realise that I am using an Acer AL1716 and not a NEC CI FC700?

---

### Post by wolfen69 on 2008-06-04
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Fakename McGrew on 2008-06-04
Ran the command and restarted. Success! Glorious 1280x1024. Thanks!

---

