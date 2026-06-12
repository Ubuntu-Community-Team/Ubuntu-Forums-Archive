---
title: "Compiz using 200+MB of RAM, is it right?"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by t1497f35 on 2011-09-29
Hi,
See title and screenshot.
Is this a bug or is it normal?

Oneiric amd64, GeForce gtx 560Ti with drivers from nvidia-current.


EDIT: to me this looks ridiculous since a few years ago a whole Linux desktop distro used < 200MB.

---

### Post by cariboo on 2011-09-29
I seem to recall a thread on compiz and memory leaks, but at the moment I can't seem to find it.

---

### Post by ventrical on 2011-09-29
> **t1497f35 said:**
> Hi,
See title and screenshot.
Is this a bug or is it normal?

Oneiric amd64, GeForce gtx 560Ti with drivers from nvidia-current.


EDIT: to me this looks ridiculous since a few years ago a whole Linux desktop distro used < 200MB.




I got the cube, bells and whistles and all I get is 37MB.

  I'll keep an eye on it of course.

---

### Post by MacUntu on 2011-09-29
Ubuntu 11.10 will release with some leaks (like compiz and unity-panel-service are a bit problematic this cycle). Unfortunately it's not always easy to fix them in time. :-)

---

### Post by catlover2 on 2011-09-29
> **ventrical said:**
> I got the cube, bells and whistles and all I get is 37MB.

  I'll keep an eye on it of course.


Same here, 33MB on Natty.

---

### Post by t1497f35 on 2011-09-29
Then this is indeed some kind of BIG FAT bug (or many small ones) cause I've been using the computer for like 2 hours.
Amazing difference, 33MB vs 200+.
Do you guys also use nvidia cards with proprietary drivers?

---

### Post by MacUntu on 2011-09-29
Nope, Intel HD graphics 2000/3000 here.

---

### Post by howefield on 2011-09-29
> **t1497f35 said:**
> Then this is indeed some kind of BIG FAT bug (or many small ones) cause I've been using the computer for like 2 hours.
Amazing difference, 33MB vs 200+.
Do you guys also use nvidia cards with proprietary drivers?

My oneiric install with an nvidia card/proprietary drivers has similar memory usage to yours, around 220 plus,  but my ATI install sees around 60megs.

Happened during the natty cycle as well, with some fixes before release bringing it down.

---

### Post by ventrical on 2011-09-29
> **t1497f35 said:**
> Then this is indeed some kind of BIG FAT bug (or many small ones) cause I've been using the computer for like 2 hours.
Amazing difference, 33MB vs 200+.
Do you guys also use nvidia cards with proprietary drivers?


On this one I use an ATI Radeon Express 1250.

I'll check my tower with GEforce 210.

---

### Post by cariboo on 2011-09-29
Compiz uses 33.9MiB on my Intel based netbook. and 144MiB on my Nvidia based desktop system.

---

### Post by t1497f35 on 2011-09-29
Thanks, so it looks like it only affects nvidia users.
I wonder if the compiz dev(s) know that their nvidia backend leaks quite a lot.
OTOH If compiz doesn't use custom code for nvidia hw, then this might be a leak in the nvidia proprietary driver.
Now it's too late here, I'll do a clean install of Oneiric tomorrow and use it with Nouveau for like an hour and see what happens.

---

### Post by ventrical on 2011-09-29
It's just surreal. I tested this on my nvidia based system. It started out at 76MB. As I run and exited other programs like gedit, disk-usage analyzer, terminal, snapshot ff etc.. I noticed the memory climbing up. As I exited these programs it appeared that the compiz buffer would not clear with the nvidia card.

  It kept climbing...to here_

---

### Post by ventrical on 2011-09-29
slowly climbing , climbing , climbing... appears that compiz is not clearing it's stack (or nvidia driver) is stuffing the buffer.

---

### Post by ventrical on 2011-09-29
..here..

---

### Post by ventrical on 2011-09-29
Not so fast ...

Conversely, if we drop down to the 3.0.0-11 kernel (with same bells and whistles) then the buffer is managed  much more efficiently.. hence this would force us to reasonably conclude that there is a problem with the last kernel update to -12

Also  compiz is not polling every 2 seconds in the -11 kernel like it is in the -12 kernel.

---

### Post by nerdy_kid on 2011-10-08
keep an eye on Xorg's memory too; both compiz and Xorg slowly grow in ram usage for me, and they almost double each time I suspend/resume.

---

