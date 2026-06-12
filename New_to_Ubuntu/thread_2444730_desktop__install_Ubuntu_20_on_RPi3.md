---
title: "desktop  install Ubuntu 20 on RPi3"
date: 2020-06-03
forum: New to Ubuntu
---

### Post by richard-g8jvm2 on 2020-06-03
Hi
I'm not unfamiliar with ubuntu as I've been using LM for many years
But in trying to get some software working on a RPI3B with raspbian , I gave up in disgust and loaded ubuntu20 on to it.

I downloaded the image, flashed it on to a SD card with Etcher, plugged it in and no problem , booted up in to CLI
I loaded ulbuntu-desktop,  but its not starting up automatically , its booting up in to CLI.
I can start it with "startx"
Where are the settings to get it booted in graphical mode.  ?
the subtle differences between distros :)

---

### Post by richard-g8jvm2 on 2020-06-03
OK , I've sorta fumbled my way through

I've installed the Mate desktop,   but why has it got debian logos on the background 
It looks nothing like the Mate desktop I use on my Odroids with ubuntu18.04
Whats lightweight, its only a raspberry PI3B, and looks a bit like the cinnamon desktop
Yeah I know cinnamon is not a ubuntu desktop, but its a sorta decendant of gnome2
gnome is far to heavy for a diddy PI
I didn't think much of lxde as it cut down KDE, and I'm not a fan of KDE

just some suggestions please

---

### Post by grahammechanical on 2020-06-03
Please remember that I am not speaking from experience but I think that the official way (if it can be called that) is to install Ubuntu server and then add a desktop of your choice.

[https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)

[https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)

I doubt if Snappy Ubuntu Core would be suitable as I do not think that a snap version of any Ubuntu desktop exists. 

Regards

---

### Post by richard-g8jvm2 on 2020-06-03
OK 
thanks for the reply
I did install the server first then the desktop, but getting the desktop to start was a Pain, I ended up using tasksel .
I may have another attempt in the morning, I only need a minimal desktop , preferable with gnome based applications, not KDE

---

### Post by ActionParsnip on 2020-06-06
I suggest LXDE or just Openbox or Fluxbox as standalone WM. This will leave more resources for your applications

---

### Post by DuckHook on 2020-06-06
Though not an RPi3, I do run an RPi4 using server + XFCE. Provided that you don't push the graphics beyond their capacity by asking for too much resolution, performance should be acceptable.

You are right. Getting the desktop to display properly was something of a pain. This thread might help: [https://ubuntuforums.org/showthread.php?t=2441007](https://ubuntuforums.org/showthread.php?t=2441007)

Re: the right DE/WM &#8212; please have a look at the link in my sig: "The Best 'buntu Flavour".

---

### Post by travis-falkenberg on 2020-06-07
Try 'sudo systemctl get-default'

It will probably return multi-user.target

If it does then use 'sudo systemctl set-default graphical.target'

You can switch back to the normal cli boot with 'sudo systemctl set-default multi.user.target'

Well this is my theory.

---

### Post by bobbyk56 on 2020-06-09
I  used LM for years but tried to install it on Lenova s145 ideapad and no go. Nothing. And it has not let me down all these years. The problem was it wouldn't recognize my internet. So. off to Ubuntu I go with no problems.

---

