---
title: "A frambuffer-only OS? NO X!"
date: 2008-01-16
forum: Other OS Talk
---

### Post by ed_agamemnon on 2008-01-16
X eats my system resources. I hate it.

I do, however, love my framebuffer. I already use commandline web browsers (that show pictures!), and am trying to migrate to a framebuffer-only environment.

What distros are there out ther that don't have X, but are graphical, and well maintained (in terms of driver support)?

---

### Post by Nano Geek on 2008-01-16
Get Ubuntu-Server and install what you need from there.

---

### Post by voteforpedro36 on 2008-01-16
Or Arch, or Debian can not install a DE (it's net-install would work too).

---

### Post by SunnyRabbiera on 2008-01-16
well there is mepis antix

---

### Post by K.Mandla on 2008-01-17
There are a couple of very small distros that use xvesa or tinyx instead of the entire X desktop, and they run like a cat on fire. :shock: Maybe that was a bad analogy.

Slitaz is one. It's customizable and very light (a 25Mb ISO!) and has pretty good hardware support too.

[http://www.slitaz.org](http://www.slitaz.org)

Check the sticky at the top of this forum for more ideas. A few of the ultralight ones do the job you describe, but I don't know if any are purely framebuffer-oriented.

---

### Post by aeto on 2008-01-19
Just get a distro that has net-install option.

---

### Post by francisco_athens on 2008-01-19
It's not well known, but Ubuntu can indeed net [boot/install]("https://help.ubuntu.com/community/Installation/Netboot").  You can boot the tiny (10 MB) ISO that will pull Ubuntu debs off the web and you can also boot that via PXE (or boot over ethernet/wireless).  I've even copied the ISO contents to a flash drive and net-installed from that.  You can then to the CLI (server) install as suggessted above.

---

### Post by init1 on 2008-01-19
> **K.Mandla said:**
> There are a couple of very small distros that use xvesa or tinyx instead of the entire X desktop, and they run like a cat on fire. :shock: Maybe that was a bad analogy.

Slitaz is one. It's customizable and very light (a 25Mb ISO!) and has pretty good hardware support too.

[http://www.slitaz.org](http://www.slitaz.org)

Check the sticky at the top of this forum for more ideas. A few of the ultralight ones do the job you describe, but I don't know if any are purely framebuffer-oriented.
SliTaz is awesome (if you couldn't already tell from my avatar :D) and I'm using it right now. I'm not sure though if it's what you are looking for. Although it's X, it's fast and small. I would recommend a minimal Debian Etch bootable business card installation. That way you can install only what you need.

---

