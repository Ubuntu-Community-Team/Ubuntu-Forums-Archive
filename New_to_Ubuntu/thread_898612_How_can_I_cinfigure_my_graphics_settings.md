---
title: "How can I cinfigure my graphics settings"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-08-23
Hi,

To solve some Google Earth 4.3 issues on my Feisty machine, I want to make sure all 3D options are ON.

How can I see and change my 3D settings in Feisty?

Thanks,

Udi

---

### Post by ggaaron on 2008-08-23
glxinfo  | grep 'direct rendering'

yes means that everything is OK

If it is no then post what video card do you have?

---

### Post by Udibuntu on 2008-08-23
> **ggaaron said:**
> glxinfo  | grep 'direct rendering'

yes means that everything is OK

If it is no then post what video card do you have?

I got a yes, but I was looking for something more like dxdiag.

Thanks anyways,

Udi

---

### Post by ggaaron on 2008-08-23
You can just use glxinfo to get information about acceleration. From what I read this DxDiag handles more things than just acceleration.

Try this commands
glxinfo - acceleration
lshw - everything about your hardware (probably you should run it with sudo)
lspci - list all pci cards
uname -a - linux version, hostname and so on
lshal - list hal information (a lot of hardware is used on GNU+Linux via hal)
xrandr - show monitor settings

---

### Post by Udibuntu on 2008-08-24
> **ggaaron said:**
> You can just use glxinfo to get information about acceleration. From what I read this DxDiag handles more things than just acceleration.

Try this commands
glxinfo - acceleration
lshw - everything about your hardware (probably you should run it with sudo)
lspci - list all pci cards
uname -a - linux version, hostname and so on
lshal - list hal information (a lot of hardware is used on GNU+Linux via hal)
xrandr - show monitor settings

Thanks man, I'll use them.

My current problem is a Google Earth bug and not Ubuntu related. AFAICT.

Cheers

---

