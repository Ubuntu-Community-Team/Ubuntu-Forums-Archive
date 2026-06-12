---
title: "Two monitors (cloned) playing video."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by NaF on 2008-05-20
Hi :)
I have a little mini-pc, with a on-board gfx card and a pci with a vga and a dvi port. (don't use the on-board one tho). I have it plugged into a monitor near my bed ('fall to sleep'-movies) and a monitor on my desktop, with a keyboard and mouse near. By default (not that there's any other options available) the two monitors shows the same content (cloned). This works, except when I watch movies - only one of the monitors shows the video the other is black? I can make the other monitor show the video by unplugging the monitor on my desktop and logging out and in again. But the monitor near my bed is 10meters away from the mouse and keyboard and in a dead angle, so I have to start the video in blind (i'm posting in absolute beginner, so clearly i can't).

Anyone know how to fix this, or just dictate what monitor is to show the video content? compiz isn't enabled.

---

### Post by Inxsible on 2008-05-20
Video always defaults to the primary monitor. You can change which one is your primary monitor and then it will play on the one near you bed.

---

### Post by NaF on 2008-05-20
> **Inxsible said:**
> Video always defaults to the primary monitor. You can change which one is your primary monitor and then it will play on the one near you bed.

How do I change that :)? And why can't it show up on both monitors? I take it, it's a nvidia-thing? On windows it shows up on both monitors?

---

### Post by Inxsible on 2008-05-20
in a terminal, type in```
gksudo nvidia-settings
``` Change the settings there and make sure to save to X configuration.

---

### Post by NaF on 2008-05-20
> **Inxsible said:**
> in a terminal, type in```
gksudo nvidia-settings
``` Change the settings there and make sure to save to X configuration.

I have installed the restricted nvidia drivers - but absolutely nothing happens when I enter that command.

---

### Post by quelx on 2008-05-20
install **nvidia-settings** from synaptic and you should have the gui config Inxsible is talking about

---

### Post by NaF on 2008-05-20
> **quelx said:**
> install **nvidia-settings** from synaptic and you should have the gui config Inxsible is talking about

Ok, I've installed it. When Running 
```
nvidia-settings
```
it tells me:
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server
```
```
sudo: nvidia-xconfig: command not found
```:oops:

---

### Post by NaF on 2008-05-20
If I just try and get to the config page, I only have these options [IMG]http://www.fo.person.dk/Screenshot1.png[/IMG]- I can't figure out how to set the primary monitor on that page :confused:

---

### Post by quelx on 2008-05-20
do you really have an nvidia card?  what does ```
lspci |grep VGA
``` return, if nothing post your lspci (without the grep).

---

### Post by Inxsible on 2008-05-20
and if you do have an nVidia card, are you using the restricted drivers for it?

---

### Post by NaF on 2008-05-20
> **quelx said:**
> do you really have an nvidia card?  what does ```
lspci |grep VGA
``` return, if nothing post your lspci (without the grep).

:oops::oops::oops::oops::oops::oops::oops:
```
VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
```
Thought I had an nvidia card, when I activated compiz just to look at it, it asked me to install the restricted nvidia drivers, so I just assumed it was :oops: What to do on an ATI card then?

---

### Post by quelx on 2008-05-20
try fglrx-control

and make sure you have the proper drivers installed

```
sudo apt-get install fglrx-control xorg-driver-fglrx
```

---

### Post by NaF on 2008-05-20
> **quelx said:**
> try fglrx-control

and make sure you have the proper drivers installed

```
sudo apt-get install fglrx-control xorg-driver-fglrx
```

I have the "ATI binary X.Org driver" - "Optimized hardware acceleration of OpenGL with newer ATI graphic cards" but when I fire up the fglrx-control it says the drivers are not correctly installed. Compiz effects works flawlessly.

---

### Post by quelx on 2008-05-20
what does ```
glxinfo | grep rendering
``` show?

and have you tried

```
sudo dpkg-reconfigure xorg-driver-fglrx
```

or

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

---

### Post by NaF on 2008-05-20
> **quelx said:**
> what does ```
glxinfo | grep rendering
``` show?

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

I don't know how to set LIBGL_Debug to verbose :confused:

---

### Post by quelx on 2008-05-20
Did you do this?

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

---

### Post by NaF on 2008-05-20
> **quelx said:**
> Did you do this?

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

I don't know if this sets it to verbose, but I got more info out of it: 
```
naf@home:~$ export LIBGL_DEBUG=verbose
naf@home:~$ glxinfo | grep rendering
libGL: XF86DRIGetClientDriverName: 5.3.0 r200 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL error: dlopen /usr/lib/dri/r200_dri.so failed (/usr/lib/dri/r200_dri.so: undefined symbol: _glapi_Dispatch)
libGL error: unable to load driver: r200_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
naf@home:~$ 
```

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
``` resulted in:
```
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
```

---

### Post by quelx on 2008-05-20
I'm at a loss, I don't have an ATI card in any of my systems, so I can't really drive along.

---

### Post by NaF on 2008-05-20
> **quelx said:**
> I'm at a loss, I don't have an ATI card in any of my systems, so I can't really drive along.

I'm sorry I took up so much of your time, thanks for the help anyway :)

---

