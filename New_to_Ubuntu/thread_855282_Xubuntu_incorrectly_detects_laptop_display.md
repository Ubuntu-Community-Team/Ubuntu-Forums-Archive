---
title: "Xubuntu incorrectly detects laptop display"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-07-10
Hello Everybody,

I'm trying to install Xubuntu 8.04 on a Toshiba 4600 laptop and it only allows an 800x600 display when it should be 1024x768. Is there any way I can get the installer to configure it correctly?

Thanks,

Charlie

---

### Post by OffAxis on 2008-07-10
The installer doesn't include the restricted driver, so usually you'll do an install, then install the restricted driver, then tweak the settings where necessary.

If the resolution you want isn't an option after you install the restricted driver then run
```
sudo dpkg-reconfigure xserver-xorg
```

that'll walk you through the keyboard, mouse, video driver, and ultimately the display configuration, where you can add the resolution you want.

---

### Post by ajgreeny on 2008-07-10
I don't think the 
```
sudo dpkg-reconfigure xserver-xorg
```
works since ubuntu used the new xorg.  I think you may need to go to Screens and Graphics in the Other menu, if you have it.  If it's not there use ```
gksudo displayconfig-gtk
```to run it and see if you can change things there.

---

### Post by Charlie Chick on 2008-07-11
Thank you all for your help. I'll give it a go!

Charlie

---

### Post by Charlie Chick on 2008-07-14
I've now tried both the above suggestions. The first configured the keyboard only and the second brought up a dialogue box for configuring the display but the maximum resolution was still 800x600. I need to get the display to show 1024 x 768.

What's strange here is that if I install version 6.10 it correctly detects the screen resolution, but 8.04 doesn't. I wonder why?

Charlie

---

