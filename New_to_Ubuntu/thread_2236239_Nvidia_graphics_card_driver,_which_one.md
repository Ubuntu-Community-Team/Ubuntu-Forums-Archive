---
title: "Nvidia graphics card driver, which one?"
date: 2014-07-25
forum: New to Ubuntu
---

### Post by maltfrisky on 2014-07-25
Hi there

So the first time I installed 14.04 I went to additional drivers, installed NVIDIA graphics card drivers and on the restart got the black screen of death :(

So after doing a fresh install and trying different drivers I kept getting the same thing, so left it for a few months.

I'm not 100% sure with updates that this has been sorted but I'm slightly nervous trying this again.

I've attached a screen shot of my laptops specs and the driver options.

Please let me know which is the safest.

Cheers

Jonny

---

### Post by sp40140 on 2014-07-25
Don't fix it if it isn't broke. I suggest you keep the current set-up, unless you are having issues. You don't have to run prop drivers from Nvidia (like windows). If open source drivers work well. I suggest you keep them.

---

### Post by maltfrisky on 2014-07-25
It's mainly for Steam so some games run without a problem Super Meat Boy for example but other games such as System Shock 2 have problems.  I assumed it was the lack of graphics card use... unless I'm missing something with Steam.

---

### Post by sp40140 on 2014-07-25
Well.. In that case.. It's tiral and error thing. Try 331 updates first.

---

### Post by oldfred on 2014-07-25
I think you should just use the newest available. But you need to know if using Intel or nVidia if yours is switchable. If just different output video ports then not switchable.
Do not install another nVidia driver without totally purging old one, if you installed one before. They tend to have conflicts. If you got black screen, it sounds like nVidia did not fully install?

 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Even my now 5 year old nVidia card is supported by current nVidia driver, but will be only supported by a legacy driver when current hits 340.xx.

 NVIDIA is ceasing to support their older GeForce 8, 9, 200, and 300 series from their mainline driver but the NVIDIA 340.xx driver series will become a long-term legacy driver that they will commit to supporting until April of 2016. 
[http://nvidia.custhelp.com/app/answers/detail/a_id/3473](http://nvidia.custhelp.com/app/answers/detail/a_id/3473)

---

### Post by maltfrisky on 2014-07-25
Thing was it was a fresh install when I used the additional drivers and I still got the black screen of death.

That's why I'm a bit nervous because I don't want to go through the whole installation process again.

I did try following tutorials to prevent the black screen and also reverting it but nothing seemed to prevent it.

Plus I've got 14.04 just the way I want it now so anything that goes wrong means another day to waste getting it back the way it was.

The settings that are in the screen shot are the way they are now.

---

### Post by oldfred on 2014-07-25
You can always test, by creating a 10 to 20GB partition and install to that. Basic install does not take long and then you can test nVidia driver.

I now install directly from ISO loopmounted with grub from hard drive. Even with updates it is less than 20 minutes to install, if I have partition(s) created in advance.

---

