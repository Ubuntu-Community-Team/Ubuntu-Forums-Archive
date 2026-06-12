---
title: "Trying to make kernel .deb via prevu"
date: 2008-08-11
forum: Packaging and Compiling Programs
---

### Post by tinsami1 on 2008-08-11
I would like to try out the new 2.6.26 kernel in Hardy to see if it solves some exotic problems we've been experiencing.  For this I'm trying to backport it using prevu.

Compiling seems to be no problem, but at the end, it seems to check for an ABI file or folder, doesn't find it, so it aborts as such:

-----
II: Checking ABI for generic...
EE: Previous or current ABI file missing!
    /var/cache/prevu/src/7532/extracted/debian/abi/2.6.26-5.13/i386/generic
make: *** [abi-check-generic] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/7532 filesystem
 -> unmounting /var/cache/prevu/hardy-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/7668 and its subdirectories

========================
Prevu Error: Build failed.
Prevu encountered an error performing your build. The actual
error message may be further up in the scrollback before pbuilder
exited. Please look for a failed dependency or compile error in
the full output.
-----


Any help would be appreciated.

TIA!


--- mike t.

---

### Post by chandra on 2008-09-15
Ditto here, tinsami1.

I have tried compiling the 2.6.27-2.3 generic kernel to see if it helps my Pioneer DVD writer to work, and I too have encountered the same problem. It took several hours for the kernel to compile but right at the end, it gave almost identical errors:
---
II: Checking ABI for generic...
EE: Previous or current ABI file missing!
    /var/cache/prevu/src/27106/source/debian/abi/2.6.27-2.3/i386/generic
make: *** [abi-check-generic] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2
---

It would help if someone who knows kernel-building in Ubuntu using prevu explains what needs to be done.

Thanks.

---

### Post by VMC on 2008-09-15
I'm missing something here. For one thing, this is the first time I came across 'prevu'. After reading the wiki prevu, I still don't know what it does exactualy. Something to do with backporting and installing newer programs on older generics.

With that in mind, and since it has taken a few hours to build, why not build it yourself the old fashion way, by going to the source?

Here's the steps I tke to build kernel-2.6.26.3 for example:
```
1. sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
2. cd /usr/src
3. sudo -s
===Get the Kernel and extract it
4. wget -c http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.26.3.tar.bz2
   OR www.kernel.org
5. tar -xvjf linux-2.6.26.3.tar.bz2
===Link to Kernel Source
6. rm -rf linux
7. ln -s /usr/src/linux-2.6.26.3 linux
8. cd /usr/src/linux
===GET ".config"
9. cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
===APPLY OPTIONS
10. make xconfig or make menuconfig
===Start the compile process
11. make-kpkg clean
12. time make-kpkg  --revision=1custom --initrd kernel_image kernel_headers modules_image|tee MAKE_KPKG_LOG
===Install new Kernel
13. cd .. && dpkg -i linux*2.6.26*.deb
```

It works, and only takes less than an hour to compile using vanilla config file. When I removed all the stuff I don't need, it took 48 minutes to complete!

Edit: Go [HERE]("http://ubuntuforums.org/showthread.php?t=311158") for further help. There is 106 pages to read, but all you need is on page 1.

---

### Post by InfinityCircuit on 2008-09-16
I can think of no conceivable reason to build a kernel with pbuilder.  You should just follow the instructions given (although it would be better to use --rootcmd fakeroot with make-kpkg and to just use make silentoldconfig instead of make oldconfig with a pipe.)

If you want to build a real kernel for distribution, rather than just for personal use, you normally follow this guide:
[http://kernel-handbook.alioth.debian.org/ch-common-tasks.html#s-common-official](http://kernel-handbook.alioth.debian.org/ch-common-tasks.html#s-common-official)

---

### Post by chandra on 2008-09-16
My thanks to VMC and InfinityCircuit for your replies.

I have followed the instructions, and using the latest stable kernel, have compiled these two packages:

linux-headers-2.6.26.5_1custom_i386.deb
linux-image-2.6.26.5_1custom_i386.deb

but I have not installed them yet. I have these questions so far:

1. Shouldn't I be getting three .deb files (modules_image?) instead of only two as above?

2. I have an NVidia GeForce MX 440 video card and need a module for that. Any pointers on how to do that are most appreciated. (I have not thoroughly gone through the 100 plus pages of the Kernel Master Thread, though).

3. InfinityCircuit, are you suggesting that instead of 

(a)```
cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
```
I can simply say
```
make silentoldconfig 
```

(b) and also preferably say
```
make-kpkg  --rootcmd fakeroot clean
```
and
```
make-kpkg  --rootcmd fakeroot --revision=1custom --initrd kernel_image kernel_headers modules_image|tee MAKE_KPKG_LOG
```

Many thanks.

---

### Post by VMC on 2008-09-16
> **chandra said:**
> My thanks to VMC and InfinityCircuit for your replies.

I have followed the instructions, and using the latest stable kernel, have compiled these two packages:

linux-headers-2.6.26.5_1custom_i386.deb
linux-image-2.6.26.5_1custom_i386.deb

but I have not installed them yet. I have these questions so far:

1. Shouldn't I be getting three .deb files (modules_image?) instead of only two as above?

2. I have an NVidia GeForce MX 440 video card and need a module for that. Any pointers on how to do that are most appreciated. (I have not thoroughly gone through the 100 plus pages of the Kernel Master Thread, though).
You only get the two files. After executing "dpkg -i linux*2.6.26*.deb" will will find it build the mod file here "/lib/modules/<linux name>"
It will also put vmlinux and initrd into /boot and rebuild your grub file.

If you build nvidia as a module you can look into the "/lib/modules/linux???" dir for it.

As far as point 3. A lot of people have issue with using "sudo -s" and prefer you using "fakeroute". Use what your comptable with. It's just easy for me to use sudo -s and then control-d afterward to get out of it.
With fakeroute you won't forget.

EDIT: The reason I use the "time" command at the beginning of the line was to time how long it took for the process. And the "tee" at the end was to go over the output messages.
I have since used ">filename 2>&1" at the end of the line to capture ALL output messages and error messages as well. There were over 150+ warning messages I needed to investigate.

So I now use:
```
make-kpkg  --revision=1custom --initrd kernel_image kernel_headers modules_image >LOG 2>&1
```
I don't see any output messages but I can tail the LOG file. That way I can look into the error messages as well.

---

### Post by InfinityCircuit on 2008-09-17
You can do:

```
cp /boot/config-$(uname -r) .config && make silentoldconfig
```

Your fakeroot lines are correct.  The reason why you want to use fakeroot is simple: The only reason you need root privileges to build Debian packages is to make certain binaries and files be owned by root.  sudo is overkill for this, and fakeroot is all you need--if you try executing fakeroot, it will give you a shell where you can seem to chmod stuff but can't do anything beyond this.

If you are ever curious about the contents of a deb, you can use: dpkg -c linux-image*.deb: you will find that the /lib/modules stuff is already included in there, so you don't need a separate package for it.

The Nvidia MX440 requires the nvidia-legacy-glx package, I believe.  You will have to manually compile the drivers against your new kernel, however.  The process should be (from memory--the packages may have slightly different names)

sudo aptitude install module-assistant nvidia-legacy-kernel-src nvidia-legacy-glx && sudo m-a a-i nvidia-legacy-kernel-src && sudo echo nvidia >> /etc/modules && sudo dpkg-reconfigure -phigh xserver-xorg

---

