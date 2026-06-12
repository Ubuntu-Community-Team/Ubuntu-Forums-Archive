---
title: "What's the difference between Ubuntu 3D and Ubuntu 2D?"
date: 2015-10-26
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-10-26
Hello guys 
What's the difference between Ubuntu 3D and Ubuntu 2D?

---

### Post by howefield on 2015-10-26
Do you mean what's the difference between Unity 3D and Unity 2D ?

The latter was designed for machines without gpu hardware acceleration, similar in looks to the 3D version but without many of the "fancy" effects. It was intended as a fallback for machines that couldn't handle the 3D version.

I think Ubuntu 12.04 was the last release to include it, so it survives till April 2017.

---

### Post by grahammechanical on 2015-10-26
Ubuntu has used Compiz as the Compositor/window manager for some years. And if the graphic adapter lacked the capabilities the user could not activate special or fancy effects. The Unity 3D user interface is a plugin to Compiz and it makes use of special effects and requires a capable graphic adapter. The Unity 2D user interface uses Metacity as the window manager. So, a whole different set of libraries would be installed.

Today's versions of Ubuntu use an open source video driver called Gallium llvm pipe to give an approximation of Unity 3D on graphic hardware that cannot do hardware accelerated 3D rendering. So, Unity 2D is not needed any more.

Some people like the look of the old Gnome 2 panel. We get that on new versions of Ubuntu by installing Gnome Session Flashback. Which will install Metacity.

[http://www.mesa3d.org/llvmpipe.html](http://www.mesa3d.org/llvmpipe.html)

Regards.

---

### Post by Mike_Walsh on 2015-10-26
> **howefield said:**
> Do you mean what's the difference between Unity 3D and Unity 2D ?

The latter was designed for machines without gpu hardware acceleration, similar in looks to the 3D version but without many of the "fancy" effects. It was intended as a fallback for machines that couldn't handle the 3D version.

I think Ubuntu 12.04 was the last release to include it, so it survives till April 2017.

I **was **going to make reference to the 'Gnome-Flashback session', but I see Graham's already admirably explained it...

> **grahammechanical said:**
> Ubuntu has used Compiz as the Compositor/window manager for some years. And if the graphic adapter lacked the capabilities the user could not activate special or fancy effects. The Unity 3D user interface is a plugin to Compiz and it makes use of special effects and requires a capable graphic adapter. The Unity 2D user interface uses Metacity as the window manager. So, a whole different set of libraries would be installed.

Today's versions of Ubuntu use an open source video driver called Gallium llvm pipe to give an approximation of Unity 3D on graphic hardware that cannot do hardware accelerated 3D rendering. So, Unity 2D is not needed any more.

Some people like the look of the old Gnome 2 panel. We get that on new versions of Ubuntu by installing Gnome Session Flashback. Which will install Metacity.

[http://www.mesa3d.org/llvmpipe.html](http://www.mesa3d.org/llvmpipe.html)

Regards.

^^^ +1!!


Regards,

Mike. ;)

---

