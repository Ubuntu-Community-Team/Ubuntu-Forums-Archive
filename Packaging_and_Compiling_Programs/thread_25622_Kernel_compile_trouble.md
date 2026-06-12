---
title: "Kernel compile trouble"
date: 2005-04-10
forum: Packaging and Compiling Programs
---

### Post by popeye on 2005-04-10
Hello,

I'am trying to compile a new kernel, but having trouble with the following message.

I don't understand what i'm missing. Anyone can help:



  INSTALL sound/usb/usx2y/snd-usb-usx2y.ko
if [ -r System.map ]; then /sbin/depmod -ae -F System.map -b /home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7/debian/tmp-image -r 2.6.10-5-k7; fi
WARNING: /home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7/debian/tmp-image/lib/modules/2.6.10-5-k7/kernel/drivers/media/video/saa7134/saa7134-dvb.ko needs unknown symbol videobuf_dvb_unregister
WARNING: /home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7/debian/tmp-image/lib/modules/2.6.10-5-k7/kernel/drivers/media/video/saa7134/saa7134-dvb.ko needs unknown symbol videobuf_dvb_register
make[3]: Leaving directory `/home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7'
test ! -e debian/tmp-image/lib/modules/2.6.10-5-k7/source ||                        \
   mv debian/tmp-image/lib/modules/2.6.10-5-k7/source ./debian/source-link
test ! -e debian/tmp-image/lib/modules/2.6.10-5-k7/build ||                         \
   mv debian/tmp-image/lib/modules/2.6.10-5-k7/build ./debian/build-link
depmod -q -FSystem.map -b debian/tmp-image 2.6.10-5-k7;
test ! -e ./debian/source-link ||                                              \
   mv ./debian/source-link debian/tmp-image/lib/modules/2.6.10-5-k7/source
test ! -e  ./debian/build-link ||                                              \
   mv  ./debian/build-link debian/tmp-image/lib/modules/2.6.10-5-k7/build
cp arch/i386/boot/bzImage debian/tmp-image/boot/vmlinuz-2.6.10-5-k7
chmod 644 debian/tmp-image/boot/vmlinuz-2.6.10-5-k7;
if test -d /home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7/debian/image.d ; then                             \
             IMAGE_TOP=debian/tmp-image version=2.6.10-5-k7                          \
                   run-parts --verbose /home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7/debian/image.d ;               \
         fi
if [ -x debian/post-install ]; then                                    \
        IMAGE_TOP=debian/tmp-image STEM=linux version=2.6.10-5-k7    \
                debian/post-install;                                  \
fi
dpkg-deb: bouwen van pakket `linux-headers-2.6.10-5-k7' in `../linux-headers-2.6.10-5-k7_2.6.10-34_i386.deb'.
test ! -s applied_patches || cp applied_patches                        \
                        debian/tmp-image/boot/patches-2.6.10-5-k7
test ! -s applied_patches || chmod 644                                 \
                        debian/tmp-image/boot/patches-2.6.10-5-k7
test ! -f System.map ||  cp System.map                         \
                        debian/tmp-image/boot/System.map-2.6.10-5-k7;
test ! -f System.map ||  chmod 644                             \
                        debian/tmp-image/boot/System.map-2.6.10-5-k7;
# For LKCD enabled kernels
test ! -f Kerntypes ||  cp Kerntypes                                   \
                        debian/tmp-image/boot/Kerntypes-2.6.10-5-k7
test ! -f Kerntypes ||  chmod 644                                      \
                        debian/tmp-image/boot/Kerntypes-2.6.10-5-k7
rm -f debian/tmp-image/lib/modules/2.6.10-5-k7/build
dpkg-gencontrol -DArchitecture=i386 -isp                   \
                        -plinux-image-2.6.10-5-k7 -Pdebian/tmp-image/
chmod -R og=rX debian/tmp-image
chown -R root:root debian/tmp-image
dpkg --build debian/tmp-image ..
dpkg-deb: bouwen van pakket `linux-image-2.6.10-5-k7' in `../linux-image-2.6.10-5-k7_2.6.10-34_i386.deb'.
rm -f -r debian/tmp-image
echo done >  stamp-image
make[2]: Leaving directory `/home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7'
make[1]: Leaving directory `/home/erik/linux/linux-source-2.6.10-2.6.10/debian/build/install-k7'
dh_testdir
dh_testroot
# unpack the kernels into a temporary directory
mkdir -p debian/d-i-i386
# XXX: this stuff finds the kernels that need upacking according to
# kernel-versions and unpack them into the temp dir.
imagelist=$(cat kernel-versions | grep ^i386 | awk '{print $4}') && \
for i in $imagelist; do \
  dpkg -x $(ls debian/build/linux-image-$i\_*i386.deb) debian/d-i-i386; \
done
ls: debian/build/linux-image-2.6.10-5-386_*i386.deb: No such file or directory
dpkg-deb: --extract heeft een doelmap nodig.
Misschien heeft u dpkg --install nodig?
make: *** [binary-udebs] Fout 2


This are the last messeges after comiling with:

dpkg-buildpackage -rfakeroot -us -uc -b

after following the guideline: 
[http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto)

don't know what to do now.

Thanks in advance

---

### Post by brainwave64 on 2005-06-09
[http://ubuntuforums.org/showthread.php?t=40411](http://ubuntuforums.org/showthread.php?t=40411)

---

### Post by jerome bettis on 2005-06-09
sudo apt-get install build-essential libc6-dev binutils bin86 modutils gawk shellutils grep libncurses5-dev kernel-package fakeroot
cd /usr/src/linux  (assuming this is setup and points to your kernel tree)
sudo make menuconfig
sudo make-kpkg clean
sudo make-kpkg -rootcmd fakeroot --append-to-version -your_custom_version_number(1.0 etc) kernel_image modules-image
sudo dpkg -i /usr/src/kernel-image-{version).deb

that will automatically put a menu option for grub too.

---

### Post by kvidell on 2005-06-09
Am I the only person who compiles like this:
sudo -s -H
cd /usr/src/linux (assuming it's already unpacked and symlinked)
make menuconfig
make -j2 modules
make -j2 modules_install
make -j2 install
mkinitrd -o /boot/initrd.img-2.6.x 2.6.x
vim /boot/grub/menu.lst

Is there something wrong with doing it that way? Always done me well.
- Kev

---

### Post by jerome bettis on 2005-06-09
no nothing wrong with that at all.  i like the -j2 flag idea actually.

i always use kernel-package though because you get a .deb you can have hanging around and you can dpkg --purge it if need be.  plus it updates the grub menu automatically.

---

