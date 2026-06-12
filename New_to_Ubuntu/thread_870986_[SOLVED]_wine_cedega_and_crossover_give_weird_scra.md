---
title: "[SOLVED] wine cedega and crossover give weird scrambled screen"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Baarhisveiki on 2008-07-26
I' ve been working with wine, crossover and cedega (eve-online client) for over 8 months now. I use some winapps i cannot miss.
It all worked very well. Graphic apps and games (like eve for instance)have been running as they should.
This morning when i started eve i got this weird scrambled screen (like my screen is split 4 or 5 times verticaly and several coloured blocks appear at the same time horizontaly. I really dont know why. Not ubuntu regular i mean, linux works with no probs its only when i wanted to play eve (cedegaclient). It took me hours to google for other peeps with the same faillure. But only now i realize its not eve. I tried several apps running normaly under wine or with crossover and all of them that used to run ok do run (i can see em through the "blocks") but off course i cannot access them due to the scrambled screen. I can guess where to put my cursor an click the buttons of the app but hey thats no charm is it. So i guess it might have something to do with the config of wine (assuming cedega and crossover use this) but even that screen is scrambled.
Maybe an update (i take in as soon as my update manager show they are available)that is causing problems now. I always take em in coz i guess its always for the best... .
Maybe an app i unistalled some days ago and which took something with it causing problems for wine now....i honestly dont know.... .
Please, can someone help me out here....

Greetz,

Baar.

---

### Post by ProbablyX on 2008-07-26
Do you have any compositing effects on, like Compiz or KDE 4 window effects? If so can you try and turn them off and see if the problem's still there?

---

### Post by Baarhisveiki on 2008-07-26
I had compiz (not that i was using it) but that was one of the first things i thought of and uninstalled it. rebooted but no help there.

---

### Post by ProbablyX on 2008-07-26
Just to make sure your graphics drivers are OK and haven't been fiddled with, can you print the output of the command
```

glxinfo | grep vendor

```

---

### Post by Baarhisveiki on 2008-07-26
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: ATI Technologies Inc.

---

### Post by ProbablyX on 2008-07-26
First lets see what your drivers think of 3D:
```

glxinfo | grep direct

```
What did you get?

Then how ATI's driver "manager" is doing:
```

fglrinfo

```

---

### Post by Baarhisveiki on 2008-07-26
glxinfo | grep direct
direct rendering: Yes


and

bash: fglrinfo: opdracht niet gevonden

meaning no such command??

---

### Post by Baarhisveiki on 2008-07-26
i guess you meant (quick google :-))

 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.7659 Release

---

### Post by ProbablyX on 2008-07-26
It seems to be a problem with AMD/ATI and their new video card driver.

The matter is discussed at:
[http://www.phoronix.com/forums/showthread.php?t=10940](http://www.phoronix.com/forums/showthread.php?t=10940)

I only use nVidia hardware, maybe someone with an AMD/ATI card can take over as I can't reproduce the error. 
Sorry for not being able to help more

---

### Post by Baarhisveiki on 2008-07-26
You did help me. At least i got a new lead. :-)
Thanks for your time. I will close this thread as soon as i solved it (hopefully very soon)

Thanks!

---

### Post by Baarhisveiki on 2008-07-26
While looking at the above mentioned thread i found another link to the ati bug report forum as it is VERY likely an ATI driver prob.

[http://ati.cchtml.com/show_bug.cgi?id=1173]("http://ati.cchtml.com/show_bug.cgi?id=1173")

apparantly the author reports the problem resolved (for him) but i dont understand how he did it (re-emerge xorg? And adding x to the packages.keywords?)

It sounds like English but its actually chinese to me.

Anyone? 

And yes its ATI again. You cannot believe how much reconfiguring and updating  and googling i had to do with these cards.

---

### Post by ProbablyX on 2008-07-26
> **Baarhisveiki said:**
> 
apparantly the author reports the problem resolved (for him) but i dont understand how he did it (re-emerge xorg? And adding x to the packages.keywords?)

emerge is the system that handles packages, like synaptic or aptitude for the Gentoo distribution.

I would see that there are three ways to go:
1) Wait for an updated driver (shouldn't take too long)
2) Think that it's not a driver error and go on researching
3) Install envy drivers.

I would not recommend 3 for a newcommer, but if all else fails.

Envy is a software package that downloads and installs drivers directly from ATI. Its included in ubuntu, works nice, but can be tricky to setup.
Envy allows you to choose which driver version to use, so if the latest is buggy you can always go back to an older version.

As this thread is getting "flooded" and if you really need your graphics and cant wait. Go to the hardware forum, say that your ATI drivers are playing tricks on you, tell them that you are new, and that you want to try the envy drivers.
I would help, but I think it'd be better if someone who uses ATI hardware patch in there.

Good luck

---

### Post by Baarhisveiki on 2008-08-13
Me again. The 20the july (or so) a new ati driver was obtained at

[http:///ati.amd.com/support/driver.html]("http:///ati.amd.com/support/driver.html")

I installed it (its a .run command)
you will have to log in as root first install the run file and voila...all problems with wine and the buggy ati driver was solved!

I will close this thread now. Thanks for all the help

---

### Post by paradroid90 on 2009-06-08
Hi,

Just want to add to the thread in realtion to scrambled screens in certain games even after compiz switched off!!!

This is my machine spec.

AMD Athlon x2 3800
2gb DDR2 Ram
X850XT Graphics Card
Ubuntu 8.10

The games effected are Eve On Line (Wine Install) and Savage 2

Any Ideas???????

---

