---
title: "Install on Pentium 3"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by m75 on 2013-11-21
Hi.
I have an old laptop on which the installation takes a long time.
Is it possible to prepare the hard drive and install the system for a faster, modern computer with a different configuration?
Regards,
M.

---

### Post by simbauad on 2013-11-21
I don't get your question. What do you mean by a long time? Does the installation get stuck at some point. You could tell us the output. We would be glad to help you. Lubuntu was designed keeping old and underpowered laptops in mind. So it shouldn't be the problem.

---

### Post by Bashing-om on 2013-11-21
+1 on Lubuntu on older hardware.
[INDENT][INDENT]try it, you'll like it
[/INDENT][/INDENT]

---

### Post by shabuboy on 2013-11-21
It also depends how old your hardware is.

If is is very old and the CPU is non PAE. Lubuntu or Xubuntu 12.04 and older version will be the only ones that work. I ended up doing Bodhi for a 10 yr old laptop.

---

### Post by DuckHook on 2013-11-21
If you are asking whether you can take your HDD out, connect it to a faster system, install Lubuntu and then plug the HDD back into your old system, then the answer is...

...it depends. Okay, that's not especially helpful, but it's the truth. Linux is a hundred million times better at working across varying HW platforms than proprietary crippleware OSes. This is why so many people can install Lubuntu on a USB stick and use it on all sorts of strange computers. Most drivers are built into the kernel and the kernel is largely hardware agnostic (provided you aren't crossing architectural boundaries like Intel to ARM), so this trick often works. However, you have to be sure that you are installing the base system alone. If you install in a machine that has AMD graphics, install the proprietary drivers, then plug the HDD into a machine with a NVidia card, you will just get a black screen and possibly worse.

*simbuaud* asks good questions re: exactly what you mean by "long time", etc. Please provide more info. As a rule, it is best to install on the exact system that you will be running on.> **shabuboy said:**
> If is is very old and the CPU is non PAE. Lubuntu or Xubuntu 12.04 and older version will be the only ones that work. I ended up doing Bodhi for a 10 yr old laptop.+1
What it boils down to is that if you are running some form of Pentium 'M' processor, or certain old Celerons, then modern kernels won't work on it and you need to install an older version that has a non-PAE kernel. Bodhi is highly recommended for really old creaky machines, but again, only the non-PAE kernel. The new kernel will not boot on Bodhi either.

---

### Post by m75 on 2013-11-22
Hi.
Installation takes a few hours. 
Can I just to pull out a laptop hard drive and connect it to a desktop PC via USB for example, possibly using an ATA adapter port, prepare the file system, etc.
Any suggestions welcome.
Regards,
M.

Specification of my old laptop:
CPU Intel Pentium III 750.0 MHz - [COLOR=#242729]SpeedStep[SUP]&#8482;[/SUP][/COLOR] technology.
[COLOR=#242729]Intel                         Mobile 440BX PCI Chipset.[/COLOR]
Memory 256 MB SDRAM PC100 (max. 512MB).
Display 14.1"max. resolution 1024 x 768 ( XGA ).  
Graphics Processor  AGP 2x - ATI RAGE Mobility 128 - 8.0 MB SGRAM, 64 bit hardware accelerated.
The audio controller was a ESS Maestro 3i.
Xircom                         RealPort CardBus 10/100 Ethernet & 56K Modem PC card                         (Type III).
HDD 30 GB EIDE / ATA-100/5400 rpm
CDROM x8

---

### Post by heir4c on 2013-11-22
You can. I have took a Laptop HD and put it on a newer motherboard in my Desktop, and it works. And when I can't use a cd/dvd-drive or a usb, I put i in a other computer and install Ubuntu on it and than I return it to the other computer and that works too.

---

### Post by monkeybrain20122 on 2013-11-22
Yes you can (with the caveat of non pae kernel as others have pointed out).

 But since you have only 256MB of RAM it is not going to be stellar even after you have it setup. You may as well keep the hard drive detached  as a portable so you can boot it off your faster computer (or other computers as long as the hardware is supported) Just make sure you don't install any proprietary graphic driver (uncheck the box install third party software if the computer on which you do the installation has a Nvidia or an AMD card) and **important**: install the bootloader in this hard drive (rather than the internal drive of the computer on which you do the installation)

Linux installation is not tied to machine unless obviously, if you install proprietary graphic driver that doesn't work for other cards.

---

### Post by heir4c on 2013-11-22
ThanX monkeybrain for the extra info about the proprientary driver and about Grub. I forget that.

@m75, You can try a light-distro. Maybe Bodhi Linux.
I look at Distrowatch for a light-distro and found this: 
[http://crunchbang.org/](http://crunchbang.org/)
[http://www.bodhilinux.com/](http://www.bodhilinux.com/)
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)
[http://lxle.net/](http://lxle.net/)
[http://www.planetwatt.com/](http://www.planetwatt.com/)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.swiftlinux.org/](http://www.swiftlinux.org/)
[http://distrowatch.com/table.php?distribution=minino](http://distrowatch.com/table.php?distribution=minino)
[http://zorin-os.com/index.html](http://zorin-os.com/index.html)
[http://equinox-project.org/wiki/Download](http://equinox-project.org/wiki/Download)
For the last one look unther "ISO Image" (it's based up Ubuntu 12.04)

And if you can put more RAM to the computer. It will be work better.

---

### Post by mörgæs on 2013-11-22
Everybody, please don't mention the PAE problem until it's documented that it is in fact a problem. In our case the computer is a Pentium 3 which supports PAE distros (the low performance in general for a Pentium 3 is another matter).

---

### Post by DuckHook on 2013-11-22
> **m75 said:**
> ...Any suggestions welcome.Your system resources are beyond ancient and tiny. Minimalist tinkerers like me would install only a command line environment and reposition it as some kind of server, but this is not practical for general users. In my case, I was unsuccessful with any modern kernel in an old Pentium 3. That old Dell notebook would not even boot. Had to go back to no later than the 2.26 kernel. You can get this in Tiny Core, Damn Small or SLitaz. For new users, Slitaz seems to be the most full-featured with an XP-like interface that makes them feel at home. It is designed for systems like yours and won't take hours to install. In fact, any of the three can be run right off the CD or USB stick. The entire install image ranges in size from 14MB to 50MB, which is a marvel of lightness in these days of multi-GB installation disks.

I've run Lubuntu in as little as 256MB DRAM. You won't get many apps open at once, but it will work in tight memory spaces. The bigger problem, as mörgæs notes, is your P3, which is agonizingly slow and cranky with modern kernels. In your case, I would recommend avoiding the 'buntu family altogether and going with one of the above-noted distros.

---

