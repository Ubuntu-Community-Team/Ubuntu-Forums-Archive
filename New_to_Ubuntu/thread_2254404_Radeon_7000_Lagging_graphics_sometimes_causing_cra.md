---
title: "Radeon 7000: Lagging graphics sometimes causing crashes"
date: 2014-11-26
forum: New to Ubuntu
---

### Post by josh106 on 2014-11-26
Hi, I'm competely new to linux and unbuntu. I installed unbuntu studio  on an older computer that my friend had built me about 8-9 years back for  recording music. The most details I can give about it is that it's a  pentium 4, 2.4ghz processer, about 65 free gb of ram on the hard drive, an rv100 radon 7000 video card and an m-audio delta 1010lt sound card. 

I have Jack and ardour working fine to record music but the graphics are lagging quite a bit. When I try to move a window around with the mouse it lags way behind the mouse moving. In ardour the line that indicates how far you are in the recording lags behind and if I try to press the stop button on playback it often won't stop for up to 10 seconds before the button registers and looks like it's been clicked. about twice now the sound got distorted during playback and the program crashed. Obviously it's imposible to watch a video on youtube or from a file. I never had these problems when the computer was on windows and I'm told the video card is pretty decent so I'm not sure why this is happening.

Where do I start fixing this problem? I've never really done programing either so I don't even know where to find settings for the video card in unbuntu studio, I don't see anything like that in settings manager.

Thanks for any help.
Josh

---

### Post by Impavidus on 2014-11-27
Ram is not on your hard drive – except for swap, in a sense, and you may be using that. If you run this command it will tell you (and us) how much ram and swap you have and how much you use:```
free -m
```Also check for processes taking too much cpu time```
top
```You have to consider the possibility that your computer is simply not powerful enough. I don't know about your graphics card, someone else may say something about that.

Xfce, used by Ubuntu studio, is significantly lighter than the most recent Windowses, but it's not lighter than WinXP. If that computer is that old, it was probably build with WinXP in mind.

---

### Post by josh106 on 2014-11-27
Thanks,

```
The readout for the first command is
josh@Tractor:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1508       1058        450         19        112        555
-/+ buffers/cache:        390       1118
Swap:            0          0          0
```

There doesn't seem to be anything taking up too much cpu %. Ironically I tried opening ardour while in the "top" comand readout to see how much it would take, it's taking about 20% during playback, there is no lag and the buttons are responsive! But when I move a window areound it still lags very badly and Xorg takes up to 70%

Do you think it's possible for the computer to be upgraded if that's the case? could it be as simple as upgrading the cpu?

Thanks again
Josh

---

### Post by josh106 on 2014-11-27
video on youtube is sort of working now too, it's like some magic happened. There are pink dots all over the video though and its still somewhat stuttery but it's better then a frozen frame

---

### Post by Impavidus on 2014-11-28
Your ram is fine. Decent computer for an 8 year old box. If Xorg takes a lot of cpu, it may suggest that your graphics card is not powerful enough. This could also be driver related. As said, someone else may help you more with that. You could try lowering the settings of your window manager.

---

### Post by mörgæs on 2014-11-28
Radeon 7000 is a weak card. Even when it was new in 2001 it was considered low performance.

If it's a desktop computer I recommend finding something better and swap the cards.

---

### Post by josh106 on 2014-12-03
Thanks again guys, it's good to know that the pc is decent enough.

My computer is a desktop that only has pci slots and one agp slot. I was looking at the pci cards on newegg and trying to do a forum search on some of the cheaper ones with not much luck. Would a [SIZE=1]SPARKLE PCI Series 700040 GeForce 210 or a [/SIZE][SIZE=1]evga GeForce 6200[/SIZE] work good with ubuntu? or are there any cards in their selection you would suggest? I'm in canada so I'm not sure what sites are good to order from. I just want to be able to watch videos in decent quality and not have any lagging.

---

### Post by mörgæs on 2014-12-03
If you have both PCI and AGP it should be possible to find something useable. Just remember that both of them come in several different versions so take a good look at the connectors.

Nvidia is generally a fine choice and the 6000 series is a good base line, but cards later in the series are significantly stronger than the 6200 (of which there are several versions, just to make the confusion total...) Are you able to find a 6500 / 6600 or higher? The 210 will be excellent, if it fits.

Also take a look at what a complete (used) pc costs. In you find a system from the Pentium D or Core era you will likely get a better card built in.

---

### Post by josh106 on 2014-12-03
Great :)

At that site the 6200 is the highest and best quality looking Nvidia ones next to the 210 that they have in pci(and the 210 is a pci also). There is a [SIZE=2]JATON VIDEO-498PCI-TWIN GeForce 9400 GT 1GB 128-Bit[/SIZE] for not much more price that seems a lot stronger but it only has one standard vga connector and a circle looking one I don't recognize. I already have my one monitor with dvi to hdmi cable in my recording room and an other smaller monitor in the other room.

---

### Post by mörgæs on 2014-12-03
I would expect the 210 to have PCIe and not PCI connector.

---

