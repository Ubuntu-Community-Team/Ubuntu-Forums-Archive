---
title: "Virtualbox Won't Start"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by cafeinoz on 2008-11-08
I use Intrepid Ibex with the 2.6.27-7-generic linux kernel and when I try to start XP using virtualbox it says /dev/vboxdrv dose not exist. I tried installing a few virtualbox packages but I cant get it to work.

---

### Post by cafeinoz on 2008-11-08
Can't anyone tell me what package to install?

---

### Post by Elfy on 2008-11-08
Is that all the error tells you - virtual box is usually quite good at giving suggestions when there's an error - eg

This is wrong. Do this to fix it.

Might help to post the error that you get.

Is it the OSE version from the repos or the PUEL from vbox themselves.

And don't bump so soon please.

---

### Post by zvacet on 2008-11-08
```
sudo /etc/init.d/vboxdrv setup
```

Maybe that will help.And of course you add yourself to vboxusers group.If you didn´t you can do it like this

```
sudo usermod -G vboxusers -a username
```

---

### Post by cafeinoz on 2008-11-08
I tried sudo /etc/init.d/vboxdrv setup and it gave an error but after a few minutes of updating and installing packages I got it to work but thanks any way.

---

