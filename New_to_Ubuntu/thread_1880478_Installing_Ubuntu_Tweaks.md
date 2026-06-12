---
title: "Installing Ubuntu Tweaks?"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-11-13
I'm not real good at installing things unless it's in the synaptic package manager and I have searched for **Ubuntu Tweaks** there, and can't find it.
I did download it from the webpage 
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")
and have it setting on my desktop.

Can someone help me with the terminal command etc. ?

---

### Post by beew on 2011-11-13
If you are still using Ubuntu 11.04 or below you can install Ubuntu tweak using ppa.

Open Synaptic, go to Settings > Repositories > Other Software and click "add" then copy the line > ppa:tualatrix/ppa into the box, close the dialogue box, click "reload' and you should be able to find Ubuntu tweak in Synaptic.

Alternatively, you can install the .deb file you downloaded by right clicking it, or open a terminal, change directory into where the file is, say you save it on the Desktop and install it with the dpkg command

```
cd Desktop
sudo dpkg -i nameoffile.deb
```If you want to right click install, I suggest you install the package gdebi from synaptic and use it as the default application to open .deb files, otherwise the Software Center will do the installation and by the time it starts you would have finished installing with gdebi. 

The advantage of ppa is that you will be able to receive updates when they are available just like any software you install via Synaptic, whereas if you install by downloading a .deb file it will not be updated.

---

### Post by Greg Mueller on 2011-11-13
Thanks
It worked perfectly

---

