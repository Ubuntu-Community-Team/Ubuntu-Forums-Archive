---
title: "Themes dont install right"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by t1nm@n on 2012-08-26
Hey i've been trying to get some theme up and running. Well, root applications dont wear the applied theme. I tried the traaditional method ```
 sudo ln -s /home/tin/.themes /root/.themes
 sudo ln -s /home/tin/.icons /root/.icons

```

but it doesn't work.

How can I fix this???

---

### Post by MG&amp;TL on 2012-08-26
Have you tried copying the files? I think I read somewhere something about a no-follow-symlinks option being set.

Graphical apps as root is a bad idea...just thought I'd point it out. :)

---

### Post by t1nm@n on 2012-08-27
yeah I did try copying the files...but no luck... I mean synaptic has the theme I want but Update manager and some windows dont have that....

---

### Post by vasa1 on 2012-08-27
> **t1nm@n said:**
> Hey i've been trying to get **some theme** up and running. ...

Which specific theme? Does it do both gtk2 and gtk3? Synaptic is gtk2. Update Manager is gtk3, AFAIK.

---

### Post by t1nm@n on 2012-08-28
So in my themes folder i need a gtk-3.0 folder too..huh. Well thanks I'll look for themes that have them.

thank you.

---

