---
title: "Best flavour of Ubuntu for 6 year old machine"
date: 2014-10-09
forum: New to Ubuntu
---

### Post by Ross_Munro on 2014-10-09
In a bizarre twist Microsoft are demanding that I activate my copy of Windows XP after 6 years of use. I am happy to do that except when I choose to activate I end up in a worm hole that always ends up saying Windows XP is no longer supported, or they can't find the server. In the meantime an alert regularly pings onto my desktop saying I only have 3 (2,1) days to go before my computer is shut down. I have been considering a change to Ubuntu for my next computer, except I'm in no position to do that now. My only option to keep working (it seems) is to reformat and load a version of Ubuntu that's a similar pedigree to my current computer (AMD Athlon 64, 3500+, 2.21 GHz, 1.93 GB ram). Can someone please suggest a plan of attack for me? Time is of the essence because the clock is ticking. Thanks for any advice in advance.

---

### Post by A.O._Stanley on 2014-10-09
I am running Ubuntu 14.04 on an HP laptop that is probably a couple of years older than the device you're using. This machine had XP on it in a previous life. You might look at Lubuntu if you're concerned that Ubuntu might be too heavy for your old machine. Or, you could try each and see which is a better fit.

---

### Post by Dennis N on 2014-10-09
I had an AMD Sempron 3100+ single core which was running Xubuntu 14.04 just fine. It dated from about 2005. I gave it to someone else a few months ago, but it was still going strong. You can test Ubuntu and it's other family members - Xubuntu, Lubuntu, and Kubuntu + some other derivatives with a live CD or USB before installing on your hard drive to see how it goes and suits you.

---

### Post by grahammechanical on 2014-10-09
Graphic adapters are an important component for the modern OS. Ubuntu needs a graphic adapter that can do hardware accelerated 3D rendering. So, what is the graphic adapter and how much of its own memory does it have?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

[http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop](http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavour-of-ubuntu-desktop)

Regards

---

### Post by Ross_Munro on 2014-10-10
Wow, you must be psychic Graham. It was the graphics adapter (Nvidia geforce 8500, 512 mb) dying that prompted the Microsoft ultimatum. I removed it and just plugged my screen into the alternative, main board connector on the back of the tower. Checking in Device Manager tells me that my video card is now Nvidia GeForce 6100 nForce 400. That sounds like enough to me? (note question mark). Thanks to all replies. I think I'm OK to go with 14.04. If I get stuck I'll move to Lubuntu.

---

### Post by sudodus on 2014-10-10
Lubuntu and Xubuntu ***14.04 LTS*** are good alternatives. If problems with the graphics, please try the [boot options]("https://help.ubuntu.com/community/BootOptions"). You can start with **nomodeset**, which often helps with nvidia graphics. Then you can try with a ***proprietary nvidia driver***, for example 173 or 304.

If still no go, I suggest that you try a community re-spin based on Ubuntu ***12.04 LTS***, which promises support until April 2017: ***Bento, Bodhi or LXLE***. An older version of Ubuntu is more likely to work with older hardware.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Mike_Walsh on 2014-10-10
I'll back up the replies on here.

I'm running an elderly Compaq Presario desktop PC that's 10 years old. I, too, have the Athlon 64 (the 3200 +), with 3 GB of RAM, and am using the onboard ATI Xpress 200 graphics adapter. I upgraded it to 3 GB from the 1 GB it had when it was 'donated' to me back in January, since the Xpress 200 uses a 'reserved' chunk (256 MB) of the system RAM.

I run Ubuntu, Xubuntu, AND Lubuntu. All three work flawlessly; although if you're concerned about graphics rendering, I will definitely recommend Lubuntu. I know people who like it so much (despite the 2D graphics ), that they run it on top-end systems, with much higher specs than yours OR mine..! :D

Regards,

Mike.

---

### Post by tdawgf on 2014-10-11
I would also have to second Lubuntu. I am unsure as to the state of drivers for your onboard card. I do know that Ubuntu will run on single core PCs, though I highly recommend a lighter distribution. Others have suggested Lubuntu, and Xubuntu. I love both, but I would lean toward Lubuntu. i find it to be one of the better derivatives of Ubuntu, but it is all personal taste. I am currently developing my game on a combination of a Macbook Air and a Lubuntu desktop, so Lubuntu doesn't lag behind at all.

---

### Post by Alex Eagle on 2014-10-11
My reccomendation is the latest Ubuntu with XFCE DE installed. This should avoid a lot of compatability issues for an old machine.

To install XFCE open terminal and type:

```
 sudo apt-get install xubuntu-desktop 
```

I'm sure you know how to install Ubuntu and open terminal.

:-) Hope that works.

---

