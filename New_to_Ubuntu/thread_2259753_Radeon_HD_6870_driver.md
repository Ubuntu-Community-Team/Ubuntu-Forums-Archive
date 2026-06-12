---
title: "Radeon HD 6870 driver"
date: 2015-01-06
forum: New to Ubuntu
---

### Post by Bubbelgum on 2015-01-06
Hi, 

Running Ubuntu 14.04 whit Radeon HD 6870 and was woundering about drivers and looked around abit, but when new to Ubuntu it&#347; a bit hard to understand thins.

Ubunto says Graffik Gallium 0.4 on AMD BARTS, and i asume that this is not optimal driver, downloaded driver from ati and choos to open whit Program central for Ubuntu. and it says that "dependence is not satisfied fglrx-core"

so i wounder how do i solve this problem?

---

### Post by grahammechanical on 2015-01-06
There are two types of video drivers in Ubuntu - open source and proprietary. The open source video driver is the default for Ubuntu unless we tick "Install third party software" when we install Ubuntu. Then we get the proprietary video driver.

Gallium is the open source video driver. If we are using an Nvidia card Gallium will also be called Nouveau. If we are using an AMD/ATI video card then Gallium will also be called Radeon. The open source video driver is by no means poor quality. Although some people prefer the proprietary video driver.

In Ubuntu we go to System Settings>Software and Updates>Additional Drivers tab and after allowing the utility time to find the drivers (we need an internet connection) we can change video drivers. We will be offered 5 video drivers. There will be the open source driver and four versions of the proprietary driver. This is the better way for new Ubuntu users to try out different video drivers. I have been using Ubuntu for more than 7 years and I have never needed to use a different way to install a video driver.

Video drivers that we install from the makers web site might be newer but they will not have been tested. This is another reason why installing video drivers through the Additional Drivers utility is better than the way you are choosing.

What added benefits do you think you will get by installing the driver from the makers web site?

Regards.

---

