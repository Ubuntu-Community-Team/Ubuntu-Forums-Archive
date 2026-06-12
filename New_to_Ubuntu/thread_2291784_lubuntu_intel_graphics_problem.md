---
title: "lubuntu intel graphics problem"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by ryan178 on 2015-08-22
**lubuntu 15.04**


new comer from windows 7 

When i set my external monitor to 1920x1080 through my laptop via VGA its goes crazy comes up lines and flickers like mad it does it with windows until i install drivers 

having to use 1280x960

usually with windows i have to install intel drive utility with windows 7 and it fixes it any idea how i can resolve it on linux 

ANY IDEAS PLEASE ?

---

### Post by Geoffrey_Arndt on 2015-08-23
What are the PC specs?  (espcially gpu data)
May need to

>  install proprietary drivers or
>  may need to use hdmi or display port interface for those settings (if only have vga port, maybe a vga-hdmi adapter plug?

---

### Post by sol8712 on 2015-08-23
Well there's good news and bad news. 

Good news is Intel has a similar driver utility for ubuntu(yay!) 

Bad news is, they've only updated it to work up to Ubuntu 14.04(dont quote me on that number) 

Anyone know if we can "trick"  Ubuntu into thinking it's running 14.04? I'll be the guiny pig if we can, I'm comfortable reverting the driver changes through ssh if it goes south. 

I'm running lubuntu 15.04 and looking into installing the Intel video drivers as well(for game development with unity3d though), however for your issue I can confirm hdmi work very nice with the built-in drivers

---

### Post by Bucky Ball on 2015-08-24
Welcome. I suggest you run these commands in a terminal prior to doing anything further:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Reboot, then check 'Additional Drivers'. Also give the output of:

```
sudo lshw -C video
```

... which will give the details of your graphics card as requested previously. Please provide a link to the Intel driver. It generally isn't required as the appropriate driver is already in the kernel (and the above command will tell us what driver you currently have installed).

---

### Post by monkeybrain20122 on 2015-08-24
Intel's driver is basically the same as the stock driver in 15.04 according to Intel, that's why they don't provide an installer for 15.04. But I think there are minor version differences.
If you want to try beta driver check [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) Sometimes it may fix your problem especially if you have a very new card. But have ppa-purge ready and make sure you know how to use it in case things get worse. If it is working then disable the ppa because you don't want it to update everyday until things break.


Edited: link to Intel driver [https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0](https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.1.0)
But it didn't work since 14.04.2 [https://01.org/linuxgraphics/forum/graphics-installer-discussions/do-not-use-ubuntu-14.04](https://01.org/linuxgraphics/forum/graphics-installer-discussions/do-not-use-ubuntu-14.04)

---

