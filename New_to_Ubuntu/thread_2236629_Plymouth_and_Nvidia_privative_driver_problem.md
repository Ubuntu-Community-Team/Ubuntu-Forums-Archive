---
title: "Plymouth and Nvidia privative driver problem"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by arieleoar on 2014-07-28
Hi everyone!

Months ago the pc started to show a creepy "Ubuntu" boot splash text (somefont like system font) instead the splash image

Before some research i made i've managed to realize that plymouth has a rare bug with nvidia privative driver that causes the missing for a graphical interface to show the splash image, then i found the fix in 
[http://ubuntuforums.org/showthread.php?t=2223463](http://ubuntuforums.org/showthread.php?t=2223463) 
(in the last answer) [QUOTE=Drowz0r][http://youtu.be/1jIegOR6A0M](http://youtu.be/1jIegOR6A0M)[/QUOTE]
but for some reason i was unable to fix because other problem
libhal1, libhd and hw... are deprecated for "trusty-tahr" version of ubuntu so there are unable to download and install

***Then there is another way to fix it? ***i've tried plymouth-manager (no result) and the options "quiet splash" were in the grub config.

---

### Post by arieleoar on 2014-07-29
Hi again.

Before decide to break the pc :p i managed to fix the problem, so i post the solution here for someone else.

First I Downloaded *Grub-Customizer*:

```
sudo apt-add-repository ppa:danielrichter2007/grub-customizer
sudo apt update
sudo apt install grub-customizer
```

then open it and in the *"appearance customization"* tab activate the checkbox "*Customize Resolution" *and set it to 1024x768 or another resolution that you see convenient
later open the "*advanced options" *(lower right button) and add a new entry with name = "**GRUB_GFXPAYLOAD_LINUX**" and value = "**auto**" then set active and close the dialog. Now hit the button "*save*" and exit the app.
In the next boot plymouth will work. If you want to personalize it download plymouth-manager.

Thanks for reading! regards!

---

