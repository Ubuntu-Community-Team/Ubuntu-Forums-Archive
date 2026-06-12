---
title: "Failed to detect GPU and the terminal keeps kicking me out"
date: 2016-01-15
forum: New to Ubuntu
---

### Post by ToraYasha on 2016-01-15
A bit of a background of what is happening. Today was the day that I was doing to switch to the dual booting life of Windows and Ubuntu. Spending an hour trying to make heads and tail of the advanced installer. Eventually everything looked good left my PC to install Ubuntu 15.10 to go walk the dogs. My major concern was getting GRUB set up correctly, but the installer got me covered so no worries there. And thus the* fun* problems started to happen.

So as I booted up my newly installed OS I get the "Low graphic's mode" because it couldn't detect the drivers. So I rebooted into windows and grabbed the graphics card driver. (Nvidia geforce 640 if you were wondering) and then booted into linux to install it. Only to learn that ubuntu doesn't exactly work like windows. Apparently you have enter stuff into the terminal. I grabbed the commands that people said that would fix the problem. Then I came across something interesting, a login in prompt. I typed in my username and password that I set up. For a split second there was information and then it kicked me out and then prompted me to log in again. I thought I might of misspelt my password. But that wasn't the case as I was able to change it in the troubleshooting menus.

So went poking around again to see if I could anything else I could do.  There were some other errors but most notably:
"Failed to detect the available GPUs and deal with system changes"

I am completely stumped. Is it possible that I have to do a re-install?

---

### Post by cariboo on 2016-01-15
I'd suggest you do install the graphics driver the Ubuntu way :). Go to the gear icon in the top right corner and select Systems Settings next select Software & Updates go to Additional Drivers, let it search for the preferred driver for your graphics card then click Apply Changes, once it's done reboot, and you should be up and running with the proprietary driver.

---

### Post by Shane_Mundee on 2016-01-15
To add to what Cariboo said, i had to reinstall the graphics driver, but there was a video on YouTube that really helped, so i'd recommend searching YouTube because i do remember there's a semi good walk through video.

---

### Post by ToraYasha on 2016-01-16
Thank you to all that replied.

However, I forgot to explain that the "Low graphics mode" Error is actually preventing me from seeing the login screen. I tried to go into recovery mode to load the save-mode graphics but it does nothing other than display some errors and something about GPU not being detected. Only option there is a reboot.

 Pressing ctrl+alt+f1 leads me to a dos like terminal that I have to log into in. That terminal when I enter in all my login details logs me in. Shows me some info for a split second, way too fast for me to be able to read anything. It clears the screen and tells me to log in again.

---

