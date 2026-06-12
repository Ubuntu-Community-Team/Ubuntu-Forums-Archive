---
title: "[SOLVED] How to browse File System in Ubuntu"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by electroblaze1989 on 2008-05-30
finally i've got Ubuntu working after stuggling unsuccessfully with my file partition. i eventually used Wubi and now its working fine...

i want to know how to browse my files that i had when i was using Windows...especially the media...i know there is something called Nataulius which allows you to do that but i'm not very sure...Plz assist...

---

### Post by Duck2006 on 2008-05-30
You have to have ntfs-3g drivers installed. System -> Administration -> Synaptic and load ntfs-3g drivers from there. Then make sure your win drive is mounted.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

and you should be able to browse the drive.

---

### Post by electroblaze1989 on 2008-05-30
actually i found a folder called host in the main explorer...i am able to view all files there...but thank you for your quick assistance..

---

### Post by ukripper on 2008-05-30
> **electroblaze1989 said:**
> finally i've got Ubuntu working after stuggling unsuccessfully with my file partition. i eventually used Wubi and now its working fine...

i want to know how to browse my files that i had when i was using Windows...especially the media...i know there is something called Nataulius which allows you to do that but i'm not very sure...Plz assist...

Go to to places-->computer and your windows drive should appear there and just click it. Note: it will only be in read only mode to enable writable to NTFS partition you need ntfs-3g as described by above post.

---

