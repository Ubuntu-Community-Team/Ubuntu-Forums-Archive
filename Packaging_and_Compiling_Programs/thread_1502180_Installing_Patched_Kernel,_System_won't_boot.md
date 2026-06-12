---
title: "Installing Patched Kernel, System won't boot"
date: 2010-06-05
forum: Packaging and Compiling Programs
---

### Post by K. Hendrik on 2010-06-05
I recently bought a new Laptop (Sony Vaio VPCS11C5E) and I'm trying to compile a patched Kernel for it. The Patches are needed for the Internal Mic (see [http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone]("http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone")) and for the 3G-Modem (see [http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/]("http://www.codon.org.uk/~mjg59/gobi_loader/kernel_patches/")).What I've done so far is this:

```

sudo apt-get install linux-source

mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-2.6.32.tar.bz2
cd linux-source-2.6.32

patch -p1 < /home/kai/src/enable-internal-microphone.patch
patch -p1 < /home/kai/src/usb-wwan-2.6.32.diff

cp -vi /boot/config-`uname -r` .config

make oldconfig

make menuconfig

export CONCURRENCY_LEVEL=3
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers

```

After this I installed the header and image Deb-Files and rebooted, but i only get a blank screen and the Num-Lock and Casp-Lock LED's keep blinking.

Do I need to rebuild the restricted modules? And if so how can i do that on lucid, the guide wasn't really helpfull for lucid.

System Specs:
Ubuntu 10.04 64-Bit
NVIDIA Geforce 310M 512MB
Intel Core i5 M520 @ 2.40GHz
Quallcomm Gobi 2000


I really hope someone can help me get this working.

EDID: I also posted this in Laptop&Hardware where its definetly misplaced could some Admin please remove that post I can't find a Delete option.

---

### Post by gzarkadas on 2010-06-20
I would propose to follow this guide for compiling your kernel:

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/). 

It worked flawlessly for me for a 2.6.31-21 kernel on my Sony Vaio VGN AR61M (I made a custom Core2 flavour); in addition I did a small hack in the makefile to get -O3 and native instructions, see [http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/#comment-6693](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/#comment-6693); and they worked also. 

It also has instructions (as separate post) on how to upgrade on newer kernel versions. 

Although for karmic, I do not see why it cannot hold true for lucid; you will just have to get the proper git clone from the ubuntu kernel repository (lucid instead of karmic). The patches you want should be applied IMHO after the `git clean -xdf' command.

---

### Post by gzarkadas on 2010-06-20
Yeap, there is also an updated guide for lucid: [http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/05/05/how-to-compile-a-ubuntu-lucid-kernel/). Hope this helps :).

---

