---
title: "How to put logging into the kernel"
date: 2011-05-05
forum: Programming Talk
---

### Post by jasejones7 on 2011-05-05
I found a way to do something that I thought could be useful to others and I wanted to share it. The purpose of this post is to explain a way to add some logging to the kernel. 

The reason I have needed to do this is to get a load balancer kernel module working, that was written by someone else. I can see in the module where control is passed to the kernel, but could not work out why the kernel was doing what it did (dropping an IP packet). I needed to log certain things in the kernel code to work out what was going on. I was using Ubuntu 10.10, and I needed to access the kernel source code, add some printk instructions, re-compile the kernel and run it, to see what was happening. I wanted to be able to build the kernel quickly, and only re-compile the files I had modified, and not wait several hours for the kernel and it's modules to compile each time I changed my logging.

Using the method below, I can re-compile the kernel with my logging in it and run the new kernel in about 10 minutes. Please note I am not a kernel developer, I am a programmer more experienced with php and java, and I am finding c a pretty steep learning curve. Here is how I did it:

The first step is to rebuild the kernel using some of the instructions on the Ubuntu site. This is the page I used:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

These are the commands I used from this link:

sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
sudo apt-get source linux-image-$(uname -r)

If I remember correctly, the last command gave me the linux sources as a .tar.gz file in /usr/src, which I unpacked:

sudo tar zxvf linux-source-2.6.35.tar.gz

There are various ways to obtain the sources as on the link above, and also from this link:

[http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/](http://blog.avirtualhome.com/2010/11/06/how-to-compile-a-ubuntu-10-10-maverick-kernel/)

Whichever way I did it, I ended up with the kernel sources in the following directory:

/usr/src/linux-source-2.6.35/linux-source-2.6.35/

From the first link above, further down the page is a heading: Alternate Build Method: The Old-Fashioned Debian Way. I used some of the instructions here to build my kernel. The commands were:

sudo cp -vi /boot/config-`uname -r` .config

This copies the existing config in to use for my re-compile, because I only want to add logging, I don't want to change the configuration.

sudo apt-get install libncurses5 libncurses5-dev
sudo make localmodconfig

This line should speed up the build substantially, by only compiling needed modules. By default, the Ubuntu kernel has a very large number of modules so as to run, out of the box, on as much hardware as possible.

sudo make menuconfig
sudo fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers

For -some-string-here I substituted my name, jase, so as to be able to identify my kernel when i type uname -r. The next step was to install the kernel, by running the following commands:

cd ..
sudo dpkg -i linux-image-2.6.35.11-jase_2.6.35.11-jase-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.35.11-jase_2.6.35.11-jase-10.00.Custom_i386.deb

At this stage on the KernelCompile page on the Ubuntu site, where I got these instructions from, it says that the initrd image is not made properly and it needs to be made. I did not need to do this on Ubuntu 10.10. The dpkg commands above were sufficient to install the complete kernel, and all I had to do was reboot, and my machine simply booted up into my new kernel.

sudo reboot

At this stage I was booted up in my new kernel and all was well so far. Open up the file /boot/grub/grub.cfg with nano or other editor, and find, about 10 lines down, the line that says:

set default="2"

The 2 will probably be 0, which means the default kernel to boot is the first in the list of kernels below. You can change this number to change the kernel that boots, and I suggest you change back to the normal kernel, before adding logging to the new one. With mine, my original Ubuntu kernel is option 2, so I set it to 2 and reboot. I will then be booted into my original kernel, from which I will make modifications (such as adding printk statements) to my new one. The possible kernels are listed lower down in the file, and the list is 0 based, so the first in the list is 0. The second one is usually a safe mode of the same kernel which I don't normally use, and therefore the third, number 2 is the next proper kernel, probably the original one.

After adding my logging statements to the kernel sources in /usr/src/linux-source-2.6.35/linux-source-2.6.35/ using nano, I was then able to rebuild the same kernel and run it. These are the commands required to build the kernel again and install it:

cd /usr/src/linux-source-2.6.35/linux-source-2.6.35/
sudo fakeroot make-kpkg --initrd --append-to-version=-jase kernel-image kernel-headers
cd ..
sudo dpkg -i linux-image-2.6.35.11-jase_2.6.35.11-jase-10.00.Custom_i386.deb

The first command moves to the top of the sources as usual for building the kernel. The second one performs the rebuild, but only re-compiles files that have changed and ones that depend on them. make still goes through a lot of steps and outputs copious amounts of information that I can't understand, but it is clear which files are being compiled, and the whole process only takes about 5 minutes. The last two commands simply unpack the new kernel and install it (this take a few more minutes), and this will also update /boot/grub/grub.cfg to make the newly compiled kernel the default. You can check this to be sure, or reboot. If the machine won't boot, you need to get a live cd, boot off that and change /boot/grub/grub.cfg to boot off the original kernel and fix the problem from there.

Using this method I was able to add logging to the kernel to diagnose the problems with a load balance application. It was an easy way to add logging repeatedly to different parts of the kernel and see what was going on. Good luck!!

Jase

---

### Post by heyandy889 on 2011-05-05
Yeah, right on, my brother. I did some kernel development for my Operating Systems class this semester. The most time consuming part was recompiling the kernel. Here are some parts of your post that stand out to me.
> **jasejones7 said:**
> 
The first step is to rebuild the kernel using some of the instructions on the Ubuntu site. This is the page I used:
**[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)**

...

sudo make localmodconfig
** This line should speed up the build substantially, by only compiling needed modules.**

...

The first command moves to the top of the sources as usual for building the kernel. The second one performs the rebuild, but **only re-compiles files that have changed and ones that depend on them.** 

Yep. You nailed it, dude. Once you have the .c files translated, or "compiled," into .o files, then there's no need to recompile them. Changing 1 .c file won't add much time. Changing a header .h file might add a considerable amount of time, because there are probably a lot of .c files that include the .h file. Or, if you run "make clean" to erase all your object files, that will set you back to square one. But yes, my friend. I believe that we are on the same page, here.

---

