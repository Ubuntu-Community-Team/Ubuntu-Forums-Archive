---
title: "Hardy Heron wireless and video drivers"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Ewm002 on 2008-06-27
Ok, as a Linux newbie,tried to install ndisgtk with Synaptic and it is not in the list. when I search the cd it is there and I am asked if I want to install using the Debian Package Manager which produces an error message.
Do I need a wired connection first to download extra packages?

Secondly this a new attempt at Linux for me with a new dual core amd 64 PC with no previous Windows installation. How do I get the new motherboard drivers to work  so I don't get stuck with a low res display

Thanks

---

### Post by overdrank on 2008-06-28
> **Ewm002 said:**
> Ok, as a Linux newbie,tried to install ndisgtk with Synaptic and it is not in the list. when I search the cd it is there and I am asked if I want to install using the Debian Package Manager which produces an error message.
Do I need a wired connection first to download extra packages?

Secondly this a new attempt at Linux for me with a new dual core amd 64 PC with no previous Windows installation. How do I get the new motherboard drivers to work  so I don't get stuck with a low res display

Thanks

Hi and welcome, You will need a internet connection, wired or wireless to download additional apps. Apps is short for applications.
Your motherboard drivers should be included in the kernel and what is the model of the graphics card in your system? You may use the command ```
lspci
``` in the terminal and look for VGA.

---

