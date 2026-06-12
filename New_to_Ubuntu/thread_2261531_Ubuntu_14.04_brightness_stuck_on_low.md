---
title: "Ubuntu 14.04 brightness stuck on low"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by tobysullivann on 2015-01-19
[FONT=tahoma][SIZE=3][FONT=trebuchet ms][COLOR=#333333]My brightness controls weren't working before but I didn't really care, but somehow I lowered my screen brightness while downloading league through playonlinux. Now the brightness controls aren't working on the fn keys or in settings, and its stuck on very low.
[/COLOR]
[COLOR=#333333]I tried this [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/), and everything here[https://sites.google.com/site/easylinuxtipsproject/display](https://sites.google.com/site/easylinuxtipsproject/display), and have tried editing the grub file but they didn't do anything.
[/COLOR]
[COLOR=#333333]I am on a Lenovo Z500 using intel graphics. (I have a nvidia geforce gt 635m but don't use it)
[/COLOR]
[/FONT][COLOR=#333333][FONT=trebuchet ms]I have noticed in /sys/class/backlight/ there are the folders ideapad, intel_backlight, thinkpad_screen, each with the files actual_brightness, brightness, and max_brightness. Only in intel_backlight is actual_brightness set to the maximum value. Although it says I don't have the permissions to change them, with sudo.[/FONT][FONT=trebuchet ms][/FONT][/COLOR][/SIZE][/FONT]

---

