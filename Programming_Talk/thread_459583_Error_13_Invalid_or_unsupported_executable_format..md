---
title: "Error 13: Invalid or unsupported executable format."
date: 2007-05-30
forum: Programming Talk
---

### Post by timdoc1 on 2007-05-30
Hi,

I downloaded the 2.6.21.3 kernel from kernel.org. I build this, added this to the menu.lst file and trying to boot this and get this error. I am running on a Pentium III Celeron (Coppermine) and set this in make menuconfig.

After I did make bzImage, I moved both the vmlinux file from the root into a sub-dir of boot. I also tried copying the vmlinux.bin file that was made in the arch/i386/boot directory into this same directory and tried booting this. I think the vmlinux file from the root dir is the real file, but I thought I would try the other file as well.

We are students and need help!

Thanks,
Hachemi, Sunil and Tim.

---

### Post by moma on 2007-05-31
Hello Hachemi, Sunil and Tim.

Try these instructions, steps 1 - 7. [Link...]("http://home.online.no/%7Eosmoma/kompilere_kjerne.html")
The text is in Norwegian language but just issue the commands and you're done.

In step 5) "make oldconfig" press [Enter] if you do not know what the option is. [Enter] sets a safe default value.

In step 5), you take copy of the old and stable **.config** file and put it into /usr/src/linux. 
cp /boot/config-`uname --kernel-release`  ./.config
Start "make menuconfig" and check what the processor type was set to.

[COLOR="RoyalBlue"]A piece of advice:[/COLOR]
* Compile and test your kernel before you make changes with "make menuconfig".  But of course do "make oldconfig".

* When you boot your new kernel, it may have loosed the display driver. Each kernel in **/lib/modules/2.6.*** has its own drivers and modules. 
If the driver has gone, then you can get up & running by editing the /etc/X11/xorg.conf  and set the Driver to "vesa".  Driver "vesa" vil give a basic, usable graphical GUI.

Notice also: In Ubuntu, the display drivers are normally handled by DKMS. Study: [http://freshmeat.net/projects/dkms/](http://freshmeat.net/projects/dkms/)  and [http://linux.dell.com/projects.shtml#dkms](http://linux.dell.com/projects.shtml#dkms)

* If you need to re-configure and re-compile the kernel several times, run 
# make-kpkg clean
before every compilation.

Give also a new revision (--revision ) string for each test. Eg.
# make-kpkg -initrd  --revision=custom.1.2b  --append-to-version=-686 kernel_image kernel_headers modules_image

---

