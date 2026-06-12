---
title: "[SOLVED] DVD+/-RW drivers missing"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-06-24
I have a 8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability on my dell inspiron 1420. I have burnt discs before, but when I went to burn a normal 4.7 Gb DVD+R today it told me that it had to be a dual layer disc. Why is it doing that? I tried to burn it in Braseo and K3b.

---

### Post by cariboo on 2008-06-24
There is a bug in the dvd+rw tools see here:

[https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/235381](https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/235381)

Jim

---

### Post by slughappy1 on 2008-06-24
I checked that out, but in Synaptic there is only one dvd+rx-tools. How can I downgrade?

---

### Post by halitech on 2008-06-24
have you double checked the size of the image you were trying to burn? maybe it is just beyond the size that will fit on a normal dvd and that is why it was looking for a dual layer

---

### Post by slughappy1 on 2008-06-24
The disc I was using was a blank 4.7 Gb DVD. The files came up to 4.3 Gb

---

### Post by halitech on 2008-06-24
a 4.7gig dvd will only actually hold about 4.4gig worth of data (4482meg to be exact) so as long as it is under that it should be able to burn it. I had a problem with my old burner at one point doing the same thing, if I remember right, turned out the drive was dying :(

---

### Post by slughappy1 on 2008-06-24
Well I am pretty sure it was below that, but I tried to burn the same files on a different computer, but it failed during burning.

---

### Post by halitech on 2008-06-24
maybe its a problem with some of the files then

---

