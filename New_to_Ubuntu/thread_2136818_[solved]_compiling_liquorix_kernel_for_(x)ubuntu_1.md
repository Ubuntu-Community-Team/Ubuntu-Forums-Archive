---
title: "[solved] compiling liquorix kernel for (x)ubuntu 12.10"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by rootfairy on 2013-04-18
hi guys,

i just installed the latest liquorix kernel on my xubuntu 12.10 and i really like it. now, i would like to compile the liquorix kernel myself, but i have absolutely no clue of how to do so. can you provide some help, like guides / tutorials? i found a few but they seem outdated. i really want to get into this stuff and learn about linux. like what packages do i need and what commands do i issue? how do i config the new kernel?

help much appreciated, best regards and thanks in advance

related topics:
[http://askubuntu.com/questions/218382/installing-the-liquorix-kernel-on-ubuntu-12-04-x64bit](http://askubuntu.com/questions/218382/installing-the-liquorix-kernel-on-ubuntu-12-04-x64bit)

[http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/)

[http://askubuntu.com/questions/13327/what-would-be-the-recommended-kernel-configuration-for-a-gaming-machine](http://askubuntu.com/questions/13327/what-would-be-the-recommended-kernel-configuration-for-a-gaming-machine)

[http://how-to.wikia.com/wiki/How_to_configure_the_Linux_kernel](http://how-to.wikia.com/wiki/How_to_configure_the_Linux_kernel)

[http://how-to.wikia.com/wiki/Howto_compile_the_Linux_Kernel](http://how-to.wikia.com/wiki/Howto_compile_the_Linux_Kernel)

[http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization](http://wiki.fragaholics.de/index.php/EN:Linux_Kernel_Optimization)

[http://wiki.fragaholics.de/index.php/EN:Kernel_Configuration_General](http://wiki.fragaholics.de/index.php/EN:Kernel_Configuration_General)

[http://wiki.fragaholics.de/index.php/EN:Linux_Optimization_Guide](http://wiki.fragaholics.de/index.php/EN:Linux_Optimization_Guide)

[URL="https://help.ubuntu.com/community/Kernel/Compile"]https://help.ubuntu.com/community/Kernel/Compile

[https://help.ubuntu.com/community/forum/software/CustomKernel](https://help.ubuntu.com/community/forum/software/CustomKernel)

[/URL][http://manpages.ubuntu.com/manpages/precise/man1/make-kpkg.1.html](http://manpages.ubuntu.com/manpages/precise/man1/make-kpkg.1.html)

---

### Post by matt_symes on 2013-04-18
Hi  > **rootfairy said:**
> hi guys,  i just installed the latest liquorix kernel on my xubuntu 12.10 and i really like it. now, i would like to compile the liquorix kernel myself, but i have absolutely no clue of how to do so. can you provide some help, like guides / tutorials? i found a few but they seem outdated. i really want to get into this stuff and learn about linux. like what packages do i need and what commands do i issue? how do i config the new kernel?  help much appreciated, best regards and thanks in advance  Install the prerequists.  ```
sudo apt-get install build-essential kernel-package libncurses5-dev
```  Download the linux source.  Naivkigate to the source directory and configure the kernel..  ```
sudo make menuconfig
```  Build the kernel deb  ```
sudo CONCURRENCY_LEVEL=2 make-kpkg --initrd --append-to-version=-my-custom kernel-image kernel-headers
```  Install it as you would any deb  ```
sudo dpkg -i 

```  Kind regards

---

### Post by Cheesemill on 2013-04-19
Check out the wiki page...
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

To build the Liquorix kernel instead of the standard Ubuntu kernel you would just have to apply the correct Liquorix patches to the kernel source once you have downloaded it.

---

### Post by rootfairy on 2013-04-20
so i would download the default ubuntu kernel, then apply the liquorix patch and then build it? i absolutely not understand it. where do i download which kernel source?

---

### Post by matt_symes on 2013-04-20
Hi

You get the patches and config from here. Select the config for your arch type.

[http://liquorix.net/sources/](http://liquorix.net/sources/)

Get the kernel sources from here.

[https://www.kernel.org/](https://www.kernel.org/)

You can try the Ubuntu sources but i dont know if their own patches will cause problems or not. Try it and see.

You have inspired me to build it as well.

Kind regards

---

### Post by rootfairy on 2013-04-20
while you are at it, just post a step by step guide and i can finally understand what to do. i have still 0 clue.

---

### Post by matt_symes on 2013-04-20
Hi

Take a look at this thread.

[http://forums.debian.net/viewtopic.php?f=5&t=62069](http://forums.debian.net/viewtopic.php?f=5&t=62069)

I wont get time to build it until tomorrow but i will post back.

Change it for the updated patch.

Kind regards

---

### Post by rootfairy on 2013-04-20
hm, i understand a bit more now. but, if 3.8.8 is latest stable release and liquorix is only for 3.8.6 then i cant use the patch and the config on the kernel 3.8.8? :Z best regards and many thanks

---

### Post by matt_symes on 2013-04-20
Hi

Root around their public file system a bit ;)

[https://www.kernel.org/pub/linux/kernel/v3.x/](https://www.kernel.org/pub/linux/kernel/v3.x/)

Kind regards

---

### Post by rootfairy on 2013-04-20
when i try to patch the 3.8.6 from kernel.org with 3.8.6.1 liquorix i get spammed with this, no matter what i do the patch is permanently interrupted by this notification...

> 

Reversed (or previously applied) patch detected!  Assume -R? [n] Y
Apply anyway? [n] Y



what about this?
> 

biatch@biatchXFCE:~/Downloads/kernel$ sudo apt-get source linux-image-$(uname -r)
[sudo] password for biatch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-liquorix' as source package instead of 'linux-image-3.8-6.dmz.1-liquorix-amd64'
Need to get 85.5 MB of source archives.
Get:1 [http://liquorix.net/debian/](http://liquorix.net/debian/) sid/main linux-liquorix 3.8.0-4 (dsc) [1,585 B]
Get:2 [http://liquorix.net/debian/](http://liquorix.net/debian/) sid/main linux-liquorix 3.8.0-4 (tar) [84.6 MB]
Get:3 [http://liquorix.net/debian/](http://liquorix.net/debian/) sid/main linux-liquorix 3.8.0-4 (diff) [877 kB]
Fetched 85.5 MB in 1min 18s (1,091 kB/s)                                       
dpkg-source: warning: extracting unsigned source package (linux-liquorix_3.8.0-4.dsc)
dpkg-source: info: extracting linux-liquorix in linux-liquorix-3.8.0
dpkg-source: info: unpacking linux-liquorix_3.8.0.orig.tar.bz2
dpkg-source: info: unpacking linux-liquorix_3.8.0-4.debian.tar.bz2
dpkg-source: info: applying zen/3.8.6-1.patch
dpkg-source: info: applying debian/version.patch
dpkg-source: info: applying debian/kernelvariables.patch
dpkg-source: info: applying debian/doc-build-parallel.patch




ok i think i understood the basics. but without knowing all the meanings of all the settings in makeconfig its nearly useless to compile your own kernel isnt it?

---

### Post by matt_symes on 2013-04-20
Hi

No, no, no, it does not work like that. You need to get the kernel source for 3.8.

Follow these step. And you'll have a built kernel (hopefully)

This is an extra step at the start because we'll use fakeroot to build the kernel.

```
sudo apt-get install fakeroot 
```

```

# Create a directory and move into it.
mkdir ~/linux_source && cd !_

# Get the kernel source.
wget https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.8.tar.gz

# Get the patch
wget http://liquorix.net/sources/3.8.6-1.patch.gz

# Get the config ***PICK THE CORRECT ONE FOR YOUR ARCH***
wget http://liquorix.net/sources/3.8/config.amd64 

OR

wget http://liquorix.net/sources/3.8/config.i386

# Extract the source.
tar xvf linux-3.8.tar.gz

# Extract the patch.
gunzip 3.8.6-1.patch.gz

# Move the patch
mv 3.8.6-1.patch linux-3.8

# Move the config
mv config.amd64 linux-3.8/.config

# Move into the directory
cd linux-3.8/

# Patch the kernel
patch -p1 < 3.8.6-1.patch

# Clean up before building.
make-kpkg clean

# Make from the old config. 
# Just let it open and then exit and save it straight away.
make menuconfig.

# Start building
fakeroot make-kpkg --initrd --append-to-version=-liquorix-`date +%Y%m%d` kernel-image kernel-headers
```

I'll be building it later if if i've missed anything i'll update this.

Kind regards

---

### Post by matt_symes on 2013-04-20
Hi

Well i compiled and built it.

```
linux-headers-3.8.6-zen-liquorix-20130420_3.8.6-zen-liquorix-20130420-10.00.Custom_amd64.deb
linux-image-3.8.6-zen-liquorix-20130420_3.8.6-zen-liquorix-20130420-10.00.Custom_amd64.deb
```

So give it a go. 

Post back when you've done it and we'll talk about what we could have done better; if your interested.

Kind regards

---

### Post by rootfairy on 2013-04-22
ok, i believe i succesfully compiled two files, although ive seen some warnings during the compilation.

```


linux-headers-3.8.8-zen-liquorix-20130422_3.8.8-zen-liquorix-20130422-10.00.Custom_amd64.deb
linux-image-3.8.8-zen-liquorix-20130422_3.8.8-zen-liquorix-20130422-10.00.Custom_amd64.deb



```

when i copy the config file to the linux folder, it is not visible. why is that?

```


cp config.amd64 linux-3.8/.config

biatch@biatchXFCE:~/kernel/linux-3.8$ ls
3.8.8-1.patch  drivers   kernel           net             tools
arch           firmware  lib              README          usr
block          fs        MAINTAINERS      REPORTING-BUGS  virt
COPYING        include   Makefile         samples         vmlinux
CREDITS        init      mm               scripts         vmlinux.o
crypto         ipc       modules.builtin  security
debian         Kbuild    modules.order    sound
Documentation  Kconfig   Module.symvers   System.map




```

---

### Post by Cheesemill on 2013-04-22
Anything that begins with a . is a hidden file/folder. You can see hidden files using...
```
ls -a
```

---

### Post by rootfairy on 2013-04-22
wow, thanks. :Z now, that i compiled my own kernel, etc., will it be "faster" or "better" or "different" than the one i download and install from liquorix with ```
 sudo apt-cache search liquorix 
```?

---

### Post by Cheesemill on 2013-04-22
If you didn't make any changes to the config then no, it will be exactly the same.

---

### Post by rootfairy on 2013-04-22
thanks, thats what i was thinking. so, how do i make my kernel actually a better one? i guess by tweaking the myriad settings in makeconfig. how would i figure out which settings i'd need to tweak and which not?

what difference there is between io and cpu scheduler? i seem unable to change the cpu scheduler except in the config?

how much % performance would i gain maximum by tweaking the config really hardcore?

---

### Post by rootfairy on 2013-04-22
at the moment im looking at this website and wonder about the recommendations its making:

[http://wiki.fragaholics.de/index.php/EN:Kernel_Configuration_General](http://wiki.fragaholics.de/index.php/EN:Kernel_Configuration_General)

im looking for maximum perfomance settings for a gaming / desktop computer.

[http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=7](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=7)

---

### Post by matt_symes on 2013-04-22
Hi

Congratulations. You have patched and build your first kernel :D

As i said before, let's talk about what we could have done better.

The first thing we could have done better is actually used the configuration file they supplied.

When we used the command 

```
make menuconfig
```

we overwrote the settings in the original configuration file with some defaults. I wanted to show you menuconfig.

menuconfig is the standard way to edit .config files as it supplies a pretty user interface that is searchable and highly useable. It allows you to edit kernel build parameters in a nice environment. However because we used it when we did we overwrote the configuration supplied by liquorix.

Now to use the configuration file they gave us there is an extra step we need to do.

```
make oldconfig
```

This will take the configuration file they gave us and update the kernel setting. If we then call make menuconfig after that it will have their setting in it.

So we need to build the kernel again. In the steps we ran previously, before we call make menuconfig, we need to call make oldconfig.

You said you wanted to learn how to build a kernel :) Practice makes perfect, so build the kernel again but with that extra step.

After that we'll talk about kernel build parameters if you like.

Kind regards

---

### Post by rootfairy on 2013-04-22
wow, thanks for your answer. i will do that now. but cant i just simply load the liquorix config by selecting load alternative config file and thats it? why do i have to perform make oldconfig?

is there a way to add concurrency_level to 
```

fakeroot make-kpkg --initrd --append-to-version=-liquorix-`date +%Y%m%d` kernel-image kernel-headers

```? maybe its faster then. :D

and what about all these warnings i see when i build the kernel? dont they matter? for example:

```


fs/exec.c: In function &#8216;open_exec&#8217;:
fs/exec.c:778:2: warning: passing argument 1 of &#8216;trace_open_exec&#8217; discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
In file included from fs/exec.c:60:0:
include/trace/events/fs.h:48:1: note: expected &#8216;char *&#8217; but argument is of type &#8216;const char 

[...]

 LD      vmlinux.o
  MODPOST vmlinux.o
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  GEN     .version

[...]

  LD [M]  fs/cachefiles/cachefiles.o
  CC [M]  fs/cifs/cifsfs.o
  CC [M]  fs/cifs/cifssmb.o
fs/cifs/cifssmb.c: In function &#8216;CIFSSMBGetCIFSACL&#8217;:
fs/cifs/cifssmb.c:3686:26: warning: &#8216;pSMB&#8217; may be used uninitialized in this function [-Wmaybe-uninitialized]


```

---

### Post by matt_symes on 2013-04-22
Hi

> **rootfairy said:**
> wow, thanks for your answer. i will do that now. but cant i just simply load the liquorix config by selecting load alternative config file and thats it? why do i have to perform make oldconfig?

:D Sounds like you've been reading up. Try it :) Verify that its contains/does not contain the expected parameters.

> 
is there a way to add concurrency_level to 
```

fakeroot make-kpkg --initrd --append-to-version=-liquorix-`date +%Y%m%d` kernel-image kernel-headers

```? maybe its faster then. :D


Two ways to do that.

```
export CONCURRENCY_LEVEL=2
```

before you call make-kpkg or you can add 

```
fakeroot... CONCURRENCY_LEVEL=2 make-kpkg ......
```

As you've been reading up, you can decide on the concurrency level. Play with different values as you build kernels.

> 
and what about all these warnings i see when i build the kernel? dont they matter? for example:

```


fs/exec.c: In function &#8216;open_exec&#8217;:
fs/exec.c:778:2: warning: passing argument 1 of &#8216;trace_open_exec&#8217; discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
In file included from fs/exec.c:60:0:
include/trace/events/fs.h:48:1: note: expected &#8216;char *&#8217; but argument is of type &#8216;const char 

[...]

 LD      vmlinux.o
  MODPOST vmlinux.o
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  GEN     .version

[...]

  LD [M]  fs/cachefiles/cachefiles.o
  CC [M]  fs/cifs/cifsfs.o
  CC [M]  fs/cifs/cifssmb.o
fs/cifs/cifssmb.c: In function &#8216;CIFSSMBGetCIFSACL&#8217;:
fs/cifs/cifssmb.c:3686:26: warning: &#8216;pSMB&#8217; may be used uninitialized in this function [-Wmaybe-uninitialized]


```

Don worry about them. They for the kernel developers to fix. They are not a problem.

One thing you may want to try and do is to extract one on the kernel debs to see what's inside.

```
dpkg-deb -x <kernel_name> <extract_path>
```

Have a poke around and see what gets generated.

EDIT:

Just thought i'd mention that extracting the deb may be a good way verify your builds using 'load alternative config file' have worked or not, after it's been built.

You can also verify before.

You can also use it to prove to yourself that the first build did not contain the build parameters from the config file from liquorix.

END OF EDIT

You're enthusiasm is great to see :D

Kind regards

---

### Post by rootfairy on 2013-04-22
hm... thank you very much for your answers.

what about this command? i suppose it can create a minimal-config file?

> Since the 2.6.32 kernel, a new feature allows you to  update the configuration to only compile modules that are actually used  in your system: 

```

make localmodconfig
```

so does this mean make recognizes all modules that i currently use and puts them into a config file? so i can save a lot of time by disabling things in menuconfig i dont need?

what is the difference between using concurrency_level and the --jobs argument? why do i have to use make-kpkg and not make? why are there so many ways in linux to do one and the same thing? its so confusing! xZ

WOW! i just installed my own compiled kernels with the 3 changes i mentioned and my system is still working! WOW! :D

now ill try make localmodconfig and see what it does...

---

### Post by matt_symes on 2013-04-22
Hi

> **rootfairy said:**
> hm... thank you very much for your answers.

what about this command? i suppose it can create a minimal-config file?



so does this mean make recognizes all modules that i currently use and puts them into a config file? so i can save a lot of time by disabling things in menuconfig i dont need?


That's exactly what it does. It saves time when creating a config tailored to the hardware in your PC.

I believe it uses lsmod to see what modules currently running. You will still have to tweak the .config file but it gives you a good base.

> 
what is the difference between using concurrency_level and the --jobs argument? 

Nothing really. Setting the CONCURRENCY_LEVEL=X to a value sets an environmental variable. This will get passed to make as -j X. You can set either. They both end up setting the jobs argument. One directly and one indirectly.

> why do i have to use make-kpkg and not make? 

make-kpkg will make a deb file for you that you can install using dpkg. Amongst other things, this makes it easy to uninstall later. You get all the benefits of having the package management system knowing about it.

This is the preferred method.

> why are there so many ways in linux to do one and the same thing? its so confusing! xZ

That's the Linux way. I suggest you concentrate on one method and once you have mastered that try then try other methods.

I may be AFK for most of the day now.

Kind regards

---

### Post by rootfairy on 2013-04-22
ok, thanks. do i have to use make localmodconfig before or after i have applied the patch? :Z and what about cgroups and their scheduling? is it better for perfomance? do you run make-kpkg clean AFTER the making of the config, because it cleans it up?

btw have a nice day :D

when i call make localmodconfig i get:

```

biatch@biatchXFCE:~/kernel2/linux-3.8$ make localmodconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/zconf.lex.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
using config: '/proc/config.gz'
fglrx config not found!!
*
* Restart config...

```

why isnt it getting fglrx? will this be problematic if i install this config? will it remove my current fglrx? also, the config doesnt feature things like scheduler anymore. so will they be missing? the config file size went from 140kb to 87kb, but much is missing. im not sure about this.

my procedure was now like this:
1. extract linux source
2. patch linux source
3. call make localmodconfig
4. call make oldconfig
5. call make menuconfig
6. call make-kpkg clean
7. call build with fakeroot make-kpkg --jobs=2 --initrd --append-to-version=-liquorix-`date +%Y%m%d` kernel-image kernel-headers

was it wrong? guess ill see when i install it now and it f* up my system. :D btw build with 2 jobs is much(!!!) faster.

ok i installed it and it worked, but there appeared a warning that i override an already existing image, like "are you sure what you are doing?" and that some dependencies and files could probably not be properly reconstructed etc., i just continued [forced override install] and it worked, but now i have to reinstall fglrx, which worked too.

and wow, glxgears is working now properly too, maybe due to the reinstallation: it now shows the 3d wheels instead of a spinning cube with the wheels texture on each side.

---

### Post by rootfairy on 2013-04-22
i build another kernel with localmodconfig. but this time, the ati catalyst driver installation fails.

```

First Installation: checking all kernels...
Building for 3.8.8-zen-liquorix-20130422 and 3.8.8-zenliquid
Building for architecture x86_64
Building initial module for 3.8.8-zen-liquorix-20130422
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.8.8-zen-liquorix-20130422 (x86_64)
Consult /var/lib/dkms/fglrx/12.100/build/make.log for more information.

```


```

DKMS make.log for fglrx-12.100 for kernel 3.8.8-zen-liquorix-20130422 (x86_64)
Tue Apr 23 05:06:20 CEST 2013
AMD kernel module generator version 2.1
Error:
kernel includes at /lib/modules/3.8.8-zen-liquorix-20130422/build/include do not match current kernel.
they are versioned as "3.8.8-zen-main"
instead of "3.8.8-zen-liquorix-20130422".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

```

how can i fix this? :Z i already installed a newly compiled kernel and i wont go away. think i messed up.

fixed it with:

[http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

and

[http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/](http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/)

if my systems locks up once on shutdown / reboot after in installed everything [ati catalyst] succesfully before, it doesnt matter, right? or does it still work or configure stuff on shutdown?

---

### Post by rootfairy on 2013-04-26
[solveð]

---

### Post by matt_symes on 2013-04-28
Hi

> **rootfairy said:**
> [solveð]

@rootfairy. I have been pretty busy this week and i have not been able to spend much time on the forums.

It sounds like you have it pretty much under control with the amount you have been reading :).

Keep reading and learning how to compile kernels and what each of the kernel parameters actually do.

Make sure what you read is current and up to date. Some of the best resources are the linux kernel mailing list and [http://lwn.net/](http://lwn.net/).

I'll change the thread prefix to [SOLVED]

Kind regards

---

