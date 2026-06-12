---
title: "Noob Unbuntu Resolution Issues"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by kubena on 2008-06-30
Installed Ubuntu Hardy Heron 8.04 last night.

Default screen resolution after the load was 600 x 480, or whatever the default is.

I went into "Preferences" and set my screen resolution to 1280 x 1024.

The screen resolutions did change. Everything is huge. I can drag my mouse to any side of my monitor and the screen scrolls all the way over to it's limits in whatever direction I would like to go.

So, what do I have to do to make my screen "fit" onto the monitor?

Also, I know that my monitor and graphics card are capable of higher resolutions because I was able to get higher resolutions in XP. Higher resolutions just were not offered to me as an option under Unbuntu.

I am an XP baby and any answer your give me will need to be in preschooler age terms. It seems to me from looking around the forums that I need to go into Ubuntu's config.sys equivalent and make some changes. Just not sure how to go about it.


Thanks in advance for your help.

---

### Post by avtolle on 2008-06-30
Try this from the terminal (Applications>>Accessories>>Terminal)```
gksudo displayconfig-gtk
```enter your password when prompted, and you should then try to find your monitor in the list provided (first, find the vendor in the left-hand panel, if there, click on the name, and in the right hand panel find your precise model, if there, again click on it) and hopefully this will do the trick. You could also take a look under the graphics card tab to find your card, similar drill, and hopefully, after applying, this will give you better results.

---

