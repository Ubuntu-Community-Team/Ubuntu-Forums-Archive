---
title: "HOWTO: Openswan Klips support in Feisty"
date: 2007-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by ThomasNovin on 2007-04-18
(WARNING: THIS GUIDE IS NOT COMPLETE/WORKING YET AS THERE SEEMS TO BE BUILD PROBLEMS WITH THE KERNEL MODULE AGAINST 2.6.20?)

KLIPS SUPPORT IN UBUNTU FEISTY FAWN (7.04)
==========================================

This guide is written to help us get KLIPS support in Ubuntu. KLIPS is needed to get virtual interfaces (ipsec0 etc.) that can be used when setting up VPN tunnels with Openswan if you are a "road warrior".

sudo apt-get install linux-source
sudo apt-get install linux-patch-openswan
sudo apt-get install kernel-package
sudo apt-get install openswan-modules-source (no need for this?)
sudo apt-get install libncurses5-dev

cd /usr/src
sudo tar jxvf linux-source*.tar.bz2
sudo ln -s linux-source-<your version> linux
cd linux
sudo make oldconfig (enter on all questions)
sudo make menuconfig (if you need to enable SMP support)
sudo make-kpkg clean
cd /bin
sudo rm sh # this is needed or make-kpkg will fail!
sudo ln -s bash sh
cd /usr/src/linux
sudo export PATCH_THE_KERNEL=YES && make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd /bin
sudo rm sh
sudo ln -s dash sh
cd /usr/src/linux
sudo cp -pdvi ../kernel-patches/all/openswan/linux/net/ipsec/* net/ipsec/
sudo cp -Rvpid ../kernel-patches/all/openswan/linux/include/* /usr/src/linux/include/
cd net/ipsec
sudo cp Makefile.fs2_6 Makefile
cd ../..
sudo touch include/linux/config.h
sudo make oldconfig (answer m on KLIPS and default on the rest)
sudo make-kpkg --initrd --append-to-version=-klips kernel_image kernel_headers

Right now this fails at:

  CC [M]  net/ipsec/ipsec_sa.o
net/ipsec/ipsec_sa.c:104: error: ‘struct sk_buff’ has no member named ‘nfmark’
net/ipsec/ipsec_sa.c:104: warning: type defaults to ‘int’ in declaration of ‘type name’
net/ipsec/ipsec_sa.c: In function ‘ipsec_SAtest’:
net/ipsec/ipsec_sa.c:134: error: ‘struct sk_buff’ has no member named ‘nfmark’
net/ipsec/ipsec_sa.c:134: warning: type defaults to ‘int’ in declaration of ‘type name’
make[3]: *** [net/ipsec/ipsec_sa.o] Error 1
make[2]: *** [net/ipsec] Error 2
make[1]: *** [net] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2

Found this: [http://bugs.xelerance.com/view.php?id=747](http://bugs.xelerance.com/view.php?id=747)

Do we need a newer version of linux-patch-openswan?

---

### Post by carpy on 2007-10-10
Why does Ubuntu need specially compiled kernels for KLIPS?  Where is the problem?  This sounds like it requires a bug report, not a HOWTO.  Did you submit a bug report?  I don't see one.

Thanks,
Matt

---

### Post by ScarEye on 2007-10-25
Hey,

Any update with this.  I have 7.04 installed and I need to use KLIPS. I am a newb to linux alltogether but I can follow directions any help would be appreicated.


Thanks
ScarEye

---

