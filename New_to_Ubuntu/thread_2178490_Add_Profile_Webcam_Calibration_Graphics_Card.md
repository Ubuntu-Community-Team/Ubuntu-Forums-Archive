---
title: "Add Profile? Webcam Calibration? Graphics Card?"
date: 2013-10-03
forum: New to Ubuntu
---

### Post by rami5 on 2013-10-03
System settings -> Color -> Toshiba Satelllite L300 -> Add Profile

^ What is this, and what does it do?

...
Also, in the same pane i can calibrate the Webcam ( built in )
I can choose a "Target Type" from a combo box - What the heck is this?
When i try to download the file in the next windw it just fails to "download the package" - Why?

...
System Settings -> Details -> Graphics
It says "Driver unknown"

Does this mean my graphics card is unidntified/ inactive?

---

### Post by DuckHook on 2013-10-03
I don't use webcams so can't advise you on second question. However:> **rami5 said:**
> System settings -> Color -> Toshiba Satelllite L300 -> Add Profile

^ What is this, and what does it do?This is for setting color profiles on your computer so that every colour output and input device produces exactly the same colour. It is critical for desktop publishers, video editors and other exacting graphics work that require precise control over colour matching. For ordinary mortals, defining a colour profile is usually more trouble than it's worth and I never bother.> System Settings -> Details -> Graphics
It says "Driver unknown"

Does this mean my graphics card is unidntified/ inactive?This is just an info box. Your system cannot find your graphics card on its limited internal database of graphics cards, so returns an "unidentified" result. Your graphics card is obviously active, else you could not read the results on your monitor. Nothing to worry about on this one.

---

### Post by rami5 on 2013-10-04
Hmmm, so if my system dont recognize my graphics card, im guessing i wont be able t utelize its features either...?
Like when i use other Window computers, i can right click and acced an Nvidia ( for example ) controll panell to use/ view the graphics card features.

I dont know how this works in Linux/ Ubuntu, but how can i get the system to recognize my graphics card?
Do i need to install some sort of drivers, would that work?

---

### Post by DuckHook on 2013-10-04
It recognizes the chipset, which is the important thing. It is just not recognizing the exact model of your card, which is not that big a deal. I am not familiar with your laptop.

1. What are its system specs?
2. What video chip does it use?
3. Did you install proprietary video drivers for it or is it still running with the default drivers?

If you installed proprietary drivers and video system is either AMD or nVidia video, then the proprietary driver will come with settings software (control panels) that you can use to fine-tune your features. Such control is also possible using command line, but not recommended for beginners.

To figure out what drivers you need (if any), please answer above questions and post back results of:```
lspci -vk | grep -iA10 vga
```

---

### Post by andrea.bonomini on 2013-12-08
Hi there,
after the installation of ubuntu 13.10 all the graphics seems to work fine, but the webcam image is very very dark and the people on skype can't see me very well.
Is this an issue with the webcam calibration?

Thx to all

---

