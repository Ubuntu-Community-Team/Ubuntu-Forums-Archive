---
title: "Running Myth from a USB stick"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by Will_Cain on 2015-11-25
I know very little about Ubunto but am a very experienced Windows user so know my way round most day to day things, butI have decided to try and set up a media centre PC with MYTH seeing as Windows 10 has pulled the plug.

I made a USB 3 stick with Ubunto and Myth on which successfully boots my PC.

What I don't know is will any changes/new apps etc I make/install be written to this stick?

If I install it on my PC on a spare Hard drive will it make the PC duel boot, something I want to avoid?

How do I get the live TV to work as there doesn't seem to be any software for this on MYTH and it doesn't seem to detect my tuner card, is that because I'm running from the USB stick?

Finally can you recommend any books/guides to explain terminal commands, and Ubunto 

Thankyou in anticipation

---

### Post by sudodus on 2015-11-25
Welcome to the Ubuntu Forums :-)

There are several options, for example a persistent live USB drive or an installed system (installed like it were installed to an internal disk). See these links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

---

### Post by deadflowr on 2015-11-25
What's the tuner card?

Also, to use mythtv you'll need to configure mysql and a myth backend as well as a myth frontend.
Not sure how well these would work in a persistent state.

> [COLOR=#000000]If I install it on my PC on a spare Hard drive will it make the PC duel boot, something I want to avoid?[/COLOR]
If you have an other operating system installed then it can.
But with a little tweaking you can set it not to.
(In Ubuntu you'd disable the bootloader, grub's os-prober, which is used to probe for other operating systems.
Then all you'd need to do is use the PC's own boot menu if you wanted to toggle for one system to another.
Each system would(or should be) isolated from one another in this way)

---

### Post by grahammechanical on 2015-11-25
TV tuner cards are a specialist area. The people to go to are here. 

[http://www.linuxtv.org/](http://www.linuxtv.org/)

[https://www.mythtv.org/](https://www.mythtv.org/)

[URL="http://www.mythbuntu.org/home"]http://www.mythbuntu.org/home

[/URL]And you might have been better off installing Mythbuntu. With Mythbuntu it is possible to get at the underlying OS if you know how but otherwise it seems a stand alone Digital Video Recorder system.

> If I install it on my PC on a spare Hard drive will it make the PC duel boot, something I want to avoid?

2 hard drives and 2 operating systems in the same machine and no dual boot? What would the point be of having 2 operating systems in the same machine if it is not possible to switch between the two somehow? 

Regards.

---

### Post by Will_Cain on 2015-11-26
Thanks for the reply. I use WMC going in and out of sleep to record programs so anything that might compromise that is not welcome. I dual boot by pressing F8 and get the Bios boot selection, personally can't see the point of using anything else.

I've got Mytbunto but I'm currently trying to understand how to get the live TV bit of MYTH working, slow going! I think based on what the other responses are saying I'd be better putting MYTH on the other hard drive rather than using the USB stick. I'll make sure that the install doesn't install a dual boot by unplugging the other drives while I do it. Once I've done that I should be able to try more things without having to repeat them every time I boot.

Thanks for the help so far

The Tuner card is TBS PCI-E DVB-T2 Dual tuner

---

