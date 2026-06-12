---
title: "Web Browsers and 8.10"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by crimlaw on 2008-11-04
I am currently running 8.04 and Firefox crashes all the time.  I don't like Opera.  Anyone have any suggestions on a third browser that is great?  

If I am already running 8.04, what is the easiest way to update?  Does Firefox work better on 8.10?  

Thanks!!!

---

### Post by Zill on 2008-11-04
> **crimlaw said:**
> I am currently running 8.04 and Firefox crashes all the time...
That shouldn't happen.  It sounds to me like you could have hardware problems - maybe bad RAM.  Try running memtest from the Live CD and see if it finds any errors.

If the hardware is good then maybe you have installed an incompatible extension with Firefox.  Try uninstalling all extensions and see if it becomes stable.

---

### Post by Sarmacid on 2008-11-04
If it's crashing because of the flash plugin, then I had the same problem, had to remove the plugin from the repositories and get the .deb from adobe's site.

---

### Post by oldsoundguy on 2008-11-04
> **sarmacid said:**
> if it's crashing because of the flash plugin, then i had the same problem, had to remove the plugin from the repositories and get the .deb from adobe's site.

+1

---

### Post by jenkinbr on 2008-11-04
Adobe? Deb? *Runs to check*

Wow.

---

### Post by Majorix on 2008-11-04
Intrepid has Flash Player 10 already, which shouldn't crash. Are you perhaps still running the older Flash 9?

---

### Post by ww711 on 2008-11-04
> **crimlaw said:**
> I am currently running 8.04 and Firefox crashes all the time.  I don't like Opera.  Anyone have any suggestions on a third browser that is great?  


Epiphany? Kazehakase? Have a look in your package manager. With KDE there's konquerer too.

> 
If I am already running 8.04, what is the easiest way to update?


using apt and Internet.

> 
  Does Firefox work better on 8.10?  



Not much difference.

---

### Post by philinux on 2008-11-04
> **jenkinbr said:**
> Adobe? Deb? *Runs to check*

Wow.

It's even in the repo's partner.

---

### Post by gandaran on 2008-11-04
> **crimlaw said:**
> I am currently running 8.04 and Firefox crashes all the time.  I don't like Opera.  Anyone have any suggestions on a third browser that is great?  

If I am already running 8.04, what is the easiest way to update?  Does Firefox work better on 8.10?  

Thanks!!!
is your firefox updated to 3.0.3 and using flash 10? this combination should work fine. 
do you have libflashsupport installed, if so get rid of it!

---

### Post by crimlaw on 2008-11-04
Thanks for all of the suggestions.  Unfortunately, as a beginner, I do not know how to check, delete, or install anything by the way you all suggested.  However, I will learn.  

Thanks again.

---

### Post by Sarmacid on 2008-11-04
> **crimlaw said:**
> Thanks for all of the suggestions.  Unfortunately, as a beginner, I do not know how to check, delete, or install anything by the way you all suggested.  However, I will learn.  

Thanks again.

On the menu on the top go to system -> administration -> synaptic package manager. Search for flashplugin-nonfree, right click and mark for removal. Hit apply. There, uninstalled it, or with a console```
sudo apt-get remove flashplugin-nonfree
```

Then go to adobe's site and look for the flash player installer, there should be an option for ubuntu or debian, download it, it's a .deb. To install it just double click and hit install. Really easy. Post if you have more questions.

---

### Post by crimlaw on 2008-11-04
thanks so much for holding my hand through that.  I have the updated firefox and now the updated flash player.  

Are you able to walk me through updating ubuntu to 8.01.  I used windows install to install 8.04.  If I upgrade, will it delete my saved settings or the files I currently have saved under 8.04?  Or, does it just upgrade?

---

### Post by Sarmacid on 2008-11-05
> **crimlaw said:**
> thanks so much for holding my hand through that.  I have the updated firefox and now the updated flash player.  

Are you able to walk me through updating ubuntu to 8.01.  I used windows install to install 8.04.  If I upgrade, will it delete my saved settings or the files I currently have saved under 8.04?  Or, does it just upgrade?
It just upgrades, nothing will be lost.

---

