---
title: "Another resulution problem"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by BackBack on 2008-06-08
Everything looks a bit squished together under 1280x800 resolution, is there a way to make it look as it should? My graphics card is an NVIDIA GeForce Go 7150M, so it should be able to handle it, and I'm on Ubuntu Hardy.

---

### Post by BackBack on 2008-06-08
Bump

---

### Post by chewearn on 2008-06-08
Back-up your /etc/X11/xorg.conf, then run nvidia-settings:
```
gksudo nvidia-settings
```Remember to save the new settings to xorg.conf after you have made the changes.  And reboot after that.

---

### Post by alienexplorers on 2008-06-08
Try running:
> sudo nvidia-xconfig

---

### Post by BackBack on 2008-06-08
gksudo nvidia-settings didn't seem to do anything at all, and the sudo nvidia-xconfig  command said > Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf' But it didn't really help :/

---

### Post by chewearn on 2008-06-08
> **BackBack said:**
> gksudo nvidia-settings didn't seem to do anything at all


Sorry, I forgot you need to specifically install nvidia-settings in hardy.
```
sudo apt-get install nvidia-settings
```

.

---

### Post by SunnyRabbiera on 2008-06-08
also try gksu displayconfig-gtk in a terminal, I had to play around with it to get my video working.

---

### Post by BackBack on 2008-06-08
Everything looks scretched out, as if Ubuntu just wasn't made for widescreen.  Nothing that I mess with tends to help :/

---

### Post by SunnyRabbiera on 2008-06-08
Well I have noted a fluke like that myself, but using gksu displayconfig-gtk did help when I played around with stuff in the screens section.
I have a older HPmx50 monitor, its max res is 1024x768 but until I changed the monitor settings I was stuck at 800x600.
but once I played with the model setting in the screens tab I was able to fix it.

---

### Post by BackBack on 2008-06-09
Problem is, I've already tinkered with it, and it still looks odd :/

---

### Post by chewearn on 2008-06-09
> **BackBack said:**
> Problem is, I've already tinkered with it, and it still looks odd :/

Have you use nvidia-settings?

---

