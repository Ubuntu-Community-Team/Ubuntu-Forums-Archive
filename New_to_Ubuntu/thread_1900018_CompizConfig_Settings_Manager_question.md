---
title: "CompizConfig Settings Manager question"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by siriusbg on 2011-12-25
Hi! I have some problems with the CompizConfig Settings Manager. I had to reinstall ubuntu for some reason and I just installed the nvidia proprietary drivers and used the Nvidia Xserv Settings (or something like that) to configure the resolution and refresh rate. As I previously installed ubuntu, I downloaded the CCSM and tweaked the refresh rate, since the desired number wasn't present under the Nvidia settings manager - it had 70,75,85 and 87 Hz and I wanted 80. I really don't remember how I got the CCSM options work around the Nvidia settings and how I had a 80 Hz refresh rate instead of the default 85. Could someone please give me a hint?

---

### Post by BC59 on 2011-12-25
I think it's here:
[http://ubuntuforums.org/showthread.php?t=1390284](http://ubuntuforums.org/showthread.php?t=1390284)

---

### Post by siriusbg on 2011-12-25
Alas, it didn't work. Maybe I'm not being too precise. I want to replace the CCSM options - to be used instead of the Nvidia X server settings when it comes to refresh rate. And I'm pretty sure that it is possible, only I don't know how. 
Previously I tried using xrandr and editing the monitors.xml file - in vain. I'm still stuck at 1024x768 @ 85 Hz...

---

### Post by siriusbg on 2011-12-27
I really may be annoying, but I could really use some help, please..

---

### Post by AgentZ86 on 2011-12-27
First let me ask how do you know your monitor refresh rate is 80 ?

Check your monitors specs to determine the refresh rate even if your card support higher the monitor will only do what it can do

And if you set them up incorrectly it could cause a problem

So Nvidia applications settings are not detecting proper available settings that your use to using already or is this a new setup that your attempting to force to work ?

One thing to be sure the Nvidia shows your monitor in the Nvidia settings Display Configuration

Let me know what is says

---

### Post by grahammechanical on 2011-12-27
Check this link to see why a driver settings manager will not offer greater resolutions and refresh rates than that decided by the monitor manufacturer.

[http://en.wikipedia.org/wiki/Extended_display_identification_data]("http://en.wikipedia.org/wiki/Extended_display_identification_data")

You can also try searching for EDID override and see what you get.

Regards.

---

### Post by siriusbg on 2011-12-28
[This is a screenshot of the Nvidia settings -> Display Configuration](http://imageshack.us/photo/my-images/94/screenshotat20111228094.png/)

[These are the CompizConfig settings](http://imageshack.us/photo/my-images/192/screenshotat20111228095.png/)

AgentZ86, I know that my refresh rate IS NOT 80 Hz. My outdated monitor has a Menu button where one can read Status - 1024x768,  H:69.0 KHz, V:85.5 Hz.

grahammechanical, I've read the wiki article, but I simply got the idea, without any further technical aspects. One thing's sure - somewhere in the Nvidia settings panel there is a mentioning about EDID and a button "acquire EDID", but I didn't dare pushing it :)

---

