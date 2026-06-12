---
title: "should i be seeing lag on this system?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by KeithF40 on 2008-08-24
asus a7v600
amd athlon xp 2500+
1.5 gb ram (pc3200 i think)
120 gb wd sata drive
ati radeon 9800 pro

running ubuntu (latest version 10 point something)

put appearance on clearlooks, i think it is less demanding than the default, am i right, also i dont like the orange, this clearlooks is blue apparently

also put visual effects at none, would prob prefer that neway, i dont like all the glits and glamour.

seems like some menus are lagging a tad, i think this computer is going on its last leg anyway but should i be seeing any lag and if so how can i fix it.

---

### Post by mgranet on 2008-08-24
I would say a bit of lag might be seen due to the video card or processor. BTW, the release version of Ubuntu is 8.04. If you want more speed, you can try Xubuntu, a lightweight member of the Ubuntu family.

---

### Post by Sinkingships7 on 2008-08-24
Your hardware seems pretty nice, except for the processor. That seems to be a bit outdated. It shouldn't be having trouble running Ubuntu w/ Metacity, but it might if you're running Compiz.

---

### Post by mgranet on 2008-08-24
The video card is ~2002 as well. Are you using proprietary video drivers?

---

### Post by dodle on 2008-08-25
Your specs look fine to me (I'm no professional). I'm guessing maybe you're having a problem with the video card driver.  Have you tried any other drivers?

---

### Post by KeithF40 on 2008-08-25
this is what i did for video

1) went to system>administration>hardware drivers and it came up with a dialog about enabling the 3d on my card and i selected yes and then it had to restart

2) downloading the linux x86 drivers for my card

then i went into terminal and figured out how to become super user

then i ran the command sh filename.run

i guess it installed itself



i dont know if i have metacity or compiz, how do i know.  i downloaded ubuntu straight from the ubunty website.

---

### Post by KeithF40 on 2008-08-25
Release 8.04 (hardy)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

---

### Post by mgranet on 2008-08-25
EDIT: Have you looked at Xubuntu? It should run quite well on older hardware.

---

### Post by KeithF40 on 2008-08-25
restricted drivers manager is not available.

hardware drivers is one

under THAT it lists device driver as "ATI accelerated graphics driver" and is checked for enable, i did that, and has a green dot saying in use.

idk if that is what you were referring to.

---

### Post by KeithF40 on 2008-08-25
no not yet.  what is the diffence?

---

### Post by Sinkingships7 on 2008-08-25
> **KeithF40 said:**
> this is what i did for video

1) went to system>administration>hardware drivers and it came up with a dialog about enabling the 3d on my card and i selected yes and then it had to restart

2) downloading the linux x86 drivers for my card

then i went into terminal and figured out how to become super user

then i ran the command sh filename.run

i guess it installed itself



i dont know if i have metacity or compiz, how do i know.  i downloaded ubuntu straight from the ubunty website.

If installing the one you downloaded worked properly, then you have two drivers installed. That might be the problem.

To see if you have Metacity or Compiz running, go to System -> Preferences -> Appearance and go to the Visual Effects tab. If it's on None, then you're running Metacity. If it's on Normal, Extra, or Custom, then you're running Compiz.

---

### Post by mgranet on 2008-08-25
It uses the XFCE desktop environment.

---

### Post by Sinkingships7 on 2008-08-25
> **mgranet said:**
> It uses the XFCE desktop environment.

What does?

---

