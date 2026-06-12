---
title: "Ubuntu boots into tty1 virtual console login"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by sydney2 on 2013-11-13
Hello Forums.....

I have been using Ubuntu 12.04 for quite a sometime. It works well. Well just a couple of days back I set up a Nvidia Graphic card, a Geforce 7600 GS model. The drivers were well installed. However since they were not auto loading at startup I had to to add a startup program of its settings to load them  "nvidia-settings --load-config-only" and that was successful. But a slight problem has now cropped up. When I boot into Ubuntu I get the tty1 virtual console login screen. If i wait for just a bit it gets ahead and boots normally into the desktop. 

So Is there a way to avoid the virtual login screen and directly get started with the desktop login ...

Well any help would be greatly appreciated........

Sydney2....

---

### Post by squakie on 2013-11-13
Interesting - I get the same thing with the AMD drivers and Catalyst for my AMD/ATI graphics card.  I didn't need to add anything to start up the settings though.  Mine also goes to the normal GUI after a short period.

I'm not any sort of expert on nVidia based cards, having very limited experience with them.  I will ask - what did you do to install them?  I would probably have made sure I was connected to the internet, done a sudo apt-get update and a sudo apt-get upgrade, then gone to restricted drivers to see if any were available.  I might also have checked in Synaptic Package Manager to see what was available in the way of open-source drivers - not sure but I think there is something called Nuveao, but I don't know if that's open source or not - I've just seen it mentioned in some of the threads I have read.

---

### Post by sydney2 on 2013-11-13
Well frankly speaking I just got to the System-settings & using the additional drivers I got it installed. Although initially when the additional drivers were not installed the Ubuntu logo at startup appeared differently I would rather say the normal way but after the install it appeared boring like something spread-ed out.Well did it appear for u in this way ?

Secondly I don' t know if it has to do  something with the xorg.conf. This file was suggested to be deleted if the nvidia drivers were to be uninstalled.So I tried it in this way: 

sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop
sudo rm /etc/X11/xorg.conf
echo 'nouveau' | sudo tee -a /etc/modules

But after reinstallation the file stayed absent and the same problem occured.

So I seem a bit confused. Well any help would be greatly honored...

Thanks...

Sydney2

---

