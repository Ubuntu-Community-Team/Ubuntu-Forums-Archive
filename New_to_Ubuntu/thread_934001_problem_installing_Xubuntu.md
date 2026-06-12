---
title: "problem installing Xubuntu"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by 2blue on 2008-09-30
Hi 

Not too long ago I installed Ubuntu on an old laptop I have as I needed an extra workstation and it was a good way to get to know Linux. I first used 7.10 and then 8.04. Hardy Heron was the most trouble free of them and practicly was installed all by it's self and everything working instantly. 

This is an old machine Packard Bell Easy One, Dc 1712 DVD, Serial Number W794300017. 

I wantet to try Xubuntu, as it problaby will run faster on the old ting. Xubuntu does not install it self that easily. During the installing prosess neither harddisk is found or drivers for network card. I get a long list of harddisk drivers to choose from if I only new wich of them I needed. 

How do I go about this? Am I correct in assuming that Xubuntu will work on my old laptop since Ubuntu did?

---

### Post by jamesrl on 2008-09-30
Xubuntu should install just as easily as ubuntu.  If you can install ubuntu on the machine, you can install use the package manager to install xubuntu at a later time by 
```

sudo apt-get install xubuntu-desktop

```

I would guess from what you are saying that (regular) ubuntu won't install easily) and will have the same hardware problems.  This could be a fact of some part of your hardware died (unless its a dual boot and you can check), or for some reason the new version you are trying doesn't support the HW you are using fully right out of the box (e.g., it autodetects it wrong or you specify the wrong info).

---

### Post by 2blue on 2008-09-30
...hmm
Ubuntu still works just fine on the machine, harddisk and the network card seems to be all right(separate ethernet lan card). I thought I had to make a clean install of Xubuntu from CD to get the lighter running benefits on the laptop. 

When I started the machine after trying to install Xubutnu, the Ubuntu OS did a check of the harddisk during the booting, and it went just fine.

Is a clean CD-install preferable?

---

### Post by 2blue on 2008-09-30
...after restarting the laptop and repeating the procedure a few times, the installing cd seems take. I'm crossing all fingers and hoping for the best :)

---

### Post by 2blue on 2008-09-30
Xubuntu is up and running, and I'm posting from my xubuntu laptop :D

What is typically to run easier in Xubuntu compared to Ubuntu? Have anyone tried xubuntu on an old not so powerful laptop? I think this machine has 700 MHz Duron processor and about 10 GB harddisk, and when used everything will be stored on a memory stick.

---

### Post by aeiah on 2008-09-30
most things will run a little faster, but with some caviats. you should stay away from software that loads a lot of gnome or kde libraries, since you really just want gtk anf xfce libraries to be loaded. so try not to use nautilus, evolution, konqueror, k3b, amarok etc

if firefox runs sluggish there are several lightweight alternatives like [these](http://www.terminally-incoherent.com/blog/2007/10/02/lightweight-browser-rundown/)

---

### Post by snowpine on 2008-09-30
Xubuntu is no more than 10% faster than Ubuntu in my experience. The real benefit comes if you start using light-weight apps: Abiword instead of Openoffice, Thunar instead of Nautilus, a light-weight browser instead of Firefox, etc. You will notice the benefit there. Good luck!

---

