---
title: "Activating screenlets"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by amc6987 on 2008-09-17
Hey guys,

I'm new to this open source stuff, and have hooked up my desktop using most of the ideas i got from here: [http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/](http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/)

EVerything went pretty smoothly, until I got to step 5, widgets. When I go to system>preferences, the option of "screenlets" is not there. Any ideas as to why this tab is missing?

Thanks

---

### Post by tuxxy on 2008-09-17
applications > accessories > screenlets

---

### Post by amc6987 on 2008-09-17
hmm... Its not under there either!

---

### Post by tuxxy on 2008-09-17
Weird, do you have them installed, type this in a terminal and it should start the app

```
screenlets
```

if no luck search for screenlets in synaptic, or type in terminal

```
sudo apt-get install screenlets*
```

---

### Post by amc6987 on 2008-09-17
That did the trick. Thanks a bunch!

---

### Post by tuxxy on 2008-09-17
No problem, glad it worked, you can mark your thread solved now too :)

---

### Post by amc6987 on 2008-09-17
Tuxxy, hope you're still there.

It seems that a lot of the things I customized disappeared. I had a dock at the bottom, and extra visual effects, but when I restarted my computer, my dock was gone (I now have a bar indicating open windows, which is located right below the top panel) and I can no longer choose the extra visual effects. When I attempt to, it says "desktop effects could not be enabled".

Somethings really wrong I think, any idea what?

---

### Post by tuxxy on 2008-09-17
Try starting your dock application again, it amy not have been set to auto start.

Are you sure you video card driver is enabled at system > admin > hardware drivers as this will prevent effects working and also your dock if its awn

---

### Post by amc6987 on 2008-09-17
The site Im using said to install all fglrx and nvidia-glx drivers. Well in the synaptics package manager, I installed fglrx-control-envy, fglrx-kernel-source-envy, and fglrx-amdcccle. I installed all three figuring I would need them all. When I try to install nvidia-glx, it says that it has to remove fglrx-amdccle, fglrx-control-envy, and xorg-driver-fglrx-envy. What do I do here?

Also, when I check my hardware drivers, it is blank...

---

### Post by tuxxy on 2008-09-17
Open synaptics package manager and search for nvidia or glrx and remove any drivers you have installed, now run envy and it should select the correct one.

---

### Post by amc6987 on 2008-09-17
Hi tuxxy,

I removed all the drivers, but when I run EnvyNG and try to apply auto install for either ATI or NVIDIA, I get an error messge saying the ATI or NVIDIA card is not found (depending on which I try to auto install).

Just to clarify, all I have installed when I search fglrx is the following:
jockey-common
jockey-gtk
linux-restricted-modules-2.6.24-16-generic
linux-restricted-modules-2.6.24-19-generic
xserver-xorg-video-ati

When i search nvidia-glx, nothing that comes up is installed.



Im not sure if I installed the 5 fglrx drivers that are currently installed on my computer, or if they were already installed when I got ubuntu.

---

