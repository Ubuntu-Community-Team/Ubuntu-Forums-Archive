---
title: "How do I compile a kernel (Linux Newb)"
date: 2005-04-08
forum: Packaging and Compiling Programs
---

### Post by SolidStClair on 2005-04-08
Hi, I am fairly new to Linux and I love Ubuntu. I want to recompile my kernel to get my system running faster, but I have no idea where to begin. Can someone please write out some directions for me? Thanks.

Dell Latitude Cpx H 500 mhz PIII (non-speedstep)
448 MB PC 100 RAM
30 GB HDD
ATI Mobility 8 MB AGP 2x
ESS Maestro 2E

---

### Post by az on 2005-04-08
Open a terminal.

sudo apt-get install build-essential linux-source-2.6 libncurses5-dev kernel-package

cd /usr/src
tar xvjf linux-source*
cd linux-source
cp /boot/config-2.6.10.5-386 .config
sudo make menuconfig

cofigure the heck out of your kernel

sudo make-kpkg --revision-1 --append-to-version=mykerne1 kernel_image kernel_headers

cd ..
sudo dpkg -i linux-image-2.6.10*.deb


Seriously, this probably will not make your system go any faster.

---

### Post by jdong on 2005-04-08
[QUOTE=SolidStClair]I want to recompile my kernel to get my system running faster,[/QUOTE]

That is quite a misconception.... I have a i386 and athlon-k7 optimized kernel on my system, and am using an AMD64. I cannot measure or feel any difference in speed.

---

### Post by shakin on 2005-04-08
[QUOTE=jdong]That is quite a misconception.... I have a i386 and athlon-k7 optimized kernel on my system, and am using an AMD64. I cannot measure or feel any difference in speed.[/QUOTE]

I agree. Compile if you want specific functionality that you can't get by default. Don't let the Gentoo folks fool you into thinking you need to compile anything to gain speed :)

---

### Post by CRCampbell on 2005-04-08
Down with Gentoo!  Heretics and insulters of our great Ubuntu Nation!

---

### Post by az on 2005-04-08
Alrighty.


*Ahem*.

I think Ubuntu attracts many people.  Possibly many people tried linux years ago when it was recommended to recompile a kernel after you install.  This is no longer the case.

The message to these people is:

1- Welcome back.

2- Stock distribution kernels are pretty much all you will ever need to use.  You will not have to recompile your kernel.  And also, you can compile kernel modules (drivers) without having to recompile the kernel.  Look at the linux-headers package.


------------
On another note, Gentoo rocks, too.  Just differently....

---

### Post by jdong on 2005-04-08
[QUOTE=CRCampbell]Down with Gentoo!  Heretics and insulters of our great Ubuntu Nation![/QUOTE]

Ok... that's a bit *too* strong.... ;)

The problem is that you take quite a large responsibility into your own hand... Every vendor has a team of kernel experts tracking the latest patches flying around lkml for security fixes, stability patches, and bugfixes, which are often not going to be released officially for a relatively long time.

You are best off leaving the job of kernel management to experts. The Ubuntu kernel comes in 386,686, and k7(Athlon) flavors, which should be optimized enough for any purpose.

---

### Post by fsman on 2005-04-10
[QUOTE=azz]Alrighty.


*Ahem*.

I think Ubuntu attracts many people.  Possibly many people tried linux years ago when it was recommended to recompile a kernel after you install.  This is no longer the case.

The message to these people is:

1- Welcome back.

2- Stock distribution kernels are pretty much all you will ever need to use.  You will not have to recompile your kernel.  And also, you can compile kernel modules (drivers) without having to recompile the kernel.  Look at the linux-headers package.


------------
On another note, Gentoo rocks, too.  Just differently....[/QUOTE]

WRT point 2. I'm trying to get the 'Zoran' video driver installed. I'm trying rebuild the entire kernel.
what do I need to do to just build the Zoran module?

---

