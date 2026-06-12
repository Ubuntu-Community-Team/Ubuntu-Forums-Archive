---
title: "cannot find -lbsd"
date: 2006-05-01
forum: Programming Talk
---

### Post by technodolt on 2006-05-01
I can't figure out which forum to post this to, but this might be the right one.

I'm trying to compile the source of a program I want to use, and I'm getting this error:

/usr/bin/ld: cannot find -lbsd

I'm aware that this means I'm missing the libbsd files, but what I don't know is how to acquire them... I've been trying to find a package I can download with apt-get, but can't seem to figure out if there are any packages containing these files.

Can anyone help?

---

### Post by bonzodog on 2006-05-01
Synaptic seems to indicate that it might be a package called libbsd-resource-perl.

---

### Post by technodolt on 2006-05-01
That seems to have not done it, unless I'm missing something and I have to do more than just apt-get install libbsd-resource-perl... I'm new to ubuntu, and mostly new to linux, so I could be just not figuring something out.

---

### Post by LordHunter317 on 2006-05-01
There is no libbsd on Linux.  Not that I'm aware of anyway.  BSD compatibilty is provided by libc6 directly, plus perhaps some preprocessor defines where required.

---

