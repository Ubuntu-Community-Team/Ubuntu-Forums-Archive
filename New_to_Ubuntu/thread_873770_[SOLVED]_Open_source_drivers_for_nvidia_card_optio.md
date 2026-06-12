---
title: "[SOLVED] Open source drivers for nvidia card options"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by onesojourner on 2008-07-29
I am having some [video card issues]("http://ubuntuforums.org/showthread.php?t=873073") and I am trying to explore other options.

I seem to remember reconfiguring my xorg on an older version of ubuntu on an older computer and I had a whole list of different drivers to choose from for my video card. Can some one tell me what command I need to use to get those options? I thought I was just reconfiguring xorg (sudo dpkg -reconfigure xorg.conf ) but that is mostly just asking about my keyboard layout and does not really do anything with my video/video card settings.

---

### Post by philinux on 2008-07-29
From synaptic install nvidia-settings or

sudo apt-get install nvidia-settings

it turns up in System>Admin

xorg.conf don't contain any graphics stuff anymore.

Also in recovery mode is a menu and a choice called xfix.

Try that too.

---

### Post by Nepherte on 2008-07-29
The open source nvidia driver is referred to as 'nv'. If you want to reconfigure your xorg.conf file, type in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by onesojourner on 2008-07-29
> **philinux said:**
> From synaptic install nvidia-settings or

sudo apt-get install nvidia-settings

it turns up in System>Admin

xorg.conf don't contain any graphics stuff anymore.

Also in recovery mode is a menu and a choice called xfix.

Try that too.


I installed the nvidia-settings but there does not appear to be any options for configuring s-video out. 

Can you give me a few more details on xfix?

---

### Post by philinux on 2008-07-29
This might help, I think xfix mainly sorts out resolution problems.

[http://ubuntuforums.org/showthread.php?p=4929070](http://ubuntuforums.org/showthread.php?p=4929070)

---

### Post by onesojourner on 2008-07-29
Solved:
[http://ubuntuforums.org/showthread.php?p=5484100#post5484100](http://ubuntuforums.org/showthread.php?p=5484100#post5484100)

---

### Post by Haioko on 2008-07-29
Can this be done with ATI cards as well? I have an Asus EAH3450.

---

### Post by ModdTaco on 2008-07-29
My ATI X600 seemed to be native to that. My new 8800GT however is not. Give it a try anyways. xserver is pretty damb sweet. Going a bit off topic Compiz Config is pretty cool to.

---

### Post by onesojourner on 2008-07-29
try the second post:

[http://ubuntuforums.org/showthread.php?p=5484100#post5484100](http://ubuntuforums.org/showthread.php?p=5484100#post5484100)

---

### Post by Haioko on 2008-07-29
I'm only having problems when I try to play WoW using wine. When I load the game the colours go all weird and don't change back until I restart the computer. I was hoping that a driver might fix this.

---

