---
title: "no sound after upgrade"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by endtheembargo on 2008-06-30
Hi, I just upgraded to ubuntu, version 8.04 and suddenly I have no sound on my computer. What should I do?

---

### Post by NT4usB on 2008-06-30
un mute it..?
double click the speaker and look if master and/or pcm is muted.
Try changing the sound device in the same screen.

---

### Post by kansasnoob on 2008-06-30
I always start by installing 

> gnome-alsamixer

from synaptic. It then shows up under Sound & Video in gui form:

Left most view: [ATTACH]75834[/ATTACH]

Right most view: [ATTACH]75835[/ATTACH]

Lots of toggles to play with ........... and I'm a gui guy:D

---

### Post by dwhitney67 on 2008-06-30
I was going to suggest that you first read the countless other posts in this forum that deal with the same issue.

When a sound card doesn't work, it is probably because the driver (and/or driver options) is not loaded into the kernel.  I don't know what driver your card requires because you have not reported which sound card you have.

If you run this command and report back the results, then perhaps someone can assist you in tracking down which driver is needed:
```
$ lspci | grep -i audio
```

---

