---
title: "how do i add cflags"
date: 2011-03-17
forum: Packaging and Compiling Programs
---

### Post by termin on 2011-03-17
the whole point of compiling on my old pentium3 is to make sure that i get optimized code. I am a newbie to cflags and optimized codes. The first app that i ever compiling with these was firefox, however, that was easy because of the .mozconfig file.Now, i am trying to add cflags to mplayer. I can't figure it out. The shell i use is ZSH incase that's important. :confused:

thanks for your help

---

### Post by wojox on 2011-03-17
Here's where I learnt about CFlags [Compilation Optimization Guide]("http://www.gentoo.org/doc/en/gcc-optimization.xml")

---

### Post by termin on 2011-03-17
thanks for the fast reply, but i still don't understand where to implement it in ubuntu. Would it work if i add it in /etc/make.conf? I tried finding that file but it does not exist. If i make that file and add cflags to it, then what command will i use to execute it when compiling?

---

### Post by Simian Man on 2011-03-17
> **termin said:**
> the whole point of compiling on my old pentium3 is to make sure that i get optimized code.

That usually doesn't make nearly such a big difference as you might imagine.  Turning off services and using lighter apps will make a much bigger difference.  Moreover, if you're using a distro that compiles its packages for 686, like Arch or Fedora, that will get most of what little benefit there is of specifying your architecture to gcc.

---

### Post by termin on 2011-03-17
So what are lighter alternatives then? i already use opera as a (almost) replacement for firefox. what other alternatives are there? please list one for nautilus, it hogs up more than 20MB of ram on this machine. On my pentium4 machine, it only takes up 5MB. I am still not sure why

---

### Post by Simian Man on 2011-03-17
> **termin said:**
> please list one for nautilus, it hogs up more than 20MB of ram on this machine.

Thunar and PCManFM are both lighter file managers.  I would personally not run Gnome on a Pentium 3 at all.

---

### Post by termin on 2011-03-17
okay, thanks. i think that if i install XFCE then i would be good. Thanks for your help

---

### Post by Ibidem on 2011-03-17
By the way: Ubuntu has been built for i686 (Pentium II+, more or less) since 10.10.
However, it seems to get more bloat by the release.
Xfce is lighter than gnome, but lxde (includes pcmanfm) is lighter than xfce.

Gnumeric for a spreadsheet, Abiword for a word processor, mtpaint instead of Gimp for graphics, lxterm instead of gnome-terminal, and similar choices are all helpful.

---

