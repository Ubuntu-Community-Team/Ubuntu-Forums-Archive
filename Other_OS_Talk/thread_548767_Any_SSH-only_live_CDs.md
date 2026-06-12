---
title: "Any SSH-only live CDs?"
date: 2007-09-11
forum: Other OS Talk
---

### Post by MethodOne on 2007-09-11
I am interested in a live CD that only does telnet and SSH.  It must run on very recent hardware and older systems.  I tried [this](http://souptonuts.sourceforge.net/cdrom.htm) and [this](http://www.minimalinux.org), but those instructions involve using an older kernel.   What do you suggest I do?   I don't want to spend a lot of time building one from scratch.

---

### Post by init1 on 2007-09-11
> **MethodOne said:**
> I am interested in a live CD that only does telnet and SSH.  It must run on very recent hardware and older systems.  I tried [this](http://souptonuts.sourceforge.net/cdrom.htm) and [this](http://www.minimalinux.org), but those instructions involve using an older kernel.   What do you suggest I do?   I don't want to spend a lot of time building one from scratch.
So you already tried TTY Linux? Why is using an old kernel a problem? 
Many floppy distros like Knopperdisk have ssh. You can do a floppy boot, or make an El Torito ISO. 
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)
[http://knopperdisk.knopper.tk/](http://knopperdisk.knopper.tk/)

---

### Post by MethodOne on 2007-09-11
I'm afraid the old kernel might not support a newer NIC chipset.

---

### Post by mips on 2007-09-12
Why don't you roll your own OpenBSD LiveCD. I saw some guides a while back that showed how to do it and it did not look to hard and it will be very small if all you want is telnet & SSH besides being pretty secure.

---

### Post by init1 on 2007-09-12
> **MethodOne said:**
> I'm afraid the old kernel might not support a newer NIC chipset.
It's worth a try. On my laptop (<1 year old) I cannot connect to the internet. But I can on a particular desktop (~1 year old)

---

### Post by Bachstelze on 2007-09-12
Gentoo's "Minimal CD" could also do the trick.

---

### Post by init1 on 2007-09-13
> **HymnToLife said:**
> Gentoo's "Minimal CD" could also do the trick.
Yeah, that's only 50MB.

---

### Post by MethodOne on 2007-09-16
I don't want a CD with partitioning tools or installers.

---

### Post by init1 on 2007-09-17
> **MethodOne said:**
> I don't want a CD with partitioning tools or installers.
It's going to be hard to find that, actually. The closest I can think of is TTY, but even that has fdisk and an installer. 
Maybe you could make a custom Slax CD.
Edit: I'll see if I can make you a custom distro, one with a new kernel and ssh. And nothing else.

---

### Post by MethodOne on 2007-09-18
Looks like I'll stick with SLAX.

---

### Post by fistfullofroses on 2007-09-18
you could do a Debian Live CD and select the minimal base sytem and then for optional packages bash, screen, and ssh.

add "deb [http://live.debian.net/debian/](http://live.debian.net/debian/) etch main" to an ubuntu or debian sources.list
then you would "# apt-get install live-helper"
after that cd ~ and "# make-live config"
cd debian-live/config
then I think it is chroot_local or something similar...
change the line that says standard to minimal
and then in chroot local packageslists
make a file that lists
bash ssh

---

