---
title: "Xoom Kernel Development"
date: 2012-02-20
forum: Packaging and Compiling Programs
---

### Post by Igneo676 on 2012-02-20
Wasnt quite sure where to put this since I am doing this all on a ubuntu install on my main computer so I figured since the actual work is involving ubuntu I would put this here.

I am following the guide here ( [http://www.cactuar.net/2011/06/19/ho...motorola-xoom/](http://www.cactuar.net/2011/06/19/ho...motorola-xoom/) ) to install debian natively to my xoom using my Ubuntu install, but as the author notes: sound, bluetooth and hardware acceleration do not work. What he did not have access to at the time were the binary blobs from Nvidia from here [http://developer.nvidia.com/linux-tegra](http://developer.nvidia.com/linux-tegra) for the ventana platform.

He has left behind a github with the kernel source here: [https://github.com/LIV2/LIV2-Xoom-GNU](https://github.com/LIV2/LIV2-Xoom-GNU) This is just a few modifications to the kernel source I could do pretty easily myself but I have the following questions: How do I merge the Nvidia drivers with my kernel? Can I use github to help do this for me? Even better, can I use some newer kernel source from here [https://github.com/solarnz/Tiamat-Xoom](https://github.com/solarnz/Tiamat-Xoom) and add those same nvidia drivers?

The reason those kernels dont work out of the box is they are meant for android and not a proper linux install, so that is why the linux4tegra packages are needed.

Notes:

I have also tried, in my own noobish way, to simply combine the source by copying whole folders from the nvidia kernel they had over to the modified kernel by the author. Compiling worked, however, when I run mkinitramfs within the debian chroot it claims that the /lib/modules/2.6.35-30... is missing despite the fact that the kernels are both 2.6.36, so it is obvious to me that my hackish way of pulling them together doesnt work.

Also i might mention Nvidia has a github here: [http://nv-tegra.nvidia.com/gitweb/?p....git;a=summary](http://nv-tegra.nvidia.com/gitweb/?p....git;a=summary) but it is rather confusing since I cant find what is for the ventana platform and what isnt.

many thanks ahead of time for help!

---

### Post by smp4488 on 2012-02-21
I was looking to do this same EXACT thing. I think we are in the same boat my friend. I have also built an ubuntu kernel using the guides you posted links to. As you mentioned bluetooth and graphics acceleration do not work. I also could NOT get wifi to work. I read somewhere that the wifi and bluetooth are built into the same chip. I looked into building a kernel module with no luck. I have Ubuntu 11 running with a little bit of touchscreen working. I am mainly fooling around using a USB keyboard. I would love to move the sd card to an internal partition and see how much the speed increases. I will be watching this thread closely. Maby later we can hit each other up on IRC?

---

### Post by anontheanon on 2012-04-13
Life is easier when you relax a little about 'binary blobs'.

Its amazing how much personal freedom people are willing to restrict in the pursuit of "software freedom" :/

I dont always see eye to eye with Ubuntu, but I must say that I agree with their approach to free software over that of the FSF....Use the free software over the proprietary if it exists and works for your needs. Use the proprietary if you must and you trust it, but give the end user the final say in what they are willing to risk/agree-to. 

I would love to get Ubuntu on my Xoom. Unity may not be the best DE for a workstation, but I think its a great cellphone/tablet interface ;)

Isnt Xandros or some others developing some 'lite' desktop just for touch screens and virtual appliances?

---

