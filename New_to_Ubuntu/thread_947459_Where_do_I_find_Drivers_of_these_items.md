---
title: "Where do I find Drivers of these items?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by mogui_666 on 2008-10-14
Hi guy,

where can i find driver for

- [Microsoft wireless Keyboard/ mouse 700 v2.0]("http://www.windowsmarketplace.com/details.aspx?itemid=6005895")
- [D-Link DWA-140]("http://www.dlink.com/products/?sec=0&pid=652")
- [M- Audio Audiophile 2496]("http://www.m-audio.com/products/en_us/Audiophile2496.html")
- [M-Audio Axiom 49]("http://www.m-audio.com/products/en_us/Axiom49.html")

I have been try to search for these driver for some time but can't find any. Please help. Thanks in Advance=)

---

### Post by mogui_666 on 2008-10-14
Sorry one more item:

- Samsung Omnia

how do i sync Omnia to my computer? 

Thanks again...

---

### Post by Thelasko on 2008-10-14
The driver for your Audiophile 2496 should be included in[ ALSA]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio") (installed by default)

Are you using UbuntuStudio?  You may also want to ask the people in the [Multimedia section]("http://ubuntuforums.org/forumdisplay.php?f=335") of the forums.

---

### Post by intel17 on 2008-10-14
Does the Keyboard and Mouse not work?  I don't see any reasons why it dose not work.  It does not require any extra drivers from what I can see on the web site.

HTH 
Pete

---

### Post by mogui_666 on 2008-10-15
hi guy sorry for the late reply. ok the keyboard and mouse are working now. but i cant find ndisgtk in synaptic package manager. i an now using another computer for internet...

---

### Post by SunnyRabbiera on 2008-10-15
> **mogui_666 said:**
> hi guy sorry for the late reply. ok the keyboard and mouse are working now. but i cant find ndisgtk in synaptic package manager. i an now using another computer for internet...

for ndisgtk try this page:
[http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk)

---

### Post by Thelasko on 2008-10-15
> **mogui_666 said:**
> hi guy sorry for the late reply. ok the keyboard and mouse are working now. but i cant find ndisgtk in synaptic package manager. i an now using another computer for internet...

[It's there.]("http://packages.ubuntu.com/hardy/ndisgtk")

If your machine doesn't have internet, it won't be able to access all of the packages in the repositories.  In this case, I recommend downloading from the link above and moving it over on a flash drive or something.

---

### Post by mogui_666 on 2008-10-15
Hi guy thanks for the help will try it later=)

---

### Post by mogui_666 on 2008-10-16
hi guy,

i have download the .deb file from the above website. but when i double click it, a msg like this came out

"Error: Dependency is not satisfiable: ndiswapper-common"

what should i do??

thanks...

---

### Post by Thelasko on 2008-10-16
> **mogui_666 said:**
> hi guy,

i have download the .deb file from the above website. but when i double click it, a msg like this came out

"Error: Dependency is not satisfiable: ndiswapper-common"

what should i do??

thanks...

Download [this]("http://packages.ubuntu.com/hardy/ndiswrapper-common") and install it.  You may need [this ]("http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9")too.

Hint:  That message just means that ndisgtk depends on ndiswapper-common to work.  A list of programs ndisgtk depends on is on the [ndisgtk page.]("http://packages.ubuntu.com/hardy/ndisgtk") (marked with red circles)  It even provides links to the dependency's page.

Synaptic normally handles all of these dependencies for you, but since your machine doesn't have internet access, it can't.

---

### Post by ByteJuggler on 2008-10-16
> **mogui_666 said:**
> 
- [D-Link DWA-140]("http://www.dlink.com/products/?sec=0&pid=652")


If you want a native driver for this, then [the driver here ]("http://www.ralinktech.com.tw/data/drivers/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2")will work (up to kernel .19, it appears to not work yet for the latest .21 kernel), although installation is a tad fiddly.  If you'd like to try to install this driver, post back and I'll try to post specific instructions.

---

### Post by mogui_666 on 2008-10-16
Hi guy,

thanks you so much for the help...will try all the matter you guy suggest until one works. 

thanks again=)

---