### Post by mastablasta on 2015-01-07
AMD driver is still some 20-30% better and has out of the box configuration for power management (e.g. on laptops it won't spin the fans at full). while the power management can also be achieved on opensource drivers it is not so trivial to setup. 

@bubblegum -  follow the advice given and you should be using the proper AMD drivers in no time.

---

### Post by Bubbelgum on 2015-01-07
Thx alot, it was easy when i did know where to look :p

---

### Post by sandyd on 2015-01-07
Hi, if you have found a working solution, please mark this thread as solved by going to Thread Tools -> Mark thread as solved.

Thanks!

---

### Post by monkeybrain20122 on 2015-01-08
> **mastablasta said:**
> AMD driver is still some 20-30% better and has out of the box configuration for power management (e.g. on laptops it won't spin the fans at full). while the power management can also be achieved on opensource drivers it is not so trivial to setup. 

@bubblegum -  follow the advice given and you should be using the proper AMD drivers in no time.

The power management thing is now automatic with newer kernels, I think stock 3.13 from Trusty should be new enough. Unless maybe you are a gamer and try to squeeze all the fsp out of the card, I think the latest open source driver is on par with the proprietary one for most AMD cards and most purposes but integrate better with the system, smoother overall and easier to maintain (in my experience with amd cards fglrx may have some marginal performance gain but I couldn't see it with my use case,--videos, occasional non hardcore games,-- but it always has some annoying glitches which are quite noticeable such as compiz artefacts or flash issues. Updates can also be problematic,--even though it shouldn't be)

With Nvidia cards I would still recommend the proprietary driver but with AMD, except for bleeding edge hardware IMO just need to update your open driver.Instead of stock Ubuntu driver, I always get the latest open AMD (or Intel for that matter) driver from [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by mastablasta on 2015-01-09
I will have to try that PPA. I have some games (nothing fancy, old games based on Q3 engine or jdoom) crashing. funny how supertux cart and similar are doing well. it's either due to CPU overheating (hmmm..) or bad drivers. so I will do a measurements and of the CPU temp first. if it's not the CPU then it is the GPU driver. and maybe this PPA could save the day.

I mentioned power management as last time I had fan spinning wildly on laptop (on 14.04) and battery kind of didn't last as long a sit used to. when I took some time to investigate a bit I noticed that opensoruce drivers were running. switched to AMD drivers and all went back to normal. quiet fan, battery is life long again (though still not as long as on win 7)

---

### Post by monkeybrain20122 on 2015-01-09
About power management. Maybe updating your kernel from mainline would help? I remember I had to edit some config file for it to work in 13.10 but not in 14.04, but then maybe that is because I am using kernel of much higher version than coming with stock Ubuntu ( on an unrelated note I am running kernel 3.19 rc3 on my intel machine. It fixes a very annoying problem of vlc crashing when vaapi is enabled)

With regard to the obaif ppa, it is providing the latest mesa 10.5 from master, while it works great mostly once in a while you may get a bad update (it updates twice a day)I would make a clone of my / partition before I go ahead and disable the ppa once everything is working. **Edited:** instead of cloning you can use ppa-purge to downgrade the packages if things go wrong, but then in that case you would downgrade all the way to square one rather than say, the last good update.

---

### Post by mastablasta on 2015-02-03
> **monkeybrain20122 said:**
> About power management. Maybe updating your kernel from mainline would help? I remember I had to edit some config file for it to work in 13.10 but not in 14.04, but then maybe that is because I am using kernel of much higher version than coming with stock Ubuntu ( on an unrelated note I am running kernel 3.19 rc3 on my intel machine. It fixes a very annoying problem of vlc crashing when vaapi is enabled)

With regard to the obaif ppa, it is providing the latest mesa 10.5 from master, while it works great mostly once in a while you may get a bad update (it updates twice a day)I would make a clone of my / partition before I go ahead and disable the ppa once everything is working. **Edited:** instead of cloning you can use ppa-purge to downgrade the packages if things go wrong, but then in that case you would downgrade all the way to square one rather than say, the last good update.

so the PPA is used for driver upgrade and then disabled? but what if something else breaks as a result?

is there any PPA with newer driver but a bit more stable? 
Would upgrading kernel help? e.g. using hardware enablement stack?

I am getting more and more of crashes with GPU "intensive" games. I still need to try but it doesn't seem that wine ones are crashing only the ones running in opengl. also the overheating - I added a fan. though I couldn't turn it properly (it's pushing air in) it seems to have cooled the CPU a bit. the CPU works at about 50-60 C when under load. quite high, but well within margin (80C = warning hot, 100C shutdown)

---

### Post by monkeybrain20122 on 2015-02-03
> **mastablasta said:**
> so the PPA is used for driver upgrade and then disabled? but what if something else breaks as a result?

is there any PPA with newer driver but a bit more stable? 

Only disable it after you reach a sweet spot. I clone my /root partiton (~15 g) with fsarchiver regularly just in case an upgrade breaks something. For more 'stable' ppa maybe xorg-edgers? But I would say the same approach applies, there is no perfectly stable way to use beta driver I am afraid. On the other hand there are some even more bleeding edge ppas built on oibaf (gallium 9 something) for gaming, but never tried those. (Edited: see discussions on link below)

> Would upgrading kernel help? e.g. using hardware enablement stack?


A lot of work has gone into supporting the raedon driver since kernel 3.18, but I think even the hes does not provide that. I am using 3.19 rc6 since it fixes a problem of vlc crashing under vaapi (intel gpu). You can get new kernels from mainline.  Not sure about the graphic driver in hes though. I have a test partition running utopic and it is very buggy IMO. Also using the hes makes it incompatible with oibaf or xorg-edgers, it gives you only less old driver and won't be supported for the whole duration of the lts, IMO too many drawbacks for too little gain, I personally don't use that.

> I am getting more and more of crashes with GPU "intensive" games. I still need to try but it doesn't seem that wine ones are crashing only the ones running in opengl. also the overheating - I added a fan. though I couldn't turn it properly (it's pushing air in) it seems to have cooled the CPU a bit. the CPU works at about 50-60 C when under load. quite high, but well within margin (80C = warning hot, 100C shutdown)


I am sorry, can't really comment on that since I don't play GPU intensive games. Perhaps you should take a look at the support section for the oibaf ppa where gamers hangout. [http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers) It is also good to check this out regularly to see bug reports if you use oibaf.

---

### Post by mastablasta on 2015-02-04
looks like the fan issue on GPU. 

thanks for the rest of the info.

---

### Post by monkeybrain20122 on 2015-02-10
The ppa has switched to mesa 10.6 since Saturday and breaks some OpenGL functions. Better wait for a week or so if you think of trying it.

---

### Post by mastablasta on 2015-02-11
nah I am good it seems. will test more heavy games or get a new card (or replace the whole PC).

---

### Post by SayakBiswas on 2015-02-15
I do not recommend installing the drivers from amd's website, its not impossible but its pretty complicated.

If you still want the latest drivers, try the xorg-edgers ppa, else i would suggest you go to "additional drivers" and activate fglrx-updates. It will give you the latest drivers that works with your current kernel. Its stable and you can update ubuntu without any problems. But dont try to install custom kernels once you use "additional drivers". Redeon HD 6870 has good performance on ubuntu with proprietary drivers......so dont give up just yet.

---

