---
title: "Resolution differences"
date: 2015-06-11
forum: New to Ubuntu
---

### Post by cowboy.bebop on 2015-06-11
Why does the resolution from a Live ISO provide several options to choose from, but after you install, it only provides one default of 800*600? I can never seem to get other resolutions to appear.

---

### Post by coffeecat on 2015-06-11
You mean why does the installation on **your** particular hardware setup only offer one resolution. I can see 11 choices of different resolutions on my setup with Ubuntu 15.04.

If you provide details of your hardware, especially the graphics card you are using, whether or not you have installed a proprietary video driver, and which version of Ubuntu you are using, I am sure someone will be able to help troubleshoot this for you.

---

### Post by papibe on 2015-06-11
Hi Ubuntwha.

Could you open a terminal run these commands and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

xrandr -q

xrandr -q --q1

lsb_release -a
```
Regards.

---

### Post by cowboy.bebop on 2015-06-11
Its a k53e laptop: [https://www.asus.com/Notebooks_Ultrabooks/K53E/specifications/](https://www.asus.com/Notebooks_Ultrabooks/K53E/specifications/)

---

