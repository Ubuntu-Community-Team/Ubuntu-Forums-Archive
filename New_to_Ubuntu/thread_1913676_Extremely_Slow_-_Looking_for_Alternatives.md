---
title: "Extremely Slow - Looking for Alternatives?"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by RadhikaM on 2012-01-22
Hey everyone. I've installed Ubuntu 11.10 on my computer, just a couple of hours ago, but found that it runs extremely slow. I haven't really tweaked around or made it any higher performance than it was out of the box.
I do have an old-ish computer (it was $100 and refurbished; came with Windows XP), so I suppose that is contributing. So, I was looking for a kind of alternative? I want it to be either GNOME or Unity interface, because I don't know how to function any of the other ones, and it has to make my computer run faster, but still be able to play media in HD. 

Are there any alternatives? Thanks.

EDIT: Here are my system specs - I think:
(you have to download the html file; there is a view option without download)
[http://ge.tt/8AAxQdC]("http://ge.tt/8AAxQdC")

---

### Post by dFlyer on 2012-01-23
Without more specs about your system, ram, processor, I would recommend Ubuntu 10.04 LTS.

---

### Post by RadhikaM on 2012-01-23
EDIT: uploaded my system specs. I apologize.

---

### Post by holycow131415 on 2012-01-23
id suggest installing xfce desktop environment or lxde environment from software center. xfce sorta looks like gnome 2, and lxde looks like windows xp.

---

### Post by 3rdalbum on 2012-01-23
You've got one gigabyte of RAM and are currently using nearly 600 MiB. That amount of used RAM is pretty high. Have you checked to see what is using all that memory? Chances are, if there's a single program using a lot of RAM, that's probably causing the slowdown.

I wouldn't recommend using an older version of Ubuntu. If it's just that you're running a lot of programs, you could consider installing another gigabyte of RAM or using a lighter desktop environment such as LXDE or XFCE. You can install them on top of Ubuntu.

---

### Post by Rodney9 on 2012-01-23
Try [[COLOR="Blue"]Lubuntu[/COLOR]]("http://lubuntu.net/")


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Jake Sweeney on 2012-01-23
If you computer is running really slow, I would recommend:
 
Upgrading your RAM
 
Switching to the Ubuntu 2D desktop enviroment
 
Or installing a lightweight desktop enviroment such as Lubuntu or Xubuntu ;)

---

### Post by Grenage on 2012-01-23
It's not a particularly fast system, but I'd go with 3rdalbum and increase your total RAM.  Ram upgrades can provide one of the best 'bang for buck' performance improvements.

---

### Post by Nick_Kats on 2012-01-23
> **RadhikaM said:**
> Hey everyone. I've installed Ubuntu 11.10 on my computer, just a couple of hours ago, but found that it runs extremely slow. I haven't really tweaked around or made it any higher performance than it was out of the box.
I do have an old-ish computer (it was $100 and refurbished; came with Windows XP), so I suppose that is contributing. So, I was looking for a kind of alternative? I want it to be either GNOME or Unity interface, because I don't know how to function any of the other ones, and it has to make my computer run faster, but still be able to play media in HD. 

Are there any alternatives? Thanks.

EDIT: Here are my system specs - I think:
(you have to download the html file; there is a view option without download)
[http://ge.tt/8AAxQdC](http://ge.tt/8AAxQdC)


I can't really see your graphics card in those specs. If it isn't there, can you please post it. I believe that your cpu and ram are not the real problem here.

---

### Post by RadhikaM on 2012-01-23
> **Nick_Kats said:**
> I can't really see your graphics card in those specs. If it isn't there, can you please post it. I believe that your cpu and ram are not the real problem here.

My graphics card has been unrecognizable throughout the process of having it. I believe it is extremely old and definitely can't stand 3D animations and games.

---

### Post by varunendra on 2012-01-24
> **RadhikaM said:**
> I want it to be either **GNOME **or Unity interface, because I don't know how to function any of the other ones, and it has to make my computer run faster, but still be able to play media in HD.
Have you tried [Mint]("http://linuxmint.com/")?

> **3rdalbum said:**
> You've got one gigabyte of RAM and are currently using nearly 600 MiB. That amount of used RAM is pretty high. I just want to mention that currently I'm running 11.10 with Unity-2D in VMware with 1GB RAM allocated. I've opened nothing but a terminal and firefox with 6 tabs of google, Ubuntu.com and wikipedia. The *free -m* command shows 626MB RAM usage!
As such, I don't think that much usage is abnormal (my VM's speed is fine, more responsive than host XP with 2GB remaining RAM).


> **Jake Sweeney said:**
> 
Switching to the Ubuntu 2D desktop enviroment
As I stated above, my 11.10 VM is already running Unity-2D and the RAM usage is similar as Radhika. But yes, it will consume less processing power.


*@Radhika,*
You can always use "System Monitor" to see CPU, RAM and network usage in GUI mode. If all of these seem normal yet the system is still slow (and I mean too slow, as default Ubuntu with Unity IS a heavy OS), I would recommend to use Xubuntu, just for testing. At least we can be sure whether or not it is a kernel-hardware compatibility issue, because Xubuntu (same version as Ubuntu you are using) will use the same kernel and drivers for the system, and is supposed to run smoothly on systems with very low specs.

---

