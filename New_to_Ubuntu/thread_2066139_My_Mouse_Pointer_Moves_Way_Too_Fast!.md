---
title: "My Mouse Pointer Moves Way Too Fast!"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by tackyjan on 2012-10-03
Hi All!

I am new to Ubuntu and first of all let me start of by saying I love it! Much better than Windows 7 and I like it as much as I do OS X (it seems Ubuntu borrowed a lot of ideas from OS X).

Anyway... here is the issue.. my mouse pointer moves WAY too fast.

I went into System Settings and then to Mouse And Touchpad to see if I could change the settings. The Acceleration and the Sensitivity properties are both set to the lowest they can be.

Why is it that even with Acceleration and Sensitivity set to their lowest possible values my mouse still moves at 500 miles per hour?

I am running Ubuntu 12.04 LTS and my mouse is a Logitech G700 gaming mouse. (Note that I have not installed any Logitech and/or third party mouse drivers. I am using whatever Ubuntu has built in.)

Thank you!

Jan

---

### Post by 2F4U on 2012-10-04
As far as I understand, this mouse allows you to set dpi settings through hardware, i.e. on the mouse itself. Did you already try to reduce the dpi settings through the mouse?

---

### Post by NikTh on 2012-10-04
Hi , 

try to install this package 

```
sudo apt-get install gsynaptics
``` 

Then call the program from terminal 
```
gpointing-device-settings
``` 
and try to set your values from there. 

Thanks

---

### Post by MoebusNet on 2012-10-04
EDIT: Nevermind, this program is for touchpads only. Useful, though.

Another program  that gives finer-grained control of mouse & trackpad settings is called *synaptiks* available in Ubuntu Software Center. This is a GUI rather than command-line type program, so you may find it easier to use. I use it to reduce the sensitivity of my trackpad, which Settings>Mouse & Touchpad is unable to do.

---

