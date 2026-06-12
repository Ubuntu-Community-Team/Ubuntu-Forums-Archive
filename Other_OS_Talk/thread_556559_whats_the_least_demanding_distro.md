---
title: "whats the least demanding distro?"
date: 2007-09-21
forum: Other OS Talk
---

### Post by mr32123 on 2007-09-21
I found a computer i my basement:
332Mhz P2,  128MB or ram, and a 10Gb Drive.

I don't need the computer but I'm bored and want to see what I can do with this computer.  Which distro should I use?  I personally was thinking of trying Xubuntu? Any other suggestions?

---

### Post by LaRoza on 2007-09-21
> **mr32123 said:**
> I found a computer i my basement:
332Mhz P2,  128MB or ram, and a 10Gb Drive.


Zenwalk might be just the thing, modern, yet light.

---

### Post by rsambuca on 2007-09-21
How about Puppy linux or DamnSmallLinux?

---

### Post by LaRoza on 2007-09-21
Try them all, Zenwalk isn't live, but there is a live cd available.

---

### Post by Bachstelze on 2007-09-21
I'd go with Debian or Slackware. Gentoo might be a good idea if you can setup distcc to use your main machine for compilation. Also, a BSD would run perfectly well.

---

### Post by regomodo on 2007-09-21
Puppy, Vector, DSL, Wolvix, Arch

Of them all Debian Etch Openboxed setup worked the best for my 448MHz laptop

---

### Post by Pancetilla on 2007-09-21
Install Arch base, and then install xorg and fluxbox to have some nice and lightweight window system.

---

### Post by LaRoza on 2007-09-21
> **Pancetilla said:**
> Install Arch base, and then install xorg and fluxbox to have some nice and lightweight window system.

+1

---

### Post by jrusso2 on 2007-09-21
what about Ubuntu Lite?

---

### Post by RAV TUX on 2007-09-21
> **mr32123 said:**
> I found a computer i my basement:
332Mhz P2,  128MB or ram, and a 10Gb Drive.
 
I don't need the computer but I'm bored and want to see what I can do with this computer.  Which distro should I use?  I personally was thinking of trying Xubuntu? Any other suggestions?



PC-BSD but start with the oldest version, once you have it installed you can go online and upgrade to the current version.

---

### Post by fistfullofroses on 2007-09-21
I would say Arch or Slackware. If you choose slackware do not do an install all. Go with the menu installer, then I would say deselect KDE and the KDE libs. Choose XFCE, fluxbox, or something similar. With Arch just install the base and go with a window manager like fluxbox, evilwm, windowlab, jwm, ede....

---

### Post by ArtF10 on 2007-09-21
I think Fluxbox might be best on an old system like that.

---

### Post by rsambuca on 2007-09-21
> **ArtF10 said:**
> I think Fluxbox might be best on an old system like that.

Well, Fluxbox really isn't a distro!  Fluxbox on...??

---

### Post by dptxp on 2007-09-22
Use Puppy. It will give you good speed. Make a SWAP of 512 MB  to say 1 or 2 GB.

2.17.1 is the latest. I think 93 MB download.

I have posted at their forums a couple of times, they are pretty helpful.

---

### Post by K.Mandla on 2007-09-22
+1 for Arch. It'll make it fly. I had a 300Mhz Pentium II that booted in 37 seconds with Arch.

Ubuntulite is working pretty well these days. You could give it a shot too.

---

### Post by miggols99 on 2007-09-22
+1 for Arch. I recommend Openbox as I have heard it is quite good, and if I ever had an old computer, I would use it.

---

