---
title: "grub-gfxboot - kernel updates"
date: 2007-09-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Agrezar on 2007-09-01
Just wanted to steer some people in the right direction if installing

grub-gfxboot_0.97-11_i386.deb

I'm running it and found that if you get a kernel update you end up with an error something like .. 

> (2.6.20-??.?? was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2

it's because the update-grub script that the gfxboot installs is an sh but supposed to be bash..

[PHP]sudo gedit  /sbin/update-grub[/PHP]

[PHP]change the #!/bin/sh to #!/bin/bash[/PHP]

[PHP]sudo apt-get dist-upgrade[/PHP]

.. should work

...on another note, if perhaps your are upgrading kernels lets say kernel 2.6.20.15 --> kernel 2.6.20.16 and update-grub doesn't update your menu.lst (from above problem) you might not be able to boot haveing an error "file not found" ..

---

### Post by benste on 2008-02-15
wanted to delete my post

---

