---
title: "problems when installing ATI drivers on custom kernel"
date: 2009-04-10
forum: Packaging and Compiling Programs
---

### Post by adam900710 on 2009-04-10
The problems occurred when i want to install the ATI drivers 9.3
The custom kernel is based on 2.6.28.8
The 9.3 driver runs well when i use the default kernel of 8.04.2LTS:2.6.24-24-generic.but it has problem when i install 9.3 on custom kernel(I've removed the ATI driver before installing on the custom kernel),i have tried 2 methods:
1st sudo sh ./ati-*.run --buildpkg Ubuntu/8.04
and install the xorg-*.deb(not the dev version) and fglrx-kernel-source-*.deb and sudo aticonfig --initial -f
after reboot ,i know i have entered the X through the sound,but the screen is a mess....

2nd i fixed the X and remove the drivers by envyng -t(quiet useful)
and sudo sh ./ati-*.deb install int the generic way and sudo aticonfig --initial -f ,reboot and the sameproblem....

i'm now hopeless.......who can help me......

PS: i'm sorry my English is quite poor......

---

