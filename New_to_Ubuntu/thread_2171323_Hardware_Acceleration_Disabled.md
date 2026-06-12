---
title: "Hardware Acceleration Disabled"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by hass2 on 2013-08-30
Hello everyone, 

Just installed Linux Mint 15 Cinnamon on a friend's Laptop (Acer Aspire 5736Z). 
Did the installation from Windows 7 and Live USB. I wanted to keep a dual boot, in case the friend in question doesn't like Mint. 
After the installation of Mint, I ran through a few problems:
1. Mint boots normally, but the screen is extremely dark. I plugged in my projector and was able to use Mint on it. 
2. I googled the problem, it seems common but I couldn't find an exact solution to my case. First I tried editing the "backlight" in the Grub configuration file, nothing happened, in fact when I did this, the brightness FN+Arrow stopped appearing on the screen. Then I tried nomodeset in Grub.
3. After nomodeset, unplugged the projector, the laptop's screen is now working, but with a new problem: hardware acceleration is off, resolution was low and all graphics are jerky. 
I found out that nomodeset turns off all hardware acceleration and bypassed the intel drivers.
This is where I'm at now. 

Apparently, running Mint from the live cd/USB does the same thing, ie black screen.
I tried updating all drivers from Mint, nothing changed. 

Laptop specs: 
Acer Aspire 5736Z 
Graphic: Intel GMA 4500M
4GB DDR3 Memory 
320 GB HDD 

I'm a beginner when it comes to Linux. I'm familiar with some commands and some basic tweaks but nothing more. 
So please if you have a solution, put the detailed steps. 

Thank you all, 
Hass.

---

### Post by hass2 on 2013-08-30
Still have no solution. 
Bump.

---

