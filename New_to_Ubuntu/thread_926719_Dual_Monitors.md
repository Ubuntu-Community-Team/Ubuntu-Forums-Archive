---
title: "Dual Monitors"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by mr wilson on 2008-09-22
I have a laptop and another display connected to my laptop. Previously, with windows, I was able to have different images etc running in each screen. Now, having put Ubuntu on the laptop, I can get either screen to work individual, or both screens to display the same image (which defeats the purpose of having two screens!). Even if I un-tick the 'clone screens' box in the 'screen resolution' window nothing changes.

 This is pretty important – it essentially makes my display superfluous!!! 

Cheers.

---

### Post by aeiah on 2008-09-22
what graphics card are you using, and have you installed the restricted drivers? if its nvidia, have you made sure you have the nvidia-settings package?

you should be able to span the monitors and such. clone isnt the only option.

---

### Post by Nettoyer on 2008-09-22
What kind of video card are you using?

Under your display settings, does it show two monitors?

```
lspci -v
```

In Ubuntu 8.04 Hardy I had an option for "Big Desktop" once I setup my video card (Ati Sapphire X1950). Which let me run both monitors.  This was in the Ati control panel for me though.

---

### Post by mr wilson on 2008-09-22
At risk of sounding like an idiot, I don't actually know what graphics card it is - it's a second hand compter. Is there an easy way to check? I am an ubuntu novice. 

P.s. That IMDB script is cool

---

### Post by aeiah on 2008-09-22
the lspci -v will probably display it. im not sure if it is displayed for onboard graphics or not. either way, if still in doubt you can go into your bios at boot and probably see from there, especially if its onboard

---

### Post by mr wilson on 2008-09-22
In the BIOS it says the Video Controller is a Intel 855GM/855GME. I assume that is the Graphics Card is. There is nothing else that looks like a graphics card.

---

### Post by jemate18 on 2008-09-22
may be this will help

> [http://ubuntuforums.org/showthread.php?t=807091](http://ubuntuforums.org/showthread.php?t=807091)

---

### Post by maires on 2008-09-23
I just installed Ubuntu 8.04 I beleive. I am having a problem with dual monitors. I installed the nVidia drivers through application manager. I saw instructions that told me to run nvidia-settings which it tried to do. It prompted me for a password but afterwords nothing came up... just a blank prompt. 

Is there an nvidia-settings app i need to grab ? I downloaded the drivers directly from nvidia's website thinking I might need to install them directly. 

First it told me I cannot have X running when I do the install... so I restart go to terminal mode. 

Then it tells me it can't run because it needs at least run level 3 to work properly... ok.. telinit 3 

X starts back up... /sigh 

I have seen a lot of config work on the forums here. Edit this conf etc... I was really hoping there was a visual tool for getting my Nvidia 7800 GTX working with dual monitors in ubuntu in the simplest way possible. 

Why doesnt the nvidia settings option work ? Any help please! I fear this isnt even the most complicated thing I will be attempting in my effort to ditch windows.

---

### Post by maires on 2008-09-24
Figured it out... envyNG for the WIN!

---

### Post by mr wilson on 2008-09-29
> **jemate18 said:**
> may be this will help

Had a good look at it, but couldn't make any sense of it.

Any other suggestions??

---

