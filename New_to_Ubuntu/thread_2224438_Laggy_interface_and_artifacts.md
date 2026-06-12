---
title: "Laggy interface and artifacts"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by r-man2 on 2014-05-16
[FONT=verdana]Hi! I have just installed Ubuntu on an old PC (spec[SIZE=2]s below) and the GUI is very laggy. For example, when i'm moving a window it moves with about 1 frame per second. The only unaffected object is the cursor which moves normally. Also the screen is shaking and there [/SIZE]are artifacts (horizontal lines) on it. My guess would be that this happens because I haven't installed the graphics driver. But, I am unable to find the right one and nothing shows up in [/FONT][SIZE=2][FONT=verdana]Additional Drivers[/FONT][/SIZE][FONT=verdana]. Please help!

Old PC specs:
[COLOR=#333333]CPU - AMD Sempron 2200+ 1.5 GHz single core[/COLOR]
[COLOR=#333333]RAM - 1 GB DDR[/COLOR]
[COLOR=#333333]GPU - NVIDIA GeForce4 MX Integrated GPU
Motherboard - [/COLOR][SIZE=2]PoX EP-8RGM3I 462(A) NVIDIA nForce2 IGP Micro ATX AMD

Yeah, quite old. I know![/SIZE][/FONT]

---

### Post by LastDino on 2014-05-16
Not related to the problem itself but I must ask, did you install Lubuntu or Ubuntu unity? If it is latter, I'm afraid solving drivers ''problem'' alone is not going to make world of difference.

---

### Post by Drowz0r on 2014-05-16
Yeah seems the spec just won't really reach Ubuntu. I would go with Lubuntu or maybe even Xubuntu.

Alternatively Bodhi is even lighter and still very graphical.

---

### Post by r-man2 on 2014-05-16
Ok. I'll try Lubuntu. Wish me luck!

---

### Post by r-man2 on 2014-05-16
I have installed Lubuntu and it's running smooth (using that PC right now). Sadly, the screen is still shaking and there are artifacts on it. Also, I can't set the resolution above 1024x768. How can I fix these issues?

---

### Post by Drowz0r on 2014-05-16
I had that problem when installing on a super old laptop from 2001 this one time but never saw it since. I would only guess at it being driver related or a corrupt copy installed. I suspect the former but I'm far from an Ubuntu expert.

---

### Post by LastDino on 2014-05-16
I would suggest you to make a new thread with that issue. I don't have exact solution for it but I'm guessing, this sounds like gpu issue. There are countless threads adressing that on here, just check one of them to know how to change those gpu drivers to non-free.

---

### Post by Rob Sayer on 2014-05-16
I think it's probable a video driver issue as well.  

If you're really new to linux this is probably a good place to tell you that drivers in linux do *not* work the same way as they do in windoze.  You can't just download a driver to a folder.

First you need to know exactly which card you have.  Try this ....

[http://askubuntu.com/questions/348308/find-graphics-card-driver-details](http://askubuntu.com/questions/348308/find-graphics-card-driver-details)

... and then search for ubuntu + whatever it is.

Don't assume that the solution for a previous ubuntu version will work in your version either.

---

### Post by Drowz0r on 2014-05-16
I believe Lubuntu has a way to search and install the right driver for you If the OS is marginally usable. In Ubuntu it's called Additional Drivers in the Dash. I suspect it's something similar in Lubuntu.

---

### Post by r-man2 on 2014-05-16
So, I've managed to get rid of the artifacts and the shaking screen by disabling the Nouveau driver. Now I only need to find the right driver and install it (easier said than done).

---

### Post by Drowz0r on 2014-05-16
I found this :

[http://ubuntuforums.org/showthread.php?t=2076691](http://ubuntuforums.org/showthread.php?t=2076691)

It's from like 2012 but I doubt the terminal commands have changed.

2nd post for your NVIDIA drivers.

---

### Post by monkeybrain20122 on 2014-05-16
That is a very old card. I think you need the nvidia-96 driver which is no longer supported. If you can't find anything in Additional Drivers try this ppa

[https://launchpad.net/~mati75/+archive/nvidia-96](https://launchpad.net/~mati75/+archive/nvidia-96)

---

### Post by monkeybrain20122 on 2014-05-16
> **r-man2 said:**
> So, I've managed to get rid of the artifacts and the shaking screen by disabling the Nouveau driver. Now I only need to find the right driver and install it (easier said than done).

Doesn't make a lot of sense. if you disable nouveau and you don't even know which Nvidia driver to install what is it running on?:confused: 

> Drowz0r 	 	 		 			 				

 			 			I found this :

[http://ubuntuforums.org/showthread.php?t=2076691](http://ubuntuforums.org/showthread.php?t=2076691)

It's from like 2012 but I doubt the terminal commands have changed.

I doubt that nvidia-current would work on a card that old.

---

### Post by mörgæs on 2014-05-17
These old Nvidia cards are often best served with something 12.04-based (or even better, replaced).

Please see the link in my signature for more details.

---

