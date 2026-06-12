---
title: "[SOLVED] Disable cdrom auto detect"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by bprof on 2008-08-01
I'm using ubuntu 8 and trying to make an iso image from a cd, everytime I put the cd in, ubuntu detects the cd I try to umount so I can make the is using dd but I'm getting no medium found error.

I guessing its because of the auto detect, is there away to disable the auto detect?

Thx

---

### Post by eightmillion on 2008-08-01
Go to System > Preferences > Removable Drives
and Media (or run gnome-volume-properties), and select the appropriate
options.

---

### Post by bprof on 2008-08-02
I tried that but it didn't work for me. Anyways I was able to make an iso image using the following command

> cat /dev/scd0 > /tmp/image.iso

instead of 
> dd if=/dev/cdrom of=/tmp/image.iso

---

