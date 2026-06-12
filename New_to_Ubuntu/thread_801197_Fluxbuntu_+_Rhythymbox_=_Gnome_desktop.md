---
title: "Fluxbuntu + Rhythymbox = Gnome desktop?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by heyho on 2008-05-20
Hi,

I'm experimenting with an Ubuntu-based box for my workshop, and currently have Fluxbuntu Gutsy installed (P3 128 meg ram).  It is for web surfing and playing music.

I installed Rhythmbox via aptitude, and it worked fine.  When the system was restarted, a gnome desktop appeared, followed by some error messages.  I was able to ctrl/alt/backspace to the command line and remove it(Rhythmbox) with aptitude - now I have flux back.

What did I do?  Is it not possible to run Rhythmbox outside of a Gnome environment, or should I have used apt-get?

Any help greatly appreciated!

---

### Post by Inxsible on 2008-05-20
rhythmbox is a defualt app for a gnome desktop. So what probably happened was when you installed it, the entire ubuntu-desktop was installed with it. It also probably made itself the default desktop - which is why you saw a Gnome desktop.

I would think there would be a way to install any app without having to install the entire gnome desktop.

---

### Post by heyho on 2008-05-20
Thanks for the reply.

I'm pretty sure that it wasn't the entire gnome desktop, as it was only 60 Mb or so I think.  I did notice it grabbing lots of gnome dependencies, but thought it to be normal as it is a gnome app.  It worked fine until the next restart.

---

### Post by heyho on 2008-05-21
Can anybody shed any light on this problem?

---

### Post by justin whitaker on 2008-05-21
> **heyho said:**
> Can anybody shed any light on this problem?

There are two different versions of GNOME and KDE in the repos: the one that is used in the -desktop versions, and a plain vanilla one. 

What you got was the core GNOME package to support installing rhythmbox...assuming that Fluxbuntu uses GDM, you should be able to reselect Fluxbox as your default and use rhythmbox as normal.

---

