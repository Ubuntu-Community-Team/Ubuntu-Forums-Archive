---
title: "Multi monitors"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by dgrspencer on 2008-09-28
Thanks in anticipation of the usual quick response!  (these forums are the best)

I'm in the process of making the transition to Ubuntu from windows.  Have it up and running on one desktop and laptop (although I am still very much a novice).  However, my main computer is running 3 monitors and I've just gone into Ubuntu (only Live version as yet) and only one works.

My computer setup is an Intel Quad core processor with 4 gig of RAM and 2 graphics cards - NVidea 128meg PCIe connected via an SLI bridge.

Getting this all working in windows was tricky but now it is working it is very stable and fast.  Can anyone help getting multimonitors working?  If I need 3rd party software I'll prob need help installing it too if it isn't simply a double click on an install file!

Many many thanks,

Dave

---

### Post by fooman on 2008-09-28
if i'm reading this right,  your trying to get multi-monitors working from the "live cd"?

don't think thats possible as you will need to first install the nvidia drivers.  can't do that on a live cd/dvd.

if ubuntu is installed,  then you need to install the nvidia drivers and nvidia-settings (which may auto-install with the drivers depending on how you installed them).

after both are installed, you use nvidia-settings (as root) to change the settings for multi monitors:

```
gksudo nvidia-settings
```

---

### Post by dgrspencer on 2008-09-28
if ubuntu is installed,  then you need to install the nvidia drivers and nvidia-settings (which may auto-install with the drivers depending on how you installed them).

after both are installed, you use nvidia-settings (as root) to change the settings for multi monitors:

```
gksudo nvidia-settings
```[/QUOTE]



Thanks a lot Fooman - will get it installed properly ASAP and then have a go!

---

