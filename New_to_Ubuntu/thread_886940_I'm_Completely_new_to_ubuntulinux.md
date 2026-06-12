---
title: "I'm Completely new to ubuntu/linux"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mrtasan on 2008-08-11
Hey, I'm completely new to ubuntu/linux and I'm too cheap to buy OS's (i.e. Windows) for my new computer building project. I'll be handling a shuttly I hope, that's if i score a good deal. 

Anyways, I'm worried about driver compatibility because I've been so spoiled using Windows, I'm dumbstruck about linux and applications that can/cannot be run on ubuntu. I've heard of Wine, but ubuntu has a good design so I want to try to tackle this. 

Also, Does ubuntu have the same features as windows? like a firewall, or whatever..?

Thanks

---

### Post by lisati on 2008-08-11
First of all, welcome to the team.

Yes, Ubuntu does come with a firewall. The standard one is called "iptables", and there are programs such as "firestarter" that let you change its settings through the GUI. 

Wine is normally used to run Windows programs - some work better with it than others. (Windows programs don't normally work with Linux without help) See if you can find a Linux equivalent first (one example is "Open Office", which does many of the things that Microsoft Office does)

Ubuntu comes with drivers that can handle a wide variety of hardware. Sometimes the best way of assessing how well they work is by using the "Live CD" on your system before installing Ubuntu.

---

### Post by vikramaditya on 2008-08-11
start here... [http://ubuntuhcl.org/](http://ubuntuhcl.org/)
great hardware compatibility resource. :)

---

### Post by WRDN on 2008-08-11
> **mrtasan said:**
> Hey, I'm completely new to ubuntu/linux and I'm too cheap to buy OS's (i.e. Windows) for my new computer building project. I'll be handling a shuttly I hope, that's if i score a good deal. 

Anyways, I'm worried about driver compatibility because I've been so spoiled using Windows, I'm dumbstruck about linux and applications that can/cannot be run on ubuntu. I've heard of Wine, but ubuntu has a good design so I want to try to tackle this. 

**Also, Does ubuntu have the same features as windows? like a firewall, or whatever..?**

Thanks

You would have to list what you believe Windows "features" are before we could truthfully answer that question.
As has already been said, iptables is included for a firewall, but you don't have to worry to much about breaches because, by default, no services are listening on the ports. To configure the firewall, GUI based software such as Firestarter (good) can be used. Alternatively, Ubuntu comes with ufw (which stands for Uncomplicated Firewall) preinstalled, and this can be used in the Terminal.
As for applications, there are alternatives in Linux for most Windows applications, so you often do not need to use Wine, which can be sketchy anyway. On Ubuntu, you can install both .deb (Debian) and .rpm based packages, so if you find an rpm packaged program you like, it can be converted in Ubuntu to a Debian package, then installed.

---

### Post by oldos2er on 2008-08-11
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by bodhi.zazen on 2008-08-11
> **lisati said:**
> First of all, welcome to the team.

Yes, Ubuntu does come with a firewall. The standard one is called "iptables", and there are programs such as "firestarter" that let you change its settings through the GUI. 

Wine is normally used to run Windows programs - some work better with it than others. (Windows programs don't normally work with Linux without help) See if you can find a Linux equivalent first (one example is "Open Office", which does many of the things that Microsoft Office does)

Ubuntu comes with drivers that can handle a wide variety of hardware. Sometimes the best way of assessing how well they work is by using the "Live CD" on your system before installing Ubuntu.

Firestarter is depreciated (outdated), ubuntu now uses UFW to configure iptables.

You can get a gui interface for ufw, I have not used it ...

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by billgoldberg on 2008-08-11
Read my article on my unbiased review on Ubuntu.

It should be usefull on knowing what to expect.

[link]("http://linuxowns.wordpress.com/try-ubuntu/")

---

### Post by tuxxy on 2008-08-11
Be sure to read the new user guide

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by issih on 2008-08-11
To be honest, do a little bit of research to establish what hardware is likely to run happily under linux. Generally if you stick to the mainstream stuff things will go ok, to give you an idea, I have ubuntu installed on 3 separate rigs:

1) Athlon XP 2500, nforce 2 mobo, nvidia 6800 graphics
2) Athlon64 X2 4600, via k800, ati 2350
3) Apple macbook (Core2Duo, intel X3100 graphics)

All of them work fine after a bit of tweaking, some of the networking and the graphics hardware takes a while, and laptops tend to have more quirks than desktops, but the point I'm making is the hardware support is wide ranging.

Either way, if the hardware is happy under linux just install ubuntu and play away. Linux isn't windows, and it takes a while to accept that a lot of the applications you are used to are not going to run on it, but usually there are replacements, and in some cases direct ports.

If you are building your own computer you might as well give it a go :)

Hope that helps

---

### Post by newbuntuxx on 2008-08-11
Download Everest Home Edition 2.20 (can be found at: [www.filehippo.com](www.filehippo.com)) and find out what kind of motherboard, video card, sound card, network card (wireless if applicable) you have and post them. 

The live CD will test all that hardware that you have except your video card (if its a highend video card like the Geforce 88000 etc...)

ubuntu has better features than Windows, however if you are a hardcore gamer, you may want to dual boot as most of the 3d games (UT3, call of duty 4 etc...) are not ported to linux. 

You can try installing them through wine, but you'll need to spend hours applying the right patches to wine and installing directx etc... So, you are better off dual booting for games.

Edit: for dual booting look at: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by lisati on 2008-08-11
> **bodhi.zazen said:**
> Firestarter is depreciated (outdated), ubuntu now uses UFW to configure iptables.


I only used firestarter as an *example*...... :) Thanks for the update.

---

### Post by mrtasan on 2008-08-12
Thanks everybody! I'll definately look into it once I get started!

---

