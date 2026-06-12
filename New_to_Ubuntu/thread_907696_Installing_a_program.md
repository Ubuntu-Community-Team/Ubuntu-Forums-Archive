---
title: "Installing a program"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-09-01
Hello all I am wanting to install this program [http://osu.ppy.sh/](http://osu.ppy.sh/)

And apparently it needs Microsoft .NET Framework. Which I also tried to install but once I try to load the game I get an R6034 error.  

Any help??

---

### Post by billgoldberg on 2008-09-01
Linux is not Windows.

It will not play Windows applications.

If you need games, look through the Ubuntu repos (add/remove or synaptic) or use this website:

[http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by nicedude on 2008-09-01
You would have to install .net 2.0 framework in wine ( the windows linux emulator ) and then try to install the game you want to use.

Here is a link to wine .net install I see it is listed as gold at wine hq which means it should work

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

As for the game you want to play it may or may not work in wine and even if it does you may have to google "wine nameofgame" and find someone who has done it as it may require some .dll files etc or special steps to work or it may just work. But all of this would be through Wine so install it first, its in the repositories.


Goodluck

---

### Post by Daveski on 2008-09-01
> **billgoldberg said:**
> Linux is not Windows.

It will not play Windows applications.


The site does not make it clear that this is Windows only - I guess they just assume that the whole world uses Windows. The give-away (zeththedarkmage) is that the system requirements include

DirectX9 and Microsoft .NET Framework

These are both Microsoft technologies for Windows machines.

---

### Post by billgoldberg on 2008-09-01
> **nicedude said:**
> You would have to install .net 2.0 framework in wine ( the windows linux emulator ) and then try to install the game you want to use.

Here is a link to wine .net install I see it is listed as gold at wine hq which means it should work

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

As for the game you want to play it may or may not work in wine and even if it does you may have to google "wine nameofgame" and find someone who has done it as it may require some .dll files etc or special steps to work or it may just work. But all of this would be through Wine so install it first, its in the repositories.


Goodluck

I never mention Wine to newcomers.

It confuses them too much, and leads to an unhappy experience.

**You can't play Windows apps?**

*No*.

**I've heard from someone you can?**

*Yes, well, you can do this <insert difficult instructions> and in 10% of the time it might run perfect.*

---

### Post by zeththedarkmage on 2008-09-01
I installed .net framework in wine, seeing that I am well aware of the fact that it is MICROSOFT .net framework.....

Also seeing that it was on Wines appdb I figured it would work seeing as how people say that it does. So I installed and was wondering what things I would have to do to get the program running, but thanks for stating the obvious.....

---

### Post by Daveski on 2008-09-01
> **zeththedarkmage said:**
> 
Also seeing that it was on Wines appdb I figured it would work seeing as how people say that it does. So I installed and was wondering what things I would have to do to get the program running, but thanks for stating the obvious.....

Ah, I see - being in the *Absolute Beginner Talk* section, it was assumed that you had misunderstood that this was a Windows app which is very common. Perhaps you could state next time that you wanted help with the wine configuration to run this. Sorry if we misunderstood - perhaps you could post in the *wine* section here.

---

### Post by barney385 on 2008-09-01
I just dual-boot. Windows for games. Hardy for everything else.

---

