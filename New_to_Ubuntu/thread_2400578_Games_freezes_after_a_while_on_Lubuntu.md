---
title: "Games freezes after a while on Lubuntu"
date: 2018-09-07
forum: New to Ubuntu
---

### Post by bdexsas on 2018-09-07
I recently installed Lubuntu, and decided to install a few games, but they freeze after 2-5 minutes of playing. But after exiting the console by pressing CTRL+ALT+Fn and then returning back pressing CTRL+ALT+F7 the game starts working again - and later it freezes again.

I searched a bunch of forums without finding the reason.

Maybe somebody knows how to fix it?

My system specs are:

    Processor: Intel Pentium E2160 1.8 GHz
    RAM: 2GB
    GPU: Intel GMA 3000 256MB

---

### Post by Autodave on 2018-09-07
What version of Lubuntu did you install?  What game(s) does it lock up on?

---

### Post by bdexsas on 2018-09-07
> **Autodave said:**
> What version of Lubuntu did you install?  What game(s) does it lock up on?

18.04. CS 1.6 and Crypt of the Necrodancer.

---

### Post by Autodave on 2018-09-07
Laptop or desktop?  Kinda sounds like you may have an overheating problem: that is a rather slow machine to be trying to play any sort of game on.  Checking the minimum requirements (online) shows that your machine is right at the minimum. 

If this is a laptop, have you checked to make sure that there is no dust blocking the cooling vents? Tried blowing compressed air through it?

If desktop, are the cooling fans all functioning and clean?  You could try running the machine without the side cover on it to allow a little extra cooling.

---

### Post by bdexsas on 2018-09-07
> **Autodave said:**
> Laptop or desktop?  Kinda sounds like you may have an overheating problem: that is a rather slow machine to be trying to play any sort of game on.  Checking the minimum requirements (online) shows that your machine is right at the minimum. 

If this is a laptop, have you checked to make sure that there is no dust blocking the cooling vents? Tried blowing compressed air through it?

If desktop, are the cooling fans all functioning and clean?  You could try running the machine without the side cover on it to allow a little extra cooling.

Desktop. I'm not sure that this is overheating, because the games worked fine in recovery mode, but lagged.

---

### Post by Autodave on 2018-09-07
The fact that it plays for several minutes seems to indicate that this is not a software problem. 

If it were my machine, I would pull the cover and make sure it is clean inside. Then I would leave the cover off and try it. If a little better, I would then try a small external fan blowing some cooler air into the box.

Perhaps someone else will join the fray here and offer another answer, but I have been building/repairing PCs for a good while and I am just offering my views and what I would try to either prove that it is a heat problem or prove that it is not. What I have suggested won't cost anything but a couple minutes of time.

As an example, I am running an 8 core over-clocked to 4.0. Replacing the standard cooling fan with a higher performance fan allows me to run games at a MUCH higher resolution and frames per second than I used to be able to do.  You are stressing your machine due to the low power of it.  Give it some love and cool air and see if it helps.

---

### Post by bdexsas on 2018-09-07
> **Autodave said:**
> The fact that it plays for several minutes seems to indicate that this is not a software problem. 

If it were my machine, I would pull the cover and make sure it is clean inside. Then I would leave the cover off and try it. If a little better, I would then try a small external fan blowing some cooler air into the box.

Perhaps someone else will join the fray here and offer another answer, but I have been building/repairing PCs for a good while and I am just offering my views and what I would try to either prove that it is a heat problem or prove that it is not. What I have suggested won't cost anything but a couple minutes of time.

As an example, I am running an 8 core over-clocked to 4.0. Replacing the standard cooling fan with a higher performance fan allows me to run games at a MUCH higher resolution and frames per second than I used to be able to do.  You are stressing your machine due to the low power of it.  Give it some love and cool air and see if it helps.
Ok, I'll try, thanks

---

### Post by DuckHook on 2018-09-07
I am unfamiliar with your game, but depending on its resource draw, your system may simply be underpowered for it. Your system specs are awfully light, especially for modern games. If your system is forced to go to swap or the game overruns what can be allocated for cache, your game will either slow to a crawl or freeze outright. All of your components are very underpowered by today's standards. I would hazard a guess that this is the root cause. If so, then there isn't much you can do about it except upgrade your components.

---

### Post by Autodave on 2018-09-07
Online called for a 2.0 with 2G RAM as minimum: he is right there.

---

### Post by bdexsas on 2018-09-07
> **DuckHook said:**
> I am unfamiliar with your game, but depending on its resource draw, your system may simply be underpowered for it. Your system specs are awfully light, especially for modern games. If your system is forced to go to swap or the game overruns what can be allocated for cache, your game will either slow to a crawl or freeze outright. All of your components are very underpowered by today's standards. I would hazard a guess that this is the root cause. If so, then there isn't much you can do about it except upgrade your components.
I played these games on Windows and I had no problems with them, and I thought that everything should be much better on Lubuntu. I would gladly upgrade my PC, but at the moment I can not do it.

---

### Post by Autodave on 2018-09-07
Are you playing it through WINE?  If so, that is why you are stressing the machine.  WINE is kinda like running an operating system inside of another operating system: lots of resources are being used before you even start the game.

---

### Post by Autodave on 2018-09-07
Just did a quick search and I see that the game could be had in Linux format. If you had that, I am sure that it would play well. However, running in WINE will more than likely make it slow and use up every available resource you have.

I understand about not being able to upgrade, but try what I said and make sure that you have sufficient cooling to the inards of the machine.

---

### Post by DuckHook on 2018-09-07
> **bdexsas said:**
> I played these games on Windows and I had no problems with them, and I thought that everything should be much better on Lubuntu. I would gladly upgrade my PC, but at the moment I can not do it.Games developers make sure to purposefully tweak their games for Windows. Most don't take the time to do so with Linux. Usually, Windows games are just recompiled to work with Linux system calls, and are not optimized for the ways that Linux is fundamentally different from Windows. Moreover, if you are comparing performance to an older, less resource-intensive OS, you will find that OS overhead invariably increases with new releases as well. Last but not least, it is simply a fact of life that developers don't pay as much attention to building performance-driven Linux drivers for GPUs as they do for their Windows counterparts. Linux has always emphasized stability and reliability over performance, and I doubt that this will change anytime soon.

The usual advice given in these forums is: Windows is best for gaming. So, if you are an avid gamer, you may wish to keep a Windows partition around to dual boot into Windows for those occasions when you game.

---