### Post by edubarr on 2005-04-10
Here's a link to a kernel how-to:
[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

I build my own kernel and I don't think that's a bad idea. It's configured to my system and everything works in the best way possible. The only thing you really need is a little curiosity and knowledge of what hardware you have on your system.

---

### Post by az on 2005-04-10
[QUOTE=fsman]WRT point 2. I'm trying to get the 'Zoran' video driver installed. I'm trying rebuild the entire kernel.
what do I need to do to just build the Zoran module?[/QUOTE]


sudo apt-get install build-essential linux-headers-2.6.10-5-386 (if that is the kernel you are using)

Untar the driver source
tar xvzf XXXXX.tar.gx
cd XXXXXX
 

then read the readme.  If there is a debian directory there, try
sudo debian/rules binary

---

### Post by maqi on 2005-04-10
[QUOTE=edubarr]Here's a link to a kernel how-to:
[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

I build my own kernel and I don't think that's a bad idea. It's configured to my system and everything works in the best way possible. The only thing you really need is a little curiosity and knowledge of what hardware you have on your system.[/QUOTE]

I agree that compiling a kernel is a very instructive experience. However, since we're on a debian based distro it might be better to point to links which describe the debian way of compiling IMHO (cue make-kpkg vs traditional kernel compile flame  :twisted: ): 

[http://myrddin.org/howto/debian-kernel-recompile.php](http://myrddin.org/howto/debian-kernel-recompile.php)

[http://www.falkotimme.com/howtos/debian_kernel2.6_compile/](http://www.falkotimme.com/howtos/debian_kernel2.6_compile/)

The advantage, especially for a newcomer, is that it is easier to install the custom kernel. And very much easier to uninstall the custom kernel if things don't work out quite as expected, eg, sudo apt-get remove --purge <custom-kernel-version>; or dpkg -P <custom-kernel-version_revision> rather than trying to reverse all the steps in the traditional kernel compile.

That said, one advantage of compiling your own kernel -however you choose to do it - is that you can leave out modules for old and/or non-existent hardware. If you don't have parallel ports why do you need that module? If you're not using pre ATAPI/IDE cd drives why do you need that module? How many average desktop users need support for the minix file system? Almost noone actually uses IPv6 - everyone ends up disabling it so that they can actually surf the net before they die - so why have it in there? And the list goes on and on and on.

There is a lot of stuff included in the stock kernels for the sake of compatibility, and this is how it should be. But if you know you don't need it, you don't have to keep it ... one of the beauties of linux. If you download the kernel source from th Ubuntu repsitories you get pre-patched kernel source - so you don't miss out on patches at all.

One thing saved by this process is disk space. The other is time at boot when the kernel starts checking for file systems and modules which match the hardware on the machine. I've also experienced more efficient use of memory. So it can be worth it. However, you will need to make sure you know your hardware and find out what modules you need to include for it to work, otherwise you will have an unbootable machine at the end of it all.

Good luck - it's a long journey :)
maqi

---

### Post by wazoo42 on 2005-04-18
I have a dual opteron system, so recompiling is necessary for me to get smp support and mtrr support.  Other than that I would be more than happy with the stock kernel.  BTW I tried using apt-get to install the smp image and it worked except my usb mouse and kb do not work.  They light up during bootup and then go dark again.  This even happened when I compiled my own kernel using the single proc .config and only changed smp and mtrr.  Any ideas?

---

### Post by N'Jal on 2005-04-20
> [http://www.falkotimme.com/howtos/debian_kernel2.6_compile/](http://www.falkotimme.com/howtos/debian_kernel2.6_compile/) 

Should we on Ubuntu use debian backports? I think i might have messed up a 4.10 install that way.

Correct me if i am wrong because i too, wish to learn to recompile kernels it will come in handy for me in years to come.

If we SHOULD avoid backports, what should i do to avoid the backports step?

Also the above mentioned guide dont seem to include GRUB in the kernel step but i know how to do that bit. Failed enough kernels to date to know how to do the grub step. :P

---

### Post by hobnob on 2005-04-22
For a more thorough overview of compiling your own custom kernel for Ubuntu, check out the [Wiki page](http://www.ubuntulinux.org/wiki/KernelHowto). azz's method leaves out the creation of the initrd, which is critical.

---

### Post by casualprogrammer on 2005-12-06
[QUOTE=azz]
tar xvjf linux-source*
cd linux-source
[/QUOTE]
Hi azz,

thank you for your hints. I tried them out ( Ubuntu 5.10, Intel x86 ) and found some obstacles I would like to add for the sake of others.

The lines above need to read as follows:
sudo tar xvjf linux-source*
cd linux-source-v.v.vv ( kernel version, in my case 2.6.12 )

Also make will not run with gcc 4.0, you will have to manually install gcc 3.4 with "sudo apt-get install gcc-3.4", there is a bug report on this at "http://bugzilla.ubuntu.com/show_bug.cgi?id=17517"

Cheers Casual

---

### Post by DaveApmTX on 2006-01-07
I am trying to install a driver for a Creative Webcam Live! and the instructions require compiling the driver using the same compiler and version as was used to compile the Kernel.  

I would rather not compile the Kernel (and risk making new errors), is there a way to determine the comiler and version that was used to prepare Ubuntu 2.6.12-10-386?

Regards,

Dave M

---

### Post by yshsu168 on 2006-01-16
Dear Azz:

In my breezy, it shows that 
samuel@ubuntu:/usr/src/linux-source-2.6.12$ sudo make menuconfig
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-source-2.6.12/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[1]: *** [scripts/basic/fixdep] Error 127
make: *** [scripts_basic] Error 2

Do I need to install gcc-3.4 instead of gcc-4.0??

Thanks.

Sam

[QUOTE=azz]Open a terminal.

sudo apt-get install build-essential linux-source-2.6 libncurses5-dev kernel-package

cd /usr/src
tar xvjf linux-source*
cd linux-source
cp /boot/config-2.6.10.5-386 .config
sudo make menuconfig

cofigure the heck out of your kernel

sudo make-kpkg --revision-1 --append-to-version=mykerne1 kernel_image kernel_headers

cd ..
sudo dpkg -i linux-image-2.6.10*.deb


Seriously, this probably will not make your system go any faster.[/QUOTE]

---

### Post by yshsu168 on 2006-01-16
Sorry that I find a temporary solution.
cd /usr/bin
ln -s gcc-4.0 gcc-3.4

---

### Post by GTvulse on 2006-01-16
[QUOTE=yshsu168]Sorry that I find a temporary solution.
cd /usr/bin
ln -s gcc-4.0 gcc-3.4[/QUOTE]
Don't do that!!! You'll end up with a broken kernel because it is **not compatible** with gcc4. You have to install gcc 3.4 if you want your custom kernel to work correctly (or install and compile a 1.6.15 kernel from Dapper, those kernels **can** be compiled with gcc4). Do remove that symbolic link before installing the real thing.

---

### Post by GTvulse on 2006-01-16
[QUOTE=dradul]Don't do that!!! You'll end up with a broken kernel because it is **not compatible** with gcc4. You have to install gcc 3.4 if you want your custom kernel to work correctly (or install and compile a 1.6.15 kernel from Dapper, those kernels **can** be compiled with gcc4). Do remove that symbolic link before installing the real thing.[/QUOTE]
And following up myself. After you configure your kernel, the magic command is:

```

MAKEFLAGS="CC=gcc-3.4" make-kpkg --initrd --rootcmd fakeroot \
    --revision "blah" --append-to-version "blah" \
    kernel_image kernel_headers

```

Why am I not using sudo? The first commandment of Unix administration is "You may never pronounce the name of thy god ROOT in vain." ;-)

---

### Post by jerrykenny on 2006-03-01
For people with older hardware' . . . . 

a custom kernel will give you a faster boot up 

the big disadvantage to doing this with gentoo, is your processor might expire with exhaustion just compiling kde . . . or gnome . . . or koffice . . . etc

(bit off subject that was, anyway I like gentoo, and their documentation is the best on the net)

anyway, I'm off to try the same with dapper, to try and get a Sagem usb modem working (reckon theres a module in there somewhere for it)

---

### Post by sacater on 2007-04-06
when compiling a kernel, will it automagically add it to /boot/grub/menu.lst for me to boot off

thanks

p.s jdong, excuse me, dont go downing gentoo, ubuntu and gentoo are equal, they just use different packing methods. and ubuntu is more user friendly, My best friend is a gentoo dev, who lives 6 miles up the road

---

### Post by ramjet_1953 on 2007-04-07
While I tend to agree with those who have stated that you don't really need to compile your own kernel, I also think that they are "wet blankets". 

If you want to have some fun and feel a sense of achievement - go ahead!

After all, Linux has a V12 under the hood, so why not supercharge it too?

I have had hours of good fun playing with new kernels and especially getting rid of the crap that is installed in "generic" kernels.

My new kernel is definitely noticibly quicker, especially under GNOME. 

If you like to tinker and have fun, go ahead! If you follow correct guidelines, you can't hurt your current kernel or installation, as all that happens is that you get extra boot options under GRUB.

Enjoy!

Regards,
Roger :cool:

---

### Post by myst3rious on 2007-04-23
Alright, here it goes, kernel compiled by Geeks are not performing much.
But i do compile my specific kernel, with Pentium 4 optimizations and removing generic x86 optz, removing all those networking options which i really dont have, and all those sorts of drivers. Then also, making some modules inbuilt in kernel. THis gives me  high responsiveness to my system as compared to the generic kernel, which start getting hitches when I open Acroread, Inkscape with some layers and objects, GImp and Azureus... 
What the heck, I m feeling lucky ...:guitar:

---

### Post by nsilva on 2007-04-28
I dont agree with this Microsoft mentality, the beauty of Linux is that you are able to configure,optimize or just play with it, any way u want.....yeah it is true that is hard to squezee any optimazation out of it.

So if you feel like compiling the kernel, COMPILE IT!! I like doing it, even if I dont make any changes. I feel that I control the brain of my beast!!

Enjoy it!
P.S: Dont mess with Gentoo, it is a great distribution, not aim for the masses but none the less a great work they put into it! Keep up the hard work Gentoo-ers

---

### Post by tlsarles on 2007-05-23
> **az said:**
> 
cofigure the heck out of your kernel

sudo make-kpkg --revision-1 --append-to-version=mykerne1 kernel_image kernel_headers

cd ..
sudo dpkg -i linux-image-2.6.10*.deb


You forgot the ramdisk. Use this command instead

sudo make-kpkg --initrd --revision-1 --append-to-version=mykerne1 kernel_image kernel_headers

---

### Post by alecthunder on 2007-05-25
> **az said:**
> 
...

2- Stock distribution kernels are pretty much all you will ever need to use.  You will not have to recompile your kernel.  And also, you can compile kernel modules (drivers) without having to recompile the kernel.  Look at the linux-headers package.

...


AHA! Excellent hint! I just googled for 'compile kernel modules with linux headers' and found some good stuff. Now I can try to compile the unreleased drivers for my USB Soundcard from Native Instruments. I was about to recompile the kernel from scratch... phew. Btw. I have the Audio Kontrol 1 Soundcard.

---

### Post by boogachamp on 2007-05-27
Good Luck!

I found this to be helpful:
[http://newbiedoc.sourceforge.net/system/kernel-pkg.html#BUILD-KERNEL-PKG]("http://newbiedoc.sourceforge.net/system/kernel-pkg.html#BUILD-KERNEL-PKG")

---

### Post by shae on 2007-06-10
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel")

Just a hint, if you use menuconfig instead of xconfig, you do not need the qt dependencies or will your headers depend on a qt package.

A custom kernel will not be the difference between night and day unless you know what you are doing and spend a long time working on it.  But also a custom kernel allows you to use a newer version as well as allows you to install patches.  Some of these can be very helpful such as Suspend2.  Also it makes your ubuntu install more your own.  I may be a personalization freak, but when running a custom kernel, it is cool to be able to think, "hey, I made that."

---

### Post by praxis22 on 2007-06-29
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

easy to follow, even has screenshots :)

---

### Post by zapcojake on 2007-08-24
> **SolidStClair said:**
> Hi, I am fairly new to Linux and I love Ubuntu. I want to recompile my kernel to get my system running faster, but I have no idea where to begin. Can someone please write out some directions for me? Thanks.

Dell Latitude Cpx H 500 mhz PIII (non-speedstep)
448 MB PC 100 RAM
30 GB HDD
ATI Mobility 8 MB AGP 2x
ESS Maestro 2E

Hello, use synaptic and look for the low latency kernel, the google things like "speed up Feisty" "configure feisty for speed" and how to speed feisty up."  there are some basic tweaks that work very well.

---

### Post by jargoman on 2007-08-29
Ubuntu and Gentoo are my favorite distro's. I like Gentoo because I can optimize every thing and I like Ubuntu because it's reliable and easy. 

I noticed that Ubuntu doesn't have a make.conf file. Is there a way to set compiler flags in Ubuntu the way Gentoo can. ie CFLAGS

also when I recompile my kernel I use a generic config file and only mess with what i know about. 

I once had Gentoo booting in 12 seconds!!!!

---

### Post by kevdog on 2007-09-05
Currently working in Feisty -- is there any negative repercussions about compiling and installing the latest vanilla kernel???  Is the kernel currently contained in the Ubuntu release optimized for something Ubuntu related??  Ive never compiled a kernel before but am eager to "experiment"

---

### Post by Coyote21 on 2007-09-12
> **SolidStClair said:**
> Hi, I am fairly new to Linux and I love Ubuntu. I want to recompile my kernel to get my system running faster, but I have no idea where to begin. Can someone please write out some directions for me? Thanks.

Dell Latitude Cpx H 500 mhz PIII (non-speedstep)
448 MB PC 100 RAM
30 GB HDD
ATI Mobility 8 MB AGP 2x
ESS Maestro 2E

Begin by reading, this post: [http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel+compilation)

You will also need to know your filesystem type (root), type: df -T, and in the list, look for an entry like this one (The one that has an  / in the end):

/dev/sda8      jfs   113189628  11162440 102027188  10%  /

and note down the second field (in this case jfs), this is your filesystem type.

Then in the, config menu (after you type make menuconfig), look for an entry named: Processor Type and Features, then to ProcessorFamily and choose Pentium III or something like that. Then 
go to the main menu again (by pressing, Exit (use your arrow keys to go to it, and press enter), and to File Systems, in there you will need your filesystem type (look for an entry that begins with the field you noted), and select it by pressing space, until an * apears, on it. The rest of the configuration depends an lot of your hardware.

---

### Post by dptxp on 2007-10-07
What happens with kernel updates when you compile your own kernel ?

---

### Post by loseyou2him on 2007-10-23
> **dptxp said:**
> What happens with kernel updates when you compile your own kernel ?

I imagine you just get another kernel option in your grub bootloader.  You can compile the new kernel version as you want or keep using the one you created.  From what I can tell Ubuntu doesn't remove old kernels from the system or the bootloader.

ADDITION:
Just a note, some have mentioned fast boot times with Gentoo and the like.  That's because they remove all but the most necessary services at boot time.  The kernel is only one part of the equation.

---

### Post by ajayre on 2007-10-25
I grabbed the linux source from the Ubuntu gutsy repos and found it to be 2.6.22.9. I built it and installed the package and it worked fine. I used /boot/config-2.6.22-14-generic as the .config file.

Next I grabbed 2.6.22.9 from kernel.org. I built it in the same way and installed the package. It works except ethernet is broken. I again used /boot/config-2.6.22-14-generic as the .config file.

In both cases I didn't configure the kernel - I simply built it.

So I am assuming that something was patched in the Ubuntu version to fix some kind of problem. I need to be able to run a vanilla kernel so I can patch it with RTAI. How do I find out what patch is missing from my vanilla kernel?

thanks! Andy

---

### Post by ajayre on 2007-11-02
Update - I swapped my NIC for a 9 year old one. Works now.

Andy

---

### Post by go_beep_yourself on 2007-11-19
> **az said:**
> Open a terminal.

sudo apt-get install build-essential linux-source-2.6 libncurses5-dev kernel-package

cd /usr/src
tar xvjf linux-source*
cd linux-source
cp /boot/config-2.6.10.5-386 .config
sudo make menuconfig

cofigure the heck out of your kernel

sudo make-kpkg --revision-1 --append-to-version=mykerne1 kernel_image kernel_headers

cd ..
sudo dpkg -i linux-image-2.6.10*.deb


**Seriously, this probably will not make your system go any faster.**

Why don't you do a benchmark or benchmarks to see (comparing ubuntu stock kernel with custom optimized kernel)? Also check the memory usage right after boot before loading any other programs besides the ones that load automatically. Please let us know the results. :popcorn:

---

### Post by kessaris on 2008-07-02
Just wanted to include a couple of links from the ubuntu site that might be helpful:

[Compiling a Ubuntu Kernel]("https://help.ubuntu.com/community/Kernel/Compile")

[Compiling an upstream (not yet incorporated into ubuntu) kernel]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

That said, I didn't realize there was an option to choose a k7 version of the kernel.  I still can't find it, but I'm just going through the config options of my new kernel trying to trim out some of the fat.  I have totally noticed a speed increase when I compile my own kernel.  Plus it doesn't even take that long, just like less than an hour.

I found this thread immensely helpful:

[http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)

It outlines some of the major options you can omit from the kernel.  Actually it cut my kernel size down by about 30% when I chose those options.  From about 50 megs to about 35 if I remember correctly!

---

### Post by go_beep_yourself on 2008-10-13
Does anybody have benchmark results or know how to make benchmarks in Ubuntu to compare the performance difference of a stock Ubuntu kernel with a custom configured kernel?

---

### Post by VMC on 2008-10-13
I think the first few post on this topic from 2005 tells it all. It won't go any faster. It's just a good learning experience. You can add modules or features that you have that are not included though.

I have reduced my kernel almost in half, but the speed is unaffected. It's the "tweaking" of the support programs that might reduce boot up.

---

### Post by crog62 on 2008-12-16
I am trying to build a 2.6.27-9 kernel. I have an existing .config file I want to use. I downloaded the sources and am trying to build with 

# make-kpkg --initrd kernel_image kernel_headers

but it keeps invoking 'make menuconfig' and I don't want to through that process. Is there a way to invoke the make without going through the kernel configuration process? 

Thanks in advance.
Craig

---

### Post by PmDematagoda on 2008-12-16
> **crog62 said:**
> I am trying to build a 2.6.27-9 kernel. I have an existing .config file I want to use. I downloaded the sources and am trying to build with 

# make-kpkg --initrd kernel_image kernel_headers

but it keeps invoking 'make menuconfig' and I don't want to through that process. Is there a way to invoke the make without going through the kernel configuration process? 

Thanks in advance.
Craig

I don't use make-kpkg, but make directly. So it would go like this:-
```
make
```
but the downside is that you don't get the deb packages then.

---

### Post by auroraa9420 on 2010-07-25
> **az said:**
> Open a terminal.

sudo apt-get install build-essential linux-source-2.6 libncurses5-dev kernel-package

cd /usr/src
tar xvjf linux-source*
cd linux-source
cp /boot/config-2.6.10.5-386 .config
sudo make menuconfig

cofigure the heck out of your kernel

sudo make-kpkg --revision-1 --append-to-version=mykerne1 kernel_image kernel_headers

cd ..
sudo dpkg -i linux-image-2.6.10*.deb


Seriously, this probably will not make your system go any faster.


"cp /boot/config-2.6.10.5-386 .config
sudo make menuconfig"

this part confuses me realy

i cant find any config-(new lucid kernel) and i cant copy and i dont know what to do on make menuconfig

help me ASAP

---

