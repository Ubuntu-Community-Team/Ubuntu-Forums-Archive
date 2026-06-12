---
title: "Raspberry pi imaging"
date: 2017-09-08
forum: New to Ubuntu
---

### Post by 1jarwolf on 2017-09-08
Hello everyone. I am currently using Ubuntu MATE however, I am wanting to use the official Ubuntu OS. I keep seeing an Ubuntu server classic 16.04. I don't want a linux server OS though.

---

### Post by Bucky Ball on 2017-09-08
Any reason you don't just install Ubuntu 16.04 LTS? Are you saying there isn't a spin of it for the RPi (ARM based)? Guess if you don't want a server release, don't install one. On a dinky beast like the RPi I'd go for something minimal, like Xubuntu (preferably Xubuntu-core) or Ubuntu-core. 

I would also suggest the minimal install and build that up to what you want, but not sure there is one for the RPi. You are somewhat restricted in what's available (at least last time I looked; had a few RPi).

Where are you looking for RPi Ubuntus?

---

### Post by 1jarwolf on 2017-09-08
is it actually like made for a server like what businesses uses to keep their information on, such as a Windows server? what is the difference between Ubuntu core and the official Ubuntu? indeed, I am trying to look for Ubuntu's fo my RPi 3.

---

### Post by ian-weisser on 2017-09-08
> **1jarwolf said:**
> is it actually like made for a server like what businesses uses to keep their information on, such as a Windows server? what is the difference between Ubuntu core and the official Ubuntu? indeed, I am trying to look for Ubuntu's fo my RPi 3.

A lot to unpack there.

Yes, Ubuntu Server is for servers. Do you want to run a server?

Ubuntu Core is for advanced users who want to build embedded systems and have lots of skills. Not for beginners...unless the beginner loves frustration.

---

### Post by 1jarwolf on 2017-09-08
lol. well, I dont want an OS for running a server though I also dont want frustration. i do want straight up Ubuntu OS for my raspberry pi.

---

### Post by ian-weisser on 2017-09-09
That brings us back to Bucky Ball's questions in Post #2.
I do not see how we can usefully help you further until you consider those.

---

### Post by sudodus on 2017-09-09
I would recommend one of the distros at

[https://www.raspberrypi.org/downloads/](https://www.raspberrypi.org/downloads/)

and I think that Ubuntu MATE, that you are already using, is the best Ubuntu choice (better than Snappy Ubuntu Core).

---

### Post by Bucky Ball on 2017-09-09
Guess [this would be what you're after]("https://wiki.ubuntu.com/ARM/RaspberryPi"), then. Or is that where you got the server image? If you look down the page under 'Desktop' it explains that it is a small, server image you are downloading and you need to install a desktop environment. It explains how (using three light DEs as examples and not Unity, the current default Ubuntu desktop). 

Maybe this is as close as it gets for Ubuntu on the RPi 3. The ARM server image with a desktop environment.

---

### Post by 1jarwolf on 2017-09-10
Hmm. So, I would technically install the Ubuntu server, and then install perhaps an Ubuntu Unity Desktop Enviorment to make it look like Ubuntu? That is really smart, I will for sure look into that. If I can do that, perhaps in the future, if I ever need a server for something of that nature, it will be right there. Thanks!

---

### Post by sudodus on 2017-09-10
This might work if the Ubuntu Server system for Raspberry Pi is 'complete' with all the program packages for the Ubuntu Unity desktop environment in repositories for this hardware architecture. It is worth trying.

**Edit:** As pointed out by @Bucky Ball, the graphics chip in the Raspberry Pi is probably unable to render the Unity desktop environment, but there are Ubuntu community flavours alongside Ubuntu MATE that might be compiled for the architecture of Raspberry Pi: Lubuntu with an ultra-light desktop environment and Xubuntu with a medium light desktop environment.

---

### Post by Bucky Ball on 2017-09-10
As mentioned on that website; Unity requires 3D and don't think your RPi will do that. More research required there.

---

### Post by rsavage on 2017-09-12
The raspberry pi 3 can do 3D.  The problem is you need a new version of mesa to make it useable as a gl compositor.  Unless you run 17.10, the required version is currently not in the ubuntu archive.  So a bit of compiling is necessary at the moment.  Compiz runs impressively well on the pi 3.

---

