---
title: "Intel HD 3000 control panel?"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by 1c3d0g on 2012-07-14
Hi,

Is there anything like Intel's graphics control panel for Linux?

On Windows I can get a nice utility like this:

[img]http://www.wfu.edu/~yipcw/lenovo/2011/T420s/review/images/t420s-intel_graphics-info.png[/img]

I know about DRIconf, but I can't access basic settings like AA/AF, let alone color correction etc.

The reason I ask this is because I need to change some color settings (RGB values) on my notebook's display, but I can't seem to find any setting to change this. I've searched almost a hundred different threads on more than a dozen forums, but I can't find what I'm looking for. Any help is greatly appreciated. :)

Specs: HP G7-1260US. Core i3, 8 GB RAM.

---

### Post by Mark Phelps on 2012-07-14
Nothing like that, I'm afraid.  You're going to be limited to what you can see in the Display selection.

---

### Post by 1c3d0g on 2012-07-14
So do you know how I can change AA/AF settings, and more importantly, adjust the RGB values on a notebook display?

With an external monitor, this is easy as the monitor has hardware buttons that respond to the built-in menu, but obviously this isnt possible on a notebook display.

On Windows this is easily done on control panel of the graphics card itself. There's got to be a way to adjust the display through some setting on Linux!

---

### Post by 1c3d0g on 2012-07-15
Anybody? :confused:

---

### Post by NikTh on 2012-07-15
Hi ,
As @Mark Phelps told, there is nothing like "intel control panel" at Ubuntu. 

See this program [**[COLOR=Red]here[/COLOR]**](http://jonls.dk/redshift/) , i actually not tested , but you can test it and post results.. 
Thanks

---

### Post by idoitprone on 2012-07-16
> **1c3d0g said:**
> Hi,

Is there anything like Intel's graphics control panel for Linux?

On Windows I can get a nice utility like this:

[IMG]http://www.wfu.edu/%7Eyipcw/lenovo/2011/T420s/review/images/t420s-intel_graphics-info.png[/IMG]

I know about DRIconf, but I can't access basic settings like AA/AF, let alone color correction etc.

The reason I ask this is because I need to change some color settings (RGB values) on my notebook's display, but I can't seem to find any setting to change this. I've searched almost a hundred different threads on more than a dozen forums, but I can't find what I'm looking for. Any help is greatly appreciated. :)

Specs: HP G7-1260US. Core i3, 8 GB RAM.


you can change the rgb values of the xserver

```
man xgamma
```

i not sure on how to make it permanent

---

### Post by 1c3d0g on 2012-07-16
Thanks. Is there any way to set Anti-aliasing and/or anisotropic parameters for Intel's integrated GPU's, though? They are not exposed in DRIconf. :confused:

---

