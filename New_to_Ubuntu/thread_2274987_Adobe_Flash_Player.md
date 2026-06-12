---
title: "Adobe Flash Player ?"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by Greg Mueller on 2015-04-23
Tired of dealing with Adobe.

Are we any closer to getting a substitute for Adobe Flash Player? I have heard it is being worked on since adobe abandoned us.

I keep having to click on the "Continue to Allow" thing on the address bar (when it turns red). Is there an add-on or setting that will do that automatically?

Using Firefox 37.0.1 and Ubuntu with KDE Plasma

Thanks
Greg

---

### Post by dino99 on 2015-04-23
Set the browser preferences to use html5 when possible, and/or install the required firefox plugin
Install flashpugin-installer or pepperflashplugin-nonfree for chromium-browser

---

### Post by SeijiSensei on 2015-04-23
In Tools > Add-Ons > Plugins you can select when you want a plugin to be activated.  Choose "Always Activate" for Flash if that's what you want.  Usually I prefer "Ask to Activate" then grant permanent exemptions to sites I choose to allow when prompted by the pop-up dialog.  Some sites launch Flash videos automatically; I don't like that.

---

### Post by Greg Mueller on 2015-04-23
All I have is "Ask to Activate" or "Never Activate" in the Shockwave Flash 11.2.202.425 box



> **SeijiSensei said:**
> In Tools > Add-Ons > Plugins you can select when you want a plugin to be activated.  Choose "Always Activate" for Flash if that's what you want.  Usually I prefer "Ask to Activate" then grant permanent exemptions to sites I choose to allow when prompted by the pop-up dialog.  Some sites launch Flash videos automatically; I don't like that.

---

### Post by SeijiSensei on 2015-04-23
That's weird.  I've never seen that before.  

First, let's try an easy fix if it's available.  Go to Edit > Preferences > Applications and scroll down to the Shockwave Flash entries.  See if the drop-down box is set to "Always Ask".  Mine is set to "Use Shockwave Flash (in Firefox)". 

If that doesn't help, then for testing purposes, try starting with a new Firefox profile. Close Firefox, then run:
```

cd ~
mv .mozilla .mozilla.old

```
Now start Firefox.  Same story?

---

### Post by Greg Mueller on 2015-04-23
Mine are set to "Use Shockwave Flash (in Firefox)". 




> **SeijiSensei said:**
> That's weird.  I've never seen that before.  

First, let's try an easy fix if it's available.  Go to Edit > Preferences > Applications and scroll down to the Shockwave Flash entries.  See if the drop-down box is set to "Always Ask".  Mine is set to "Use Shockwave Flash (in Firefox)". 

If that doesn't help, then for testing purposes, try starting with a new Firefox profile. Close Firefox, then run:
```

cd ~
mv .mozilla .mozilla.old

```
Now start Firefox.  Same story?

---

### Post by Greg Mueller on 2015-04-23
**How would I undo that command if nothing changes?**



[I]If that doesn't help, then for testing purposes, try starting with a new Firefox profile. Close Firefox, then run:
Code:

cd ~
mv .mozilla .mozilla.old

Now start Firefox. Same story? [/I]

---

### Post by SeijiSensei on 2015-04-23
```

cd ~
rm -rf .mozilla
mv .mozilla.old .mozilla

```

---

### Post by Yellow Pasque on 2015-04-24
> 11.2.202.425
Your Flash version is out of date. If you upgrade to 11.2.202.457, then the problem may go away. (Nowadays, I think Firefox goes into the "semi-paranoid" mode you describe if it detects an old Flash version.)

---

### Post by Frogs Hair on 2015-04-24
The add-on below works on a number of sites , but not everywhere as suggested by the name. 
 
[https://addons.mozilla.org/en-us/firefox/addon/html5-video-everywhere/](https://addons.mozilla.org/en-us/firefox/addon/html5-video-everywhere/)

---

