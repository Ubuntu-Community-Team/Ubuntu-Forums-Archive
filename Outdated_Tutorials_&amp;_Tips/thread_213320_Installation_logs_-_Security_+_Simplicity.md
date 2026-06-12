---
title: "Installation logs - Security + Simplicity"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by madblueimp on 2006-07-11
Hi there, Ubuntu Users,

Since I tried out the Xubuntu-Desktop-Live-CD,
I've been impressed so much, I installed it on my worstation PC
and on my Laptop.

I already wrote some [Linux-Tips](https://blueimp.net/forum/viewtopic.php?t=230) (German) and therefore wanted to log my installation for the community.

Important for me above all were two things:
**Security and Simplicity**

Therefore, I installed /home on a separate partition, encrypted with dm-crypt + LUKS
and mounted /tmp as tmpfs.

For the simplicity, loggin in is all I have to do to have /home decrypted,
thanks to pam-mount.

Simplicity means to me as well that all my programs and libraries can be updated
through the package management.
To accomplish this, I installed my system without any need to compile a package by hand,
although I had [Gentoo on my System](https://blueimp.net/forum/viewtopic.php?t=278) once for a short time.

In a short article about [Ubuntu, Kubuntu and Xubuntu](https://blueimp.net/forum/viewtopic.php?t=282)
I explained why:
> For me, it was time again to remind myself that I should USE my System more than I'm configuring it.

So all the programs I use reside in the Ubuntu repositories (including the Universe, Multiverse and Commercial channels).
The only exceptions are the w32codecs and libdvdcss to play copy-protected DVD's.

As a Xfce-User, I focused as well on avoiding any KDE-libraries and installing only few Gnome-libraries.
But this is a matter of taste and has only the advantage of upgrading fewer packages. 

Although the installation has been done with Xubuntu, it should be useful for Ubuntu/Kubuntu-users as well.

Here now the links to the logs:

[http://blueimp.de/upload/linux/xubuntu.txt](http://blueimp.de/upload/linux/xubuntu.txt)
[http://blueimp.de/upload/linux/xubuntu-laptop.txt](http://blueimp.de/upload/linux/xubuntu-laptop.txt)

(The logs are plain text files, so you can read them in a console while installing.)

Greetings,

madblueimp

---

### Post by madblueimp on 2006-10-17
I created a new **Linux Tutorials and HowTos** section on [blueimp.net/linux/](https://blueimp.net/linux/).

For a Xubuntu installation, you might benefit from reading my "Xubuntu Installation Log" (the xubuntu.txt file) which is an updated version of the one I had on [blueimp.de](http://blueimp.de) before.

---

