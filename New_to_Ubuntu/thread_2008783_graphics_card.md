---
title: "graphics card"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by dazdidge on 2012-06-23
Hi guys, I have just moved over to Ubuntu 12.04 after 20 years of windows and am finding it a pretty steep learning curve. I have various versions of Linux running on desktops now with no problems:p

I decided to try it on my laptop with the live cd and ended up installing it completely. The laptop has a decent graphics card but I don't know how to check if it is working correctly or if at all, if all the features are available, and I also can't find where to change any of the settings for it.
The laptop is as follows
HP Compaq NW8240 
Processor: Intel Pentium M 760 (2.0 GHz)
Chipset: Intel 915PM (533 MHz FSB)
Graphics: ATI Mobility FireGL V5000 128 MB GDDR3
Screen: 15.4" WSXGA+ (1680x1050)
Running with 2 Gb RAM

If anyone out there can help me out I would really appreciate it.

thanks in advance

daz

---

### Post by U202E on 2012-06-23
> **dazdidge said:**
> Hi guys, I have just moved over to Ubuntu 12.04 after 20 years of windows and am finding it a pretty steep learning curve. I have various versions of Linux running on desktops now with no problems:p

I decided to try it on my laptop with the live cd and ended up installing it completely. The laptop has a decent graphics card but I don't know how to check if it is working correctly or if at all, if all the features are available, and I also can't find where to change any of the settings for it.
The laptop is as follows
HP Compaq NW8240 
Processor: Intel Pentium M 760 (2.0 GHz)
Chipset: Intel 915PM (533 MHz FSB)
Graphics: ATI Mobility FireGL V5000 128 MB GDDR3
Screen: 15.4" WSXGA+ (1680x1050)
Running with 2 Gb RAM

If anyone out there can help me out I would really appreciate it.

thanks in advance

daz
ATI is my favorite gfx card, I don't think there is anything wrong with that.
what would you like do do with it? do you mean something like speed acceleration?

---

### Post by cortman on 2012-06-23
> **dazdidge said:**
> Hi guys, I have just moved over to Ubuntu 12.04 after 20 years of windows and am finding it a pretty steep learning curve. I have various versions of Linux running on desktops now with no problems:p

I decided to try it on my laptop with the live cd and ended up installing it completely. The laptop has a decent graphics card but I don't know how to check if it is working correctly or if at all, if all the features are available, and I also can't find where to change any of the settings for it.
The laptop is as follows
HP Compaq NW8240 
Processor: Intel Pentium M 760 (2.0 GHz)
Chipset: Intel 915PM (533 MHz FSB)
Graphics: ATI Mobility FireGL V5000 128 MB GDDR3
Screen: 15.4" WSXGA+ (1680x1050)
Running with 2 Gb RAM

If anyone out there can help me out I would really appreciate it.

thanks in advance

daz

If your graphics are good (no artifacts, excessive lag) and you have the correct resolution, it looks like the open-source drivers are working fine for you. Nothing more required. :)

---

### Post by dazdidge on 2012-06-23
In windows I can go into hardware manager and instantly see if the card is installed and working correctly as opposed to the standard windows drivers, in which case it would be using the onboard graphics and using RAM to run it. With having 128mb of memory on the card I would rather be using that but I don't know how to check.

thanks
daz

---

### Post by dazdidge on 2012-06-23
> **cortman said:**
> If your graphics are good (no artifacts, excessive lag) and you have the correct resolution, it looks like the open-source drivers are working fine for you. Nothing more required. :)

In that case it's looking good. I have read somewhere on the web that Ubuntu doesn't get on well with my graphics card and it can be a pita to get working correctly. 

thanks for the reply
daz

---

### Post by QIII on 2012-06-23
Don't follow any suggestion to attempt to install the fglrx (Catalyst) driver.

It's not that Ubuntu doesn't get along with your card.  AMD dropped Linux driver support for that card and there is only the legacy driver.  Unfortunately, that will not work with X server versions after 2008.  Installing the fglrx driver would leave you looking at a blank screen and throwing things.

Please have a look [here]("https://help.ubuntu.com/community/RadeonDriver") for some info on the open source Radeon driver.  If your card is not supported, you will have to use the default VESA driver.

---

### Post by grahammechanical on 2012-06-23
As you have noticed, Linux does things differently to Microsoft Windows.

Try selecting Displays from the power cog menu. Or opening the Dash and selecting the Applications lens (second icon from the left at the bottom of the Dash) and looking for a utility relating to your graphics card. You might have to click See xxx number more installed.

Another thing you can try is to Install Compiz Configuration Settings Manager (CCSM) and use the Ubuntu Unity Plugin to modify Unity. If you can resize the Launcher icons then you have Unity 3D running and your card is being used to the full.

Regards.

---

### Post by jmfal on 2012-06-23
I you want know what drivers are in use ,try this in a terminal
```
lspci -v
```

---

### Post by dazdidge on 2012-06-24
> **grahammechanical said:**
> As you have noticed, Linux does things differently to Microsoft Windows.

Try selecting Displays from the power cog menu. Or opening the Dash and selecting the Applications lens (second icon from the left at the bottom of the Dash) and looking for a utility relating to your graphics card. You might have to click See xxx number more installed.

Another thing you can try is to Install Compiz Configuration Settings Manager (CCSM) and use the Ubuntu Unity Plugin to modify Unity. If you can resize the Launcher icons then you have Unity 3D running and your card is being used to the full.

Regards.

Could not find anything in your first suggestion, but I installed CCSM and was able to resize the Launcher icons. So it would appear the card is being used to its potential and I had nothing to worry about :p

Thanks to everyone who replied =D>

daz

---

