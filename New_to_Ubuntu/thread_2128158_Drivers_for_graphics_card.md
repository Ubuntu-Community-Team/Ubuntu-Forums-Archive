---
title: "Drivers for graphics card"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by ombah on 2013-03-22
Hi!

I'm new in the Ubuntu/Linux world so I don't have much experience. I installed Ubuntu 12.10 on my MSI VX-600 notebook last week and I'm starting to feel comfortable. Anyways...

I think I need some proper drivers for my graphics card. I've done the:
> lspci | grep VGA
and this is what I got:
> VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 95c2

Now, I don't really know that to look for so any help is appreciated.

---

### Post by coffeecat on 2013-03-22
"Proper drivers"? Your system will be running with the default open source ATI driver which many people, myself included, find to be quite satisfactory. If you are a gamer you might want to consider the proprietary driver, but if not and you are getting a good graphics display, then I suggest you leave well alone. 

Are you sure you copied and pasted the output of "lspci | grep VGA" correctly. "95c2" doesn't yield anything helpful with a google search. My output is:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]

```

I would have thought you'd see something similar, only with different details at the end for your particular GPU. Try running that command again and making sure you gave us the complete output. It would help for people to advise on how well or otherwise the open source and proprietary drivers would work with your card.

---

### Post by ombah on 2013-03-22
Yeah, ofc I meant open source drivers. But it seems like most graphics card need a little driver check in Ubuntu.

I copy + pasted  your "lspci | grep VGA" and got the exact same thing:
> 01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 95c2
There are some problems that might be related to the graphics card. First of all, when I use my computer without the charger the light levels on the screen start to jump back and forth if there are 30 seconds of inactivity (30 seconds every time. I've checked with the clock). The second isn't really a problem but Minecraft is very laggy and therefore not so fun to play...

---

### Post by coffeecat on 2013-03-22
> **ombah said:**
> First of all, when I use my computer without the charger the light levels on the screen start to jump back and forth if there are 30 seconds of inactivity (30 seconds every time. I've checked with the clock). 

That's normal - a battery saving feature. If you don't like it, click on the cogwheel icon top right -> System Settings -> Brightness & Lock -> uncheck "dim screen to save power".

> **ombah said:**
> The second isn't really a problem but Minecraft is very laggy and therefore not so fun to play...

Then you probably may need the proprietary driver. From System Settings -> Software Sources -> Additional Drivers tab. See if it is offering you a proprietary driver. Although you may wish to wait to see if anyone else has a comment. That lspci output is odd and some people's experience of the proprietary driver is not good with some GPU's.

---

### Post by Rhannie on 2013-03-22
According the MSI website, your MSI VX-600 notebook has an ATi Mobility Radeon HD3410 graphics card. See: [http://www.msi.com/product/nb/VX600.html](http://www.msi.com/product/nb/VX600.html)

If you look up this card in the driver section on AMD's website, you will see it is supported by ATi's most recent Linux graphics drivers, so installing the proprietary drivers should work on your laptop. It's probably best to look up some other peoples experience with this chipset before installing it, though.

---

### Post by Mark Phelps on 2013-03-22
> **Rhannie said:**
> ... If you look up this card in the driver section on AMD's website, you will see it is supported by ATi's most recent Linux graphics drivers, ...

NOT true for Ubuntu 12.10 (and beyond).  The support for Linux drivers for the HD3x chipset ended last summer.  AMD has written a legacy driver that allows v13.1 to work in Windows -- but this is Linux, not Windows.  To use the Linux driver in Ubuntu, you have to be running Ubuntu 12.04 or older -- because the X-server got updated in 12.10 to a newer version that does not work with the Linux drivers for the HD 2x/3x/4x seried.

---

### Post by ombah on 2013-03-22
> **coffeecat said:**
> That's normal - a battery saving feature. If you don't like it, click on the cogwheel icon top right -> System Settings -> Brightness & Lock -> uncheck "dim screen to save power".

I'm pretty sure it isn't a power saving feature. After 30 secs of inactivity the brightness goes bananas and behave something like this: *Darker, darker, brighter, darker, brighter, brighter, darker, brighter, darker, darker* etc.

---

### Post by ombah on 2013-03-22
> **Mark Phelps said:**
> NOT true for Ubuntu 12.10 (and beyond).  The support for Linux drivers for the HD3x chipset ended last summer.  AMD has written a legacy driver that allows v13.1 to work in Windows -- but this is Linux, not Windows.  To use the Linux driver in Ubuntu, you have to be running Ubuntu 12.04 or older -- because the X-server got updated in 12.10 to a newer version that does not work with the Linux drivers for the HD 2x/3x/4x seried.

So what are your suggestions? Change to 12.04?

---

### Post by 3rdalbum on 2013-03-22
I think your best option is to go back to 12.04. There is not very much difference between 12.04 and 12.10.

Unfortunately AMD doesn't support their GPUs very well on Linux, or for very long. Your next computer should have Nvidia or Intel graphics as they work better on Linux.

---

### Post by ombah on 2013-03-22
> **3rdalbum said:**
> I think your best option is to go back to 12.04. There is not very much difference between 12.04 and 12.10.

Unfortunately AMD doesn't support their GPUs very well on Linux, or for very long. Your next computer should have Nvidia or Intel graphics as they work better on Linux.

Oh, just as I got everything the way I wanted it to be in 12.10...

---

