---
title: "Kernel Compile problems"
date: 2005-01-01
forum: Packaging and Compiling Programs
---

### Post by deception on 2005-01-01
I compiled the 2.6.10 kernel with success. Grub editing was also a success. But when  I boot into the new kernel I get : 

Kernel panic - not syncing: VFS unable to mount root fs on unknown-block(0,0) . 

Something to do with filesystems I missed out? 

Hoep someone can shed some light,
deception

---

### Post by clsdaniel on 2005-01-02
Probably it can be a filesystem problem, you got to make sure that the Filesystem your are using as your root partition is compiled on the kernel, or if is a module then load it on an initrd img and set that on grub.

But it seems to me more related to hardware support, are you using SATA or RAIDS?, how about and nforce board? you need to set support for some specific hardware IDE on the kernel.

Also as last resource, you can try to compile in more partition types support, but i don't thik this cna be the problem.

Don't forget to keep a copy of your old kernel aon disk and boot loader!

Edit: It can be a problem with root argument that grub is passing to the kernel.

Good luck!

---

### Post by kirsche on 2005-01-19
Hi, 
I've got the same problem.
Ubuntu on a ASUS Laptop.

VFS: Cannot open root device "hda5" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I don't have any special grub-parameters (just root=/dev/hda5), deleted/checked the links/initrd. The support for my filesystems is build in (ext3 + xfs).
Tried with and without ramdisk support - still same error.
Anybody has an idea?
Thanks!

---

### Post by kirsche on 2005-01-24
Hi again,

problem nearly solved.
Found a thread, that ubuntu needs a initrd file.
So I ran:

make-kpkg --initrd buildpackage -rev Custom.1 kernel_image
dpkg -i kernel-image-2.6.10xxxxx

---

### Post by whitehat on 2005-04-09
I've been having a similar issue installing kernel 2.6.11.7 on Hoary from source (make && make modules && make modules_install && make install)

Everything related to compiling the kernel seems to go ok, the mkinitrd process and the /boot/grub/menu.lst configuration go ok, but when I boot my new kernel I get a > Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(3,1).

I have the appropaite file systems built into the kernel rather than as a module and the rest of the configuration is a copy over from my warty config which would work.

---

### Post by jerome bettis on 2005-04-09
here's how i roll a kernel on ubuntu

sudo -s
apt-get install build-essential libc6-dev binutils bin86 modutils gawk shellutils grep libncurses5-dev kernel-package
cd /usr/src/linux 
make menuconfig
make-kpkg clean
make-kpkg -rootcmd fakeroot --append-to-version -(your custom version ie custom.0) kernel_image modules-image
dpkg -i /usr/src/kernel-image-*.deb

if you haven't deleted all the comments from your /boot/grub/menu.lst file, it will update it automatically for you, so you can just reboot.  it also places a copy of your config in /boot.  kpkg is pretty slick.  those commands worked great for me here, and you shouldn't have to worry about the initrd thing at all.

---

### Post by tarasbulba on 2005-04-10
[QUOTE=jerome bettis]here's how i roll a kernel on ubuntu

sudo -s
apt-get install build-essential libc6-dev binutils bin86 modutils gawk shellutils grep libncurses5-dev kernel-package
cd /usr/src/linux 
make menuconfig
make-kpkg clean
make-kpkg -rootcmd fakeroot --append-to-version -(your custom version ie custom.0) kernel_image modules-image
dpkg -i /usr/src/kernel-image-*.deb

if you haven't deleted all the comments from your /boot/grub/menu.lst file, it will update it automatically for you, so you can just reboot.  it also places a copy of your config in /boot.  kpkg is pretty slick.  those commands worked great for me here, and you shouldn't have to worry about the initrd thing at all.[/QUOTE]
i have solved that problem with making an initrd.img,i just follow the wikis:

> $ sudo mkdir /lib/modules/`uname -r`/boot/
$ sudo cp -a \
/lib/modules/`uname -r`/kernel/security/capability.ko \
/lib/modules/`uname -r`/boot/ && \
sudo mkinitrd -o /boot/initrd.img-`uname -r` `uname -r`

---

### Post by salle on 2005-08-22
The only way to fix kernel panic on startup for me was to enable cramfs-support (compressed file system) in kernel! I also compiled kernel with --initrd -switch.

---

