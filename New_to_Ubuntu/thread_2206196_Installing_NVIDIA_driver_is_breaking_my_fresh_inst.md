---
title: "Installing NVIDIA driver is breaking my fresh install."
date: 2014-02-17
forum: New to Ubuntu
---

### Post by jared11 on 2014-02-17
**PC SPECS:** GTX 780, ASRock Z87Extreme 6, 4770k i7

I successfully install Ubuntu via USB from the live desktop, though I can only reach the desktop by setting the launcher to "nomodeset". If I do not, I get to the desktop wallpaper, hear bongos, and then nothing else appears.

After install, I launch Ubuntu from the bootloader and it runs fine. The only noticeable issue is that everything is very large, as if the screen is 800x600 or so. Then, I install the video drivers and am told to reboot.

After rebooting, I can no longer reach the desktop. This error appears:

[I]*error* cannot initialize the agpgart module. drm fill_in_dev failed

[/I]And I am sent to a fullscreen black and white console, where I can issue commands. I do not know enough about linux/ubuntu to know what to do here and I just perform a fresh install and try again. 

I have tried the official drivers from nvidia, I have installed via terminal "current-nvidia" and "nvidia-331". They all end up with the same results.

Any ideas? Thank you so much!

---

### Post by mastablasta on 2014-02-18
is this a laptop maybe with ***nvidia optimus***?

---

