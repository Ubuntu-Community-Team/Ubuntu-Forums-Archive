---
title: "slitaz"
date: 2008-06-05
forum: Other OS Talk
---

### Post by AnLGP on 2008-06-05
Hello,

I'm curious has anyone here used (enjoy/love/istalled on HD even) slitaz?

I'm using a live CD right now and have found out that I love the size (it's 25MB!!) and that you can customize it a bit:

[http://www.slitaz.org/en/doc/handbook/gen-livecd.html](http://www.slitaz.org/en/doc/handbook/gen-livecd.html)

but am curious.  is there a place that would list all the packages you are able to install?  I'd like to remove some and add others.

---

### Post by cardinals_fan on 2008-06-05
SliTaz is fun.  It's also a little buggy.  However, they're doing a good job and it gets better with every version.

---

### Post by init1 on 2008-06-05
I have and I love it :D
It's one of my favorites by far.
The package manager that it uses is called tazpkg. There is an option for it to display all packages, but I don't remember what it is. The newest cooking ISO has a GUI for tazpkg, so you may want to try that. 
[http://ubuntuforums.org/showthread.php?t=739424](http://ubuntuforums.org/showthread.php?t=739424)
[http://download.tuxfamily.org/slitaz/iso/cooking/slitaz-cooking.iso](http://download.tuxfamily.org/slitaz/iso/cooking/slitaz-cooking.iso)

---

### Post by K.Mandla on 2008-06-06
I use it off and on, depending on my needs. It's much more friendly than DSL, and much smaller too.

---

### Post by Dr Small on 2008-06-06
I have in and use it on occasions. I love how tiny it is :)

---

### Post by kagashe on 2008-06-22
I tried slitaz 1.0 yesterday.

Generally, I don't like to waste a CD (also the CDRom drive does not work anyway), I mounted the iso and copied the contents to a spare partition. Following grub line was available in /boot/grub/example-menu.lst file:
title  SliTaz GNU/Linux
kernel /boot/bzImage root=/dev/null vga=771
initrd /boot/rootfs.gz

I added root 	(hd0,X) line and could but in Live Slitaz.

As per Slitaz handbook, if you extract rootfs.gz by using lzma and cpio, it becomes a hard disc install. Initially I tried lzma and cpio of Hardy. It did not work. Then I tried lzma and cpio of Slitaz live environment and it worked. After extracting I deleted rootfs.gz and init as per instructions and changed the grub entry to:
title  SliTaz GNU/Linux 1.0
       root(hd0,X)
       kernel /boot/vmlinuz-2.6.24.2-slitaz root=/dev/hdaX+1 vga=normal

The memory usage gets reduced on HD install compared to Live environment and it is very fast.

kagashe

---

