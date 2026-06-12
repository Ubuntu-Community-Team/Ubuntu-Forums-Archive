---
title: "dpkg to rpm"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by djallalnamri on 2008-11-14
*hello
*i am totally new to linux
*since i cannot solve the screen resolution problem on ubuntu (gforce4 mx440 with agp8x vbios) i thought i could use mandriva which make no problem with the same graphic card;it's ok but on mandriva  blender and gimp which are my favourite graphic apps are older versions than the ones in debian packages so is there a way to simply convert those dpkgs to rpms so that i could use them on mandriva....
*thanks in advance

---

### Post by vgots on 2008-11-14
> **djallalnamri said:**
> *hello
*i am totally new to linux
*since i cannot solve the screen resolution problem on ubuntu (gforce4 mx440 with agp8x vbios) i thought i could use mandriva which make no problem with the same graphic card;it's ok but on mandriva  blender and gimp which are my favourite graphic apps are older versions than the ones in debian packages so is there a way to simply convert those dpkgs to rpms so that i could use them on mandriva....
*thanks in advance

[http://itknowledgeexchange.techtarget.com/linux-lotus-domino/convert-your-dpkg-rpm-tgz-and-slp-to-another-package-with-alien/](http://itknowledgeexchange.techtarget.com/linux-lotus-domino/convert-your-dpkg-rpm-tgz-and-slp-to-another-package-with-alien/)
hope it helps

---

### Post by CatKiller on 2008-11-14
[alien]("http://packages.ubuntu.com/intrepid/alien")

---

### Post by MasterSander on 2008-11-14
apt-get install alien

alien -r <yourpackage>

---

### Post by LowSky on 2008-11-14
I check you old post and you never mention a mx440
what problems are you having with the drivers?

---

### Post by djallalnamri on 2008-11-15
> **LowSky said:**
> I check you old post and you never mention a mx440
what problems are you having with the drivers?
*hello and thanks very much for replies
*it is true that i did not mention a mx440 before because i had a gfx that i have "crashed" accidentally (at the time i was trying to solve a webcam problem -a microdia 045c:627b-,problem which i could never solve too) and this mx440 was lent by a friend in waiting to buy a new one -it is this friend who is in charge of my hardware-,my main digital hobby is computer graphics but may be i should wait till i get that new graphic card:may be a new model will make less problem;the readme which comes with the nvidia-linux driver package did not mention that how to change runlevel before starting the procedure so i have to learn this first
*well i am the guy who googles a lot before asking questions and i knew about "alien" so i thought may be asking questions about converting dpkgs to rpms will bring more solutions about...and of course safer ones for an absolute beginner like me;i have tried envyng and legacy nvidia glx packages and all that it did was to turn off screen when i start ubuntu
*thank a lot again

---

