---
title: "How do I run older kernels on current distro versions?"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by mgwhammy on 2013-04-05
I've got an old Toshiba that ran XP poorly even after a fresh install, so I put Ubuntu 10.04 on it awhile back because it seemed to be the only distribution that properly used my sound card.  After a lot of digging I've found that when the kernel went to 3.x a lot of old hardware support was dropped.  One of the self-help guides posted here led me to the kernel documentation website where I found my sound card controller (ALC861-D) was no longer an option to put in the ALSA configs. ([https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](https://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)) 

I recently stumbled upon Lubuntu, which on the 10.04 version did not bog down my hardware at all.  As much as I'd like to stick with it I want to be on something newer since there is no more desktop support forthcoming after April.  I put Lubuntu 12.10 on and my hardware still rocks on it, but I knowingly have no audio now.  I downloaded the 2.6.32-46 kernel and got it in GRUB as a boot option, but when I boot using it the desktop environment doesn't load and I'm left at a command prompt.  I saw where I might need to re-install the desktop from the command line but it would not install since this desktop was already there.  I then issued the startx command but the connection to the X server was refused and crashed.

So far I like 12.10 and want to keep it, but I'd like to run the old kernel so I can have audio too. Is there any way to accomplish this?  

Thanks in advance!

---

### Post by ibjsb4 on 2013-04-05
This sounds like a good question for ..

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by MoebusNet on 2013-04-05
Have you tried out the Lubuntu or Xubuntu 12.04 version? It has better support for older hardware; try it from Live-CD/DVD or Live-USB to confirm hardware compatibiltiy.

[https://help.ubuntu.com/community/Lubuntu/PreviousReleases#A12.04](https://help.ubuntu.com/community/Lubuntu/PreviousReleases#A12.04)

[http://old-releases.ubuntu.com/releases/xubuntu/releases/12.04/release/](http://old-releases.ubuntu.com/releases/xubuntu/releases/12.04/release/)

---

### Post by mgwhammy on 2013-04-05
I loaded 11.10 Live CD and didn't have any audio, so I didn't try 12.04 previously.

---

### Post by MoebusNet on 2013-04-05
Maybe someone else can help with attempting to run an older kernel with newer *buntu's but it might be easier to try a distro specifically for older hardware.

If you can't find a *buntu version that suits, you can try:

[http://peppermintos.com/](http://peppermintos.com/)

[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

[http://www.puppylinux.com/](http://www.puppylinux.com/)

---

### Post by mgwhammy on 2013-04-05
Thanks for these.  Downloading the Wary Puppy 5.5 .iso now. AntiX live CD didn't want to load for me, and while Peppermint looked good it was still silent.  I think it goes back to the 3.x kernel.  Wary Puppy references using older kernels so I'm holding out hope....the other Puppies were built on current Ubuntu kernels.

If anyone else has any ideas on using the older kernels on current version I'm all ears.  Other than no audio I like Lubuntu.

---

### Post by sudodus on 2013-04-05
You can also try Knoppix. I have good experiences using it with very old as well as newer computers. It is known to be good at recognizing hardware.

[[COLOR=#ff0000]http://www.knoppix.org/[/COLOR]]("http://www.knoppix.org/")

---

### Post by MoebusNet on 2013-04-06
Although it may be heavier than you would prefer, Debian 6.0.7 (Stable) is still supported and uses the 2.6.32 kernel. You can try out a Live-CD or Live-USB version to see if it suits:

[http://www.debian.org/CD/](http://www.debian.org/CD/)

I suppose you could always do a minimal-type install and install your preferred desktop environment afterwards. It really depends on how far you are willing to go to utilize your older hardware. There are some decent newer machines on ebay for under $200, so only you know how valuable your time is.

---

