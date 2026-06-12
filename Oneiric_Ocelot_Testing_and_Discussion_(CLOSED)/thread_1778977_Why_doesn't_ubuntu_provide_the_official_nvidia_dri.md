---
title: "Why doesn't ubuntu provide the official nvidia driver?"
date: 2011-06-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by someitalian123 on 2011-06-09
I'm using the official nvidia driver on my ubuntu pc, why doesn't ubuntu provide it. With the driver that was installed when I installed ubuntu couldn't even run unity, it couldn't even play back youtube videos smoothly. With the official nvidia driver I can watch youtube videos in 720p. Is it just because it's not open source, because Adobe Flash isn't open source either but that is still available in the repositories. It would be more convenient. I'm just wondering why doesn't ubuntu provide it?

---

### Post by ronacc on 2011-06-09
ubuntu does provide the "official" nvidia , several versions of it to cover a range of cards , I don't know where they hide it in unity but in classic it should be avail at system>administration>hardware-drivers , I think it should have been enabled automaticly .

---

### Post by Ichtyandr on 2011-06-09
Since natty I think if during install you tick the "install restricted extras" thing the binary nvidia driver will be installed automatically

---

### Post by cariboo on 2011-06-09
In Unity just click the applications icon and type add, and click on the additional drivers icon, Hardware drivers hasn't been used for the last two releases. On my Nvidia systems [noparse](9400GT, 8400GS, 6600GT, 6250LE and GT218)[/noparse] the nvidia-current driver works with zero problems.

---

### Post by cecilpierce on 2011-06-09
> **cariboo907 said:**
> In Unity just click the applications icon and type add, and click on the additional drivers icon, Hardware drivers hasn't been used for the last two releases. On my Nvidia systems [noparse](9400GT, 8400GS, 6600GT, 6250LE and GT218)[/noparse] the nvidia-current driver works with zero problems.

Tried the nvidia-current and it says activated but not in use so I am using the nouveau and 3d works but a little bit slow.
Geforce-6200

---

### Post by someitalian123 on 2011-06-09
I did not know it was the official one, I thought it was reverse engInered because of the poor  performance I was getting. Why doesn't the driver install during the ubuntu installation , it would be alot more convenient. I just assumed the driver was installed automatically since my sound card driver was installed automatically, and my monitor was at 1280x1024.

---

### Post by cariboo on 2011-06-09
The restricted drivers aren't installed automagically, because the Ubuntu philosophy is to only install free/open software during the install process, After the initial installation there will be a notification icon telling you restricted drivers are available.  it's up to you whether you want to use closed source drivers or not.

Canonical does have a developer (Alberto Milone) that packages the Nvidia and ATI closed source drivers, he usually has them ready for install within hours of their release by the manufacturers.

---

### Post by wildmanne39 on 2011-06-10
> **cecilpierce said:**
> Tried the nvidia-current and it says activated but not in use so I am using the nouveau and 3d works but a little bit slow.
Geforce-6200Hi, it saying that it is not in use is just a bug, if you enabled it it is in use, my says the same thing and I have the cube and effects working.

---

