---
title: "How to exit X Server?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Racecar56 on 2008-08-11
HELP!! I searched all over and I can't find a working solution to exit it.
I'm trying to install NVIDIA drivers for my 1-year old HP Pavillion dv9000 with kubuntu on it. It has a nvidia GeForce Go 7600 (ooga ooga) and why I need these drivers are because Blockland v9 won't start. Yet this isn't a virtual machine. :lolflag:

---

### Post by tuxxy on 2008-08-11
Do you mean reboot? you could try from terminal

```
 sudo shutdown -r now
```

---

### Post by Racecar56 on 2008-08-11
> **tuxxy said:**
> Do you mean reboot? you could try from terminal

```
 sudo shutdown -r now
```

It still gives me the same ol' error.

[QUOTE=console]ERROR: You appear to be running an X server. Please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com)[/QUOTE]

---

### Post by soxs on 2008-08-11
```
sudo /etc/init.d/gdm stop
```
Note: You will be restricted to an environment ala <STRG><ALT><F1>

EDIT:
for kubuntu you should use this one:
```
sudo /etc/init.d/kdm stop
```

---

### Post by Racecar56 on 2008-08-11
> **soxs said:**
> ```
sudo /etc/init.d/gdm stop
```
Note: You will be restricted to an environment ala <STRG><ALT><F1>

EDIT:
for kubuntu you should use this one:
```
sudo /etc/init.d/kdm stop
```

That got me somewhere, thanks alot, but now I have some kind of gcc compiler version check error. :(

---

### Post by soxs on 2008-08-11
post plx, and try to install the gcc stuff:
```
sudo apt-get install build-essential linux-headers-$(uname -r) gcc-4.2 gcc-4.1
```

Use the thank button if you feel like^^

btw to restart your desktop environment, you may use the command:
```
/etc/init.d/kdm start
```

---

### Post by Racecar56 on 2008-08-11
> **soxs said:**
> post plx, and try to install the multilib stuff:
```
sudo apt-get install build-essential linux-headers-$(uname -r) gcc-4.2-multilib gcc-4.1-multilib gcc-4.1 gcc-4.2
```

Use the thank button if you feel like^^

btw to restart your desktop environment, you m
ay use the command:
```
/etc/init.d/kdm start
```

It still doesn't work.

:(

---

### Post by soxs on 2008-08-11
you may try ```
sudo apt-get build-dep nvidia-glx-new
``` though I am quite clueless what your problem is.

Can you somehow attach/describe the error output?

---

### Post by Racecar56 on 2008-08-11
> **soxs said:**
> you may try ```
sudo apt-get build-dep nvidia-glx-new
``` though I am quite clueless what your problem is.

Can you somehow attach/describe the error output?

How would I? I'm using the same computer as the one that has the problem. However, I might try my other computer...

---

### Post by soxs on 2008-08-11
```
sudo apt-get install libc6 libc6-dev gcc make binutils module-init-tools
```

according to [http://de.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/chapter-02.html](http://de.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/chapter-02.html) you need them

---

### Post by bodhi.zazen on 2008-08-11
Easiest way to install the nvidia driver is with envy.

Envy can be run form X or the command line :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mustafaSK on 2009-07-10
thankyou very much soxs.....great knoledge

---

### Post by sirkrustin on 2009-11-17
> **Racecar56 said:**
> It still doesn't work.

:(

By far the easiest way to install hardware drivers in kubuntu is to download them from the repository (use KPackageKit or Synaptic). 

Then go to the menu under "system" and select "hardware driuvers" It will scan your system for available drivers which you can then install b y clicking on them. You'll have to restart.

eg, on my system i want accelerated nVidia drivers so I open synaptic and enter "nvidia" in the search field. looking for "nvidia-glx", i see the latest is "nvidia-glx-185 - 185.18.36-0ubuntu9 (amd64)". Selecting that one, synaptic informs me of all the other packages i must download to satisfy dependencies. click on "apply" 

Once downloading is complete, you can then go to hardware drivers to select the driv er you want. (eg, "NVIDIA accelerated graphics driver (version 185)". You'll likely see at least one other driver available (the one that came installed with the distro)

;)

---

