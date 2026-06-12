---
title: "Java3d and Eclipse"
date: 2007-12-10
forum: Programming Talk
---

### Post by Seb1982 on 2007-12-10
Hi everyone!

I'm currently working on a robot programming project ("c't-bot": [http://www.heise.de/ct/projekte/ct-bot/](http://www.heise.de/ct/projekte/ct-bot/) , german). The project files come with a simulator for which Java3d is necessary. Java3d is installed correctly but when starting a simulation in Eclipse all I get is a gray window. It works fine in the lab where i'm using a M$-Windows-PC.

Is it possible that some paths or parameter are not set correctly in Eclipse?

My System: Ubuntu 7.04 on BenQ-Notebook (see below)

Thanks for Help!

Seb

---

### Post by xlinuks on 2007-12-10
I guess you should have a look at the logs.
If it doesn't give you any clue what's up then start with the very beginning and find out whether you can run a 3D hello-world like program in Eclipse. If not, then there's something wrong with the 3D installation (perhaps missing the libraries or put them in the wrong directory). If it runs then there's something wrong with the project configuration.
Just my 2 cents

---

### Post by jespdj on 2007-12-10
Java3D uses OpenGL to render 3D graphics. What video card does your computer have? What video drivers are you using? Are hardware-accelerated 3D graphics supported on your video card / by your driver on Linux?

It sounds more like an issue with your video card or driver than with Eclipse.

---

### Post by Seb1982 on 2007-12-11
Hi everyone!

I found out that GLX 1.2 seems to be the problem. My application needs, as far as I know, version 1.3.

Is it possible to upgrade to 1.3 without destabelising my system? And if yes, how do I upgrade?

Thx

Seb

---

