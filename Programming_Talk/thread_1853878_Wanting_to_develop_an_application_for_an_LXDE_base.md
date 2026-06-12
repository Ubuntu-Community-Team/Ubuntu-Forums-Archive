---
title: "Wanting to develop an application for an LXDE based system"
date: 2011-10-03
forum: Programming Talk
---

### Post by ojdon on 2011-10-03
Hi there, I am interested in developing an application for my Lubuntu installation on my netbook. Basically it's going to be a launcher similar to [this]("http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/").

I already have a fair bit of programming experience under my belt including languages such as Java, C, C++ but don't mind learning a new language in order to achieve creating my project. So what's the best language/environment to use in order to develop a graphical application for LXDE?

---

### Post by scitron on 2011-10-03
Given that LXDE is written in C using the GTK+ toolkit those would seem to be the most obvious choices.

I would also consider using Cairo and/or OpenGL, but since LXDE is aiming to be a "lite" desktop maybe OpenGL is out, Cairo might work well.

So I would be looking at a combination of C, GTK+, Xlib, Cairo and maybe OpenGL.

---