### Post by init1 on 2007-09-22
TTY FTW. If the computer boots from CD, it will run. It even has an installer and a web browser. 
[http://www.minimalinux.org/ttylinux/showpage.php?pid=1](http://www.minimalinux.org/ttylinux/showpage.php?pid=1)

---

### Post by RedSquirrel on 2007-09-22
If you want to stick with Ubuntu, you could do a minimal installation and add Fluxbox, Openbox, IceWM, or something similar:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

I would also have a look at K.Mandla's guide to [tweaking for speed]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/") (see the signature above). It's a nice collection of tips.

---

### Post by kelvin spratt on 2007-09-22
i would go for slax, it is 200mb use a floppy or start cd has all the basics or dynobolic, 600mb, both live discs that can be put on your hardrive but not installed  grub not needed, both are modular so you can just drop modules straight in with no setting up both will save settings so when you restart your settings are saved both ultra fast you do need to learn a bit  with Slax but the site has all the docs the beta 6 is simple to use.

---

### Post by Bart_D on 2007-09-22
> **rsambuca said:**
> Well, Fluxbox really isn't a distro!  Fluxbox on...??

Xubuntu minimal or Ubuntu minimal.  You might be able to get away with Ubuntu Server Edition but would need to invest some time.

---

### Post by jacob01 on 2007-09-22
id say either dsl (damn small linux) or feather linux

---

### Post by GavinZac on 2007-09-22
i put vector linux on a Pentium 2 paperweight/laptop and its running sweetly. gave a discarded piece of old machinery to a friend for a present! :D

---

### Post by aysiu on 2007-09-22
I don't think the distro matters. Just make sure you use a window manager (IceWM, Fluxbox, etc.) instead of a full desktop environment (Gnome, KDE, Xfce).

---

### Post by fistfullofroses on 2007-09-23
Well, other things can make an impact. How many services run after booting? Which init system is being used? How large are the memory resident parts of the system?

---

### Post by fwojciec on 2007-09-23
There is definitely a benefit to optimizing linux performance, especially on those older machines where the differences are much more tangible.  Many modern distributions are simply not designed with such computers in mind, and some distros will are probably more suitable for low end machines than others.

I do agree with aysiu though in the sense that being thoughtful about how the system is set up as a working environment is likely a more significant factor here than things like compiler flags and such.  But still, this is more easily realized in some distros than others.

If I had to set up linux on an older computer I would probably go with something like Slackware or Arch, just because these distros make your system more transparent to you, so it's easier to set up exactly how one wants.  A binary distro in either case, not something like Gentoo, which could be made to run very well on such a machine of course, but the compile times on older hardware would probably get rather frustrating after a while.

---

### Post by RedSquirrel on 2007-09-23
I like the fact that one can stick with Ubuntu and still have a fairly light system.

I have found the Ubuntu base system with Fluxbox works well. With a few optimizations and some trimming, I have mine booting in about 27 seconds, which isn't too bad. There are some other things I can tinker with, but that's OK for now. ;)

---

### Post by ev5unleash1 on 2007-09-23
Well if your looking to have an Ubuntu distro you should try Xubuntu. I only tried it once but Ubuntu only uses about 280 MB of Ram usally and that is small compared to other distros and if they made that smaller in Xubuntu try it out.

---

### Post by Frak on 2007-09-23
Either change your WM or DE, or try Fluxbuntu, DSL, Puppy, Feather, or Arch

---

### Post by R.Bucky on 2007-09-23
Puppy linux - agreed. It is as close as one could get to being put on a floppy!!

---

### Post by angryfirelord on 2007-09-23
I'd go with TinyMe or AntiX.

---

### Post by init1 on 2007-09-23
> **R.Bucky said:**
> Puppy linux - agreed. It is as close as one could get to being put on a floppy!!
80MB is nowhere near floppy size. You can actually run Linux on a floppy. 
[http://modest-proposals.com/Hacklin.htm](http://modest-proposals.com/Hacklin.htm)

---

### Post by afonic on 2007-09-23
> **Pancetilla said:**
> Install Arch base, and then install xorg and fluxbox to have some nice and lightweight window system.

+1

I've got a laptop with specs similar to yours running lightning fast with Arch and Openbox. Plus with Arch you make sure nothing that you don't need runs.

---

### Post by darrelljon on 2007-09-25
> **mr32123 said:**
> I found a computer i my basement:
332Mhz P2,  128MB or ram, and a 10Gb Drive.

I don't need the computer but I'm bored and want to see what I can do with this computer.  Which distro should I use?  I personally was thinking of trying Xubuntu? Any other suggestions?

[http://puppylinux.org/wikka/Distros](http://puppylinux.org/wikka/Distros)
[http://en.linux.wikia.com/wiki/Category:MiniLinux](http://en.linux.wikia.com/wiki/Category:MiniLinux)

---

### Post by R.Bucky on 2007-09-25
ok, ok, fine. ya got me :-)

---

### Post by fajro on 2007-09-25
[SIZE="3"]
Try [**Ubuntulite**!]("http://ubuntulite.tuxfamily.org")[/SIZE]

---

### Post by ExSuSEusr on 2007-09-25
I'd have to say DSL...

---

### Post by mindtrick on 2007-09-25
edit: ignore this.

---

### Post by Bart_D on 2007-09-25
Hmmm,...... Ubuntulite eh?  Sounds interesting...I thoght the project was dead.

---

### Post by mindtrick on 2007-09-25
I'm writing this from Puppy Linux live CD. It's fast as hell and very friendly. I've downloaded a tiny .pup file to install XFCE base. It's the cutest linux experience I've ever had. Make sure you check out Puppy.

---

### Post by RedSquirrel on 2007-09-25
> **Bart_D said:**
> Hmmm,...... Ubuntulite eh?  Sounds interesting...I thoght the project was dead.
It was. It's been revived. ;)

[http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

---

### Post by Lord Illidan on 2007-09-25
Damn Small Linux!

---

### Post by simstim on 2007-10-01
Some excellent suggestions made already. I would add [Absolute Linux]("http://www.pcbypaul.com/absolute/index.html"). Based on Slackware 12 with IceWM window manager.

---

