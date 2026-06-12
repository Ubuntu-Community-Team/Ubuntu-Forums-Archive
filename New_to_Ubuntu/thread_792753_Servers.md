---
title: "Servers???"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by cafeinoz on 2008-05-13
What is a server and how is Ubuntu 8.04 Server compared with Ubuntu 8.04 desktop?:confused:

---

### Post by Joeb454 on 2008-05-13
Ubuntu server is just a command line interface when you install it. If you want to run Ubuntu, you will want the desktop edition :)

It should be noted that you can actually make the server edition similar to the desktop edition, and visa verca

---

### Post by tribaal on 2008-05-13
Yeah the server edition is the same as the desktop, except that it doesn't install a GUI (like GNOME or KDE), and that the default kernel installation is [preemptible]("http://en.wikipedia.org/wiki/Preemptive_multitasking") (which is desirable on heavy-loaded servers, but pointless on a workstation).

As Joeb454 said, you can easily install a desktop on top of a server install using the apt package manager ("sudo apt-get install ubuntu-desktop").
It is however quite lenghty and painful to strip a desktop install from all its GUI components to use as a server...

Hope this helps.

- Trib'

---

