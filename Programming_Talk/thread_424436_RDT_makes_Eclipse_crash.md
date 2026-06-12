---
title: "RDT makes Eclipse crash"
date: 2007-04-26
forum: Programming Talk
---

### Post by Hpatoio on 2007-04-26
I've a fresh installation of Feisty with Eclipse and I've already setup the system to use Sun JVM.

Eclipse works well, but after installing RDT it started to crash and freeze !

If I open a .rb file selecting "Open with text editor" everything is fine, but when I choose "Open with ruby editor" Eclipse freeze and after few minutes crash.

From the system monitor I can see the CPU usage jump to 100%  and the RAM usage too.

Does anyone has the same problem ? Of does someone knows how to fix it ?

Thanks 

Simone

---

### Post by JT673 on 2007-04-27
How did you install the VM?

I don't like to use the Debian package for Eclipse because some parts are broken, so download the tarball instead, and see if that works.

---

### Post by Hpatoio on 2007-04-27
Well, I've installed both Eclipse and sun JVM from the Ubuntu packages.

I'll try from the sources. I'll let you know if things get better ...

Simone

---

### Post by Hpatoio on 2007-05-01
NO, no way. 

Eclipse works well, but when I install RDT an I try to open a ruby file my CPU and RAM usage raise to 100% and after a while Eclipse crash.

Hope to find a solution.

Simone

---

