---
title: "Cant wathch You Tube Videos?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Blackdragon1400 on 2008-10-16
Does anyone know why I cant watch you tube videos? I go to you tube and where the video is it is just a gray screen. Do i need to get a plugin?

---

### Post by DeathAxe on 2008-10-16
Yes, you need Flash Plugin [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

---

### Post by crzytoxicant on 2008-10-16
yea. You need to download Adobe flash Player. 
here's the link: 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

It should download as a .deb file, then all you have to do is dowble click and install it.

---

### Post by Blackdragon1400 on 2008-10-16
i double click to install it and it says "error wrong architecture 'i386'"

---

### Post by SvistoSK on 2008-10-16
> **Blackdragon1400 said:**
> i double click to install it and it says "error wrong architecture 'i386'"

heh, it was the link for Flash which has to run under windows :-D
try this here,it's from the same site, but for linux based operating system. [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by Blackdragon1400 on 2008-10-16
well, adobe auto detects your OS, so it gave me the .deb file the first time, i got it again and I still get the same error.

---

### Post by DeathAxe on 2008-10-16
Try to install the repo version
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by SvistoSK on 2008-10-16
Do you have an Intel processor or AMD?
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash) try this, but as far as i remember, i've never had any problem with .deb downloaded from adobe.

---

### Post by Fixman on 2008-10-16
> **Blackdragon1400 said:**
> Does anyone know why I cant watch you tube videos? I go to you tube and where the video is it is just a gray screen. Do i need to get a plugin?

You probably installed GNASH player. Go to synaptic and uninstall it, then install flashplugin-nonfree.

---

### Post by SvistoSK on 2008-10-16
Yes, Gnash's been absolutely terrible something.Immediately removed and replaced by Adobe's flash.

---

### Post by panhandle on 2008-10-16
If this is a new installation, use the following guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by fooman on 2008-10-16
> **Blackdragon1400 said:**
> i double click to install it and it says "error wrong architecture 'i386'"

are you using 64 bit ubuntu?  ...the latest flash from that link is x86 only.  don't believe there is an x64 version yet.

i do not use x64...but i did find this:

[http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/](http://queleimporta.com/the-easiest-way-to-install-flash-10-on-ubuntu-64-bits/en/)

hope that helps. :)

---

### Post by Blackdragon1400 on 2008-10-16
Ok, go figure i reboot when I get home and it works find now. Thanks anyway, I already had it installed but i dont know what was going on with it (three overused letters)

---

### Post by steveneddy on 2008-10-16
> **DeathAxe said:**
> Try to install the repo version
```
sudo apt-get install flashplugin-nonfree
```

This is what I recommend.

It's fast, easy and it will update automatically.

---

### Post by yoly on 2008-10-16
Ok I'm new to ubuntu and cant also watch you tube or my space. I like to listen to music at my space. I've been trying to follow these messages but not sure what to download. Too many different download advice are given.

HELP:confused:

---

### Post by darkerlink on 2008-10-17
yoly, type in sudo apt-get install flashplugin-nonfree into your terminal if you've just installed ubuntu.

---

### Post by billgoldberg on 2008-10-17
You really shouldn't be advising to install flashplugin non-free.

Flash 10 is out and performs much better than Flash 9 (the one in the repos).

Just google for Adobe flash 10, go to the download page and select the ubuntu .deb installer.

Double click it once downloaded to install.

Restart firefox and you're good.

---

