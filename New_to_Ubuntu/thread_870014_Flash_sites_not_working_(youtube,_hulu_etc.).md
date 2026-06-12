---
title: "Flash sites not working (youtube, hulu etc.)"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Levyhouse on 2008-07-25
Flash test works here: [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) 

System Hardy 64bit using Firefox 3.0.1 and Gnash 8.0 r99


Have tried reinstall.  Any suggestions would be appreciated.

---

### Post by gimlithedwarf on 2008-07-25
try installing the flashplugin-nonfree package, I've found this works best with firefox

---

### Post by LowSky on 2008-07-25
or use mozilla-plugin-gnash

sudo apt-get install mozilla-plugin-gnash

---

### Post by Levyhouse on 2008-07-25
Should I only have one installed?  I have tried both and both are installed now...  If a purge one should I reboot afterwards?  Which one is preferred and why?

Thanks

---

### Post by Flyingjester on 2008-07-25
I would only install one, i'm not sure if it creates conflicts, but i think it might. I would use the non-free if you want flash. It has given me a lot less problems than gnash.

---

### Post by nvteighen on 2008-07-25
> **Levyhouse said:**
> Should I only have one installed?  I have tried both and both are installed now...  If a purge one should I reboot afterwards?  Which one is preferred and why?

Thanks
"Preferred" depends on what you want:

Adobe Flash: If you want have full functionality, and don't mind it being proprietary software.
GNU Gnash: If you only can stand Free Software even at the cost of lossing functionality.

I'm sure you can have both installed, but surely it will need some configuring in order to avoid any conflict. Deleting one won't hurt, anyway... It's just the Flash plugin, not an essential block... and you can always reinstall the other.

---

