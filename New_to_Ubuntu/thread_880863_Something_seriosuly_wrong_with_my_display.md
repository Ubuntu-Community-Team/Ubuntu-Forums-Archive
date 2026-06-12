---
title: "Something seriosuly wrong with my display"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by marshall1001 on 2008-08-05
I just installed a fresh version of Hardy from an install disc, the only thing I have done differently is that I told it to use the entire disc space and not partition it next to windows.

When i booted into Ubuntu again after install, it told me that my hardware could not be properly configured and that I needed to set my resolution manually, i was phased but did as I was told, however when ubuntu loaded the resolution was ridiculous, everything is enormous.

What on earth has happened? What have I done differently?

---

### Post by bobnutfield on 2008-08-05
What video card are you using?  If it is nVdia or ATI, you will need the drivers.  But, try this command:

> sudo dpkg-reconfigure -phigh xserver-xorg

This should get you back to a basic configuration that is usable.

---

### Post by marshall1001 on 2008-08-05
I have no idea what video card I'm using becuase its never been an issue before, i know its not capable of any desktop effects, however there has never been an issue with it before. I'll try that command now

---

### Post by bobnutfield on 2008-08-05
If you want to know what graphics card you have, you can issue the command:

> lspci | grep VGA

---

