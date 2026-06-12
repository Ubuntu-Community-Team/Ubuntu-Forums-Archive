---
title: "Problems with Compiz on Hardy"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by rakzor on 2008-06-09
okay. A bit of a background.
I'm running Xubuntu Hardy and I've tried just about everything and I can't get Compiz working exactly right.

I have an nVidia FX 5500 256MB graphics card.

When I run Compiz I get this:


```
rakzor@raccoon:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting
```


or I get this when I install the nVidia drivers though the hardware drivers thing.


```
rakzor@raccoon:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
** (xfwm4:5474): WARNING **: Another Window Manager is already running

```


However, when I do that I can't use keyboard shortcuts at all for some reason but compiz does run.

I tried installing the nVidia driver though envyng, but when I restarted it just told me I was running in low graphics mode. 

And a question, is it possible to use xfwm4 instead of Emerald?


Any help would be appreciated, as I've tried everything I can think of.

---

### Post by stchman on 2008-06-09
> **rakzor said:**
> okay. A bit of a background.
I'm running Xubuntu Hardy and I've tried just about everything and I can't get Compiz working exactly right.

I have an nVidia FX 5500 256MB graphics card.

When I run Compiz I get this:


rakzor@raccoon:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: true 
no true found, exiting


or I get this when I install the nVidia drivers though the hardware drivers thing.


rakzor@raccoon:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
** (xfwm4:5474): WARNING **: Another Window Manager is already running



However, when I do that I can't use keyboard shortcuts at all for some reason but compiz does run.

I tried installing the nVidia driver though envyng, but when I restarted it just told me I was running in low graphics mode. 

And a question, is it possible to use xfwm4 instead of Emerald?


Any help would be appreciated, as I've tried everything I can think of.

Here is a question:

Did you install the restricted drivers?  If you did not Compiz will not work.

I don't know where the restricted drivers are on Xubuntu but you can install them via Synaptic.

```
sudo apt-get install nvidia-glx-new
```

Make sure nvidia-settings is installed.

---

### Post by rakzor on 2008-06-09
> **stchman said:**
> Here is a question:

Did you install the restricted drivers?  If you did not Compiz will not work.

I don't know where the restricted drivers are on Xubuntu but you can install them via Synaptic.

```
sudo apt-get install nvidia-glx-new
```


I have it installed. Compiz still says Xgl isn't present. :/

---

### Post by stchman on 2008-06-09
> **rakzor said:**
> I have it installed. Compiz still says Xgl isn't present. :/

Try installing Ubuntu Hardy unless your system specs are real low.  Xubuntu is meant for older hardware needing lightweight GUI.

If you run anything over 1.5GHz and 512MB RAM you are good to run Gnome.

---

### Post by rakzor on 2008-06-09
> **stchman said:**
> Try installing Ubuntu Hardy unless your system specs are real low.  Xubuntu is meant for older hardware needing lightweight GUI.

If you run anything over 1.5GHz and 512MB RAM you are good to run Gnome.

Urg. I don't have low specs but I'm pretty fond of Xubuntu. I've gotten compiz to work a bit by playing around with it all.

There's only two problems now. No keyboard shortcuts when I install drivers through System -> Hardware Drivers and tick the box.
And second, I'd much rather use xfwm4 instead of Emerald, if it's possible.

---

### Post by rakzor on 2008-06-09
I've been reading threads and I see a few people have gotten xfwm4 working with Compiz but others say it's impossible? 
I guess I can live with it either way. Right now any help with getting the shortcuts working is much appreciated.

---

