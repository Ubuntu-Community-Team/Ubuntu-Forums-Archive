---
title: "Kernel Panic after compilation of 2.6.24 in 6.06"
date: 2008-02-03
forum: Programming Talk
---

### Post by keeler1 on 2008-02-03
I am taking a course in Operating Systems.  The first basic assignment was to install Ubuntu 6.06 (which went good) and then install a custom kernel.  By custom kernel I mean the 2.6.24 kernel with a new Name.  

All I did was change the EXTRAVERSION field in the Makefile of the kernel sources.  Here are the steps I went through.

```
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev initrd-tools 
```

It couldnt find initrd-tools so I downloaded initrd-tools_0.1.84ubuntu1_all.deb from an Ubuntu site.

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fi%2Finitrd-tools%2Finitrd-tools_0.1.84ubuntu1_all.deb&md5sum=14829bcaf192fc74a3b6c6d37f63040d&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fi%2Finitrd-tools%2Finitrd-tools_0.1.84ubuntu1_all.deb&md5sum=14829bcaf192fc74a3b6c6d37f63040d&arch=all&type=main)

After that was Installed I then took the following steps which all seemed to complete successfully.

```
cd /usr/src/
sudo chmod 775 .
sudo adduser `whoami` src
sudo wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2
md5sum linux-2.6.24.tar.bz2
```

The md5sum check out.

I then unpacked the kernels source and copied it to two directories one I wont touch and the other for the project.

```
tar -xjvf linux-2.6.24.tar.bz2
cp -ra linux-2.6.24 pristine-linux
cp -ra linux-2.6.24 project0
ln -s project0 linux
```

After changing the EXTRAVERSION field in the Makefile I executed the following

```

cd /usr/src/linux
make V=1 mrproper 
cp /boot/config-2.6.15-26-386 /usr/src/linux/.config
make V=1 xconfig
make V=1 bzImage
make V=1 modules
sudo make V=1 modules_install
sudo mkinitrd -o /usr/src/linux/initrd.img 2.6.24-GLUSERNAME-FIRSTNAME-cs421project0
sudo -s
cp /usr/src/linux/arch/i386/boot/bzImage /boot/bzImage-2.6.24
cp /usr/src/linux/initrd.img /boot/initrd.img-2.6.24
cp /usr/src/linux/System.map /boot/System.map-2.6.24
ln -s /boot/System.map-2.6.24 /boot/System.map
```

Then I added the following to my grubs menu.lst

```
title Project 0 421 Kernel (2.6.24)
            root (hd0,0)
            kernel /boot/bzImage-2.6.24 ro root=/dev/sda3
            initrd /boot/initrd.img-2.6.24
            boot

```

I restarted and tried to boot into the new but unchanged kernel.  I saw a lot of output go by and then at the end I got the following error.

```

mount: mount point dev does not exist
pivot_root: No such file or directory
/sbin/init: 426: cannot open dev/console: No such file
Kernel panic: Attempted to kill init!

```

Can anyone help to explain this.  I contacted my TA about it and he told me it was a hardware issue and to use VMWare to run it instead of booting directly into it.

Is it something I did that screwed it up or something I didnt do?

---

### Post by Compyx on 2008-02-03
Looks like your initrd.img is screwed. I have to say that the above steps are a bit more than I usually take to compile a vanilla kernel.

What I usually do (on a custom built system like mine or a Gentoo box) is:

1. untar the kernel source into /usr/src
2. run 'make menuconfig' (make sure the ncurses libraries are installed for this to work).
3. select the appropriate configuration for your particular hardware.
4. exit and run 'make && make modules_install'
5. copy bzImage, System.map and .config like you did.
6. alter grub's menu.lst
7. reboot
8 (optional) recompile anything that depends on the kernel like nVidia drivers and external alsa drivers.

By default the 2.6 kernel doesn't use an initial ramdisk, so that's one less thing to worry about.

---

