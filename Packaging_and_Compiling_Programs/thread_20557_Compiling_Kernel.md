---
title: "Compiling Kernel"
date: 2005-03-17
forum: Packaging and Compiling Programs
---

### Post by andreabg on 2005-03-17
Hello,

just to have  my modem working I need to add  USB/PPPN_HDLC support to linux kernel

where can I download sources for Ubuntu kernel, and what have I to do?

Please consider that I can't still use linux machine to surf internet, so my only possibility is to use windows machine.
so apt  doesn't work (I think in windows)

Any suggestions or help?

Andrea

---

### Post by az on 2005-03-17
install build essential libncurses5-dev fakeroot and linux-source-2.6
unpack the kernel, configure it and make it.

You can install kernel-package to make your life easier.

cd /usr/src
tar xvjf kernel-source*
cd kern*
cp /boot/config-2.6.8.1-3-368 .config
fakeroot make menuconfig
fakeroot make-kpkg --revision=1 --append-to-version=mycustom kernel_image kernel_headers

---

### Post by andreabg on 2005-03-19
Not succesfull

in my system I've got libncurses5 version 5.4-4.,
the only version of libncurses5-dev that I've found it 5.2.20020112a-7

So I've got a critical error and dpkg cannot install libncurses5-dev

I don't know what to do now :-( 

Andrea

---

### Post by maqi on 2005-04-06
Are you looking at the ubuntu repositories? I have libncurses5-dev and it's version 5.4-4. It's an official ubuntu package.

Start [here](http://higgs.djpig.de/ubuntu/www/) and you should find what you're looking for.

Good luck :)

maqi

---

