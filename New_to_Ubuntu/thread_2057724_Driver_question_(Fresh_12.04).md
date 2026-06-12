---
title: "Driver question (Fresh 12.04)"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by HeroJK on 2012-09-14
I ran into a jockey error on a fresh 12.04 install. Got the "Sorry, installation of this driver failed." thing.

The computer that I'm doing this on isn't exactly new, so is it possible that the integrated card isn't supported anymore?

Where should I go from here? I probably shouldn't have taken this long of a break from linux, kind of forgot everything about everything.. Ehhh..

lspci | grep VGA :

VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200]

---

### Post by Epodx64 on 2012-09-14
try running sudo apt-get update && sudo apt-get upgrade
after upgrading then try running Jockey again. I'm a bit more familiar with Nvidia cards but check out this PPA for better drivers then Ubuntu offers (my old Geforce 6150se Nforce 430 chipset would only run with the Nvidia 304.x Drivers same might be true for older intergrated ATI chipsets but im not 100% sure its worth a try though) 
here's the link [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by jerrrys on 2012-09-14
You seem to have video support

[http://manpages.ubuntu.com/manpages/precise/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/precise/man4/radeon.4.html)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+HD+4200&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+HD+4200&as_qdr=all&sa=Google+Search&lang=en)

good luck :)

---

