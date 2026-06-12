---
title: "HOWTO: Install vmware under your ubuntu"
date: 2005-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by i3dmaster on 2005-05-25
Wouldn't be nice if we can play diff OSs under ubuntu? Yes, that will have a lot of fun... I just tried install the latest VMware workstation 5 under ubuntu and it went pretty successfully (well, I did some researches beforehands). So I am gonna share it with everyone here.

1. Since VMware does not support any of the current Hoary kernels (2.6.10-x), you will have to build the vmware modules during the installation, so there are something you have to load before you start installing Vmware.
a. build-essential (apt-get install build-essential). It gives you all the compiling tools that you MUST need.
b. linux-source (apt-get install linux-source-xxx). For instance, mine is 2.6.10 for my running kernel 2.6.10-5-686
c. linux-headers (apt-get install linux-headers-xxx). For instance, mine is 2.6.10-5-686.
Anyway, just search apt repos for the headhers, source for your running kernel.

2. the kernel source does not get installed after you apt-get, so you will need to go to the /usr/src dir and manually untar it. After you get the directory, then do "ln -sf you_linux_source_dir linux". This will create a symblic link named "linux" under the same dir.

3. Once you have them loaded, go to [www.vmware.com](www.vmware.com) to download the vmware 5 code (version 13124 is the latest). I recommend the tar.gz format since it has a nice installation perl script.

3. gunzip and untar it, it will have a vmware-distrib directory generated, go to that dir and run the vmware-install.pl script. 

4. Follow the instructions and take pretty much all default settings (as long as you don't make any customized changes on the previous installations, header files location, source location, etc will all be in the default places)

Hopefully, the installation script will build the kernel modules without any problem (it normally shouldn't), if so,  congratulations! You have Vmware available on your ubnutu now. you can just do "vmware" to bring up the GUI and install whatever OSs you like in there... 

A comment is when you setup the virtual network interfaces during the installation process, make sure you bridge the right NIC card to the virtual interface. The default is "eth0" but you might want to make sure you do have "eth0"...

Have fun...

---

### Post by mrbass on 2005-05-25
In my experience installing vmare 5.0 all I needed to install was linux-headers and gcc ...not build-essentials, etc.

 Install VMWare 5.0

uname -a
Linux hostname 2.6.10-5-386

sudo apt-cache search headers 2.6.10-5-386
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386

sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc

Now your ready to install VMWare with the script

---

### Post by nehalem on 2005-05-25
The big question for me is how do you get sound to work for multiple VM's?  It is possible to use ESD or soemthing rather than OSS?

Plus the sound stutters?  I think I read this is just a problem with VMware but I would be interested if a solution exists.

---

### Post by i3dmaster on 2005-05-25
[QUOTE=mrbass]In my experience installing vmare 5.0 all I needed to install was linux-headers and gcc ...not build-essentials, etc.

 Install VMWare 5.0

uname -a
Linux hostname 2.6.10-5-386

sudo apt-cache search headers 2.6.10-5-386
linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386

sudo apt-get install linux-headers-2.6.10-5-386
sudo apt-get install gcc

Now your ready to install VMWare with the script[/QUOTE]

Cool, thanks for sharing. So you don't need the linux source tree to build the modules?

---

### Post by pdk001 on 2005-05-25
thanks for a tip
i will try it now

---

### Post by kb00heda on 2005-05-26
I tried this yesterday and it all worked out fine: registered at VMware's homepage, got the evaluation license per mail, downloaded and installed vmvare using the perl script (after making sure the linux-headers were present --- installed those via apt).

I must say it was mixed feelings to once again see Windows running on my machine (though as a VM)...! This was as easy as mount my Windows CD, power on the newly created VM, and install as usual. Guess I could have made some tweaking to it, but was content with making sure I could install and run Windows software.

In short: VMware is a nice thing really. However, having no urgent need for running Windows applications, in the end I uninstalled it. Sometimes it is just fun to test new things!

---

### Post by i3dmaster on 2005-05-26
[QUOTE=kb00heda]I tried this yesterday and it all worked out fine: registered at VMware's homepage, got the evaluation license per mail, downloaded and installed vmvare using the perl script (after making sure the linux-headers were present --- installed those via apt).

I must say it was mixed feelings to once again see Windows running on my machine (though as a VM)...! This was as easy as mount my Windows CD, power on the newly created VM, and install as usual. Guess I could have made some tweaking to it, but was content with making sure I could install and run Windows software.

In short: VMware is a nice thing really. However, having no urgent need for running Windows applications, in the end I uninstalled it. Sometimes it is just fun to test new things![/QUOTE]

exactly. It's a very neat tool for testing purpose since the stuff you put in the guest OS will never mess up your native host.

---

### Post by Fab on 2005-05-27
okay
i downloaded the tar from the vmware site
there was no vmware-installer.pl file in it
i tried a second and a third time
no vmware-installer.pl in it
i got a friend to download it - nada
finally got the file from a friend who had vmware installed already from a previous release
ran it - worked fine
vmware-config.pl is called afterwards
fine till the part with the kernel modules:
> Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Gehe in Verzeichnis »/tmp/vmware-config1/vmmon-only«
make -C /usr/src/linux/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.10-5-686«
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In Datei, eingefügt von /tmp/vmware-config1/vmmon-only/linux/driver.c:45:
/tmp/vmware-config1/vmmon-only/linux/driver.h:68:1: Warnung: »DEVICE_NAME_SIZE« redefiniert
In Datei, eingefügt von include/linux/miscdevice.h:5,
                    von /tmp/vmware-config1/vmmon-only/linux/driver.h:12,
                    von /tmp/vmware-config1/vmmon-only/linux/driver.c:45:
include/linux/device.h:25:1: Warnung: dies ist die Stelle der vorherigen Definit ion
objdump: /tmp/vmware-config1/vmmon-only/linux/.tmp_driver.o: File format not rec ognized
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
In Datei, eingefügt von /tmp/vmware-config1/vmmon-only/linux/hostif.c:57:
/tmp/vmware-config1/vmmon-only/linux/driver.h:68:1: Warnung: »DEVICE_NAME_SIZE« redefiniert
In Datei, eingefügt von include/linux/miscdevice.h:5,
                    von /tmp/vmware-config1/vmmon-only/linux/driver.h:12,
                    von /tmp/vmware-config1/vmmon-only/linux/hostif.c:57:
include/linux/device.h:25:1: Warnung: dies ist die Stelle der vorherigen Definit ion
objdump: /tmp/vmware-config1/vmmon-only/linux/.tmp_hostif.o: File format not rec ognized
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
objdump: /tmp/vmware-config1/vmmon-only/common/.tmp_cpuid.o: File format not rec ognized
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
objdump: /tmp/vmware-config1/vmmon-only/common/.tmp_hash.o: File format not reco gnized
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
objdump: /tmp/vmware-config1/vmmon-only/common/.tmp_memtrack.o: File format not recognized
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
objdump: /tmp/vmware-config1/vmmon-only/common/.tmp_phystrack.o: File format not  recognized
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
objdump: /tmp/vmware-config1/vmmon-only/common/.tmp_task.o: File format not reco gnized
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
objdump: /tmp/vmware-config1/vmmon-only/common/.tmp_vmx86.o: File format not rec ognized
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
objdump: /tmp/vmware-config1/vmmon-only/vmcore/.tmp_moduleloop.o: File format no t recognized
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
/tmp/vmware-config1/vmmon-only/linux/driver.o: file not recognized: File format not recognized
make[2]: *** [/tmp/vmware-config1/vmmon-only/vmmon.o] Fehler 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Fehler 2
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-5-686«
make: *** [vmmon.ko] Fehler 2
make: Verlasse Verzeichnis »/tmp/vmware-config1/vmmon-only«
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


what did i do wrong?
i symlinked the most recent 686 kernel headers to /usr/src/linux/  , since that is what i use
:(
i really want to try this

Fab

---

### Post by #Vizc@ch@ on 2005-05-27
But the default is /usr/src/linux/include not /usr/src/linux, that might be the problem.

You should make sure where the headers are.

Note: I may be talking nonsense  :-? 

Good luck

---

### Post by Fab on 2005-05-27
[QUOTE=#Vizc@ch@]But the default is /usr/src/linux/include not /usr/src/linux, that might be the problem.

You should make sure where the headers are.

Note: I may be talking nonsense  :-? 

Good luck[/QUOTE]
 nope, the files needed are in /usr/src/linux/include
the thing that bothers me is the stuff with file format not recognized, i think the key lies within that..

---

### Post by pdk001 on 2005-05-27
it doesn't work for me (-__-;;)

---

### Post by benplaut on 2005-05-30
[quote="vmware installer"]sudo /home/ben/vmware-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.
[/quote]

it hates me...

i have tried to install it soo many times, and it always fails  ](*,)

---

### Post by maltje on 2005-06-23
I installed it without problems,but now I want to install XP on the machine.
When I start the "new machine" there is coming a window with "tip" and then everything "holds"
I make a virtual disk of 7 Gig's.
MAybe this is to smal for XP????
HElp please.

---

### Post by arnieboy on 2005-06-23
7 GB isnt small for windows XP...

---

### Post by Quest-Master on 2005-06-23
> The path "/usr/src/linux" is an existing directory, but it does not contain at
least one of these directories "linux", "asm", "net" as expected.


I keep on getting this, though I've tried /usr/src, /usr/src/linux, and /usr/src/linux/include. ><

---

### Post by Nightblade on 2005-06-25
[QUOTE=Quest-Master]I keep on getting this, though I've tried /usr/src, /usr/src/linux, and /usr/src/linux/include. ><[/QUOTE]
Yeah I get that too... Really annoying.

---

### Post by i3dmaster on 2005-06-25
[QUOTE=Nightblade]Yeah I get that too... Really annoying.[/QUOTE]

You will need to install the linux headers packages for your running kernel. under /lib/modules/your_kernel_version/, make sure there is a build symlink points to /usr/src/linux-headers-kernel-version. Also gcc will need to be the same version of the one for building the kernels.

---

### Post by i3dmaster on 2005-06-25
[QUOTE=benplaut]it hates me...

i have tried to install it soo many times, and it always fails  ](*,)[/QUOTE]

you seems running it NOT on the installation dir. Look carefully, it tries to find the ./installer/service.sh, so you will need to run it from the vmware-distrib dir.

---

### Post by i3dmaster on 2005-06-25
[QUOTE=pdk001]it doesn't work for me (-__-;;)[/QUOTE]

ok, but why?

---

### Post by i3dmaster on 2005-06-25
[QUOTE=Fab]okay
i downloaded the tar from the vmware site
there was no vmware-installer.pl file in it
i tried a second and a third time
no vmware-installer.pl in it
i got a friend to download it - nada
finally got the file from a friend who had vmware installed already from a previous release
ran it - worked fine
vmware-config.pl is called afterwards
fine till the part with the kernel modules:


what did i do wrong?
i symlinked the most recent 686 kernel headers to /usr/src/linux/  , since that is what i use
:(
i really want to try this

Fab[/QUOTE]

Once you apt-get install your running kernel headers pkg, it should work without any problem. No need to manually link anything. Underneath /lib/modules/your-kernel-version, there is a "build" symlink points to your header dir, that's all you need.

---

### Post by Fab on 2005-06-25
[QUOTE=i3dmaster]Once you apt-get install your running kernel headers pkg, it should work without any problem. No need to manually link anything. Underneath /lib/modules/your-kernel-version, there is a "build" symlink points to your header dir, that's all you need.[/QUOTE]

I just wanted to say it seems it worked this time (configuring atm). The same setup, same packages, but i downloaded the package again today and this time, the installer file was there, and somehow, it chose the path you mentioned and not the one the other one chose (/usr/source/linux/include)
anyway, back to some configureing now ;P

---

### Post by Quest-Master on 2005-06-25
> Underneath /lib/modules/your-kernel-version, there is a "build" symlink points to your header dir, that's all you need.

Can someone explain how to do this? :\

---

### Post by i3dmaster on 2005-06-25
[QUOTE=Quest-Master]Can someone explain how to do this? :\[/QUOTE]

apt-get install your running kernel's header pkg is all you need. Once you get the header pkg installed, it will make the link automatically.

---

### Post by Quest-Master on 2005-06-25
[QUOTE=i3dmaster]apt-get install your running kernel's header pkg is all you need. Once you get the header pkg installed, it will make the link automatically.[/QUOTE]
 
Didn't work.

---

### Post by i3dmaster on 2005-06-25
[QUOTE=Quest-Master]Didn't work.[/QUOTE]
Hmm... that's weird. but you should still be able to do it manually by 
```

ln -sf /usr/src/linux-headers-your-kernel-version /lib/modules/your-kernel-version/build

```
Make sure you do have the linux-headers-your-kernel-version pkg installed.

---

### Post by Quest-Master on 2005-06-26
[QUOTE=i3dmaster]Hmm... that's weird. but you should still be able to do it manually by 
```

ln -sf /usr/src/linux-headers-your-kernel-version /lib/modules/your-kernel-version/build

```
Make sure you do have the linux-headers-your-kernel-version pkg installed.[/QUOTE]
 
Still doesn't work. I just keep getting the same error over and over again.

---

### Post by i3dmaster on 2005-06-27
[QUOTE=Quest-Master]Still doesn't work. I just keep getting the same error over and over again.[/QUOTE]

Hmm... you really got me there. I've never seen this type of issue before. I wonder if you can remove the header pkg and reinstall it again. Then make sure that the build symlink is auto created by the installation process. After that, you run the vmware install pl script again and see what you get...

---

### Post by Quest-Master on 2005-06-27
It appears that my kernel was still 2.6.10-4 back from Warty.. wasn't upgraded to -5 for some reason. I upgraded it, and now my X is dead.

Will have to sort that out now before VMware. :P

---

### Post by i3dmaster on 2005-06-27
[QUOTE=Quest-Master]It appears that my kernel was still 2.6.10-4 back from Warty.. wasn't upgraded to -5 for some reason. I upgraded it, and now my X is dead.

Will have to sort that out now before VMware. :P[/QUOTE]

ok, well its not good... but at least found out something...

---

### Post by uberlinux on 2005-07-13
I tried all the same stuff, no luck...   same error...

---

### Post by cutOff on 2005-07-18
That's really nice! Works pretty fine here.

Thanks a lot for this  :grin:

Btw I'd recommend to install VMware Tools.

---

### Post by UbuWu on 2005-07-20
Works great! But installing windows is a pain in the ass... I think it already has downloaded more than 100mb by now for updates and service packs. And I have  rebooted my virtual machine now for at least three times. Now trying deer park under windows, I like the fast back and forward. And ironically, openoffice seems to start faster in windows on the virtual machine than it does on ubuntu hoary...  :???:

---

### Post by keltong on 2005-07-22
I try to install the header file and the gcc and was told my is up to date. So went on to install VMware but fail. I'm a linux and ubuntu newbie. Hope you can help me.

> Trying to find a suitable vmmon module for your running kernel.

None of VMware Workstation's pre-built vmmon modules is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.10-5-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.10-5-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:41:
/tmp/vmware-config1/vmmon-only/linux/driver.h:66:1: warning: "DEVICE_NAME_SIZE" redefined
In file included from include/linux/miscdevice.h:5,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:12,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:41:
include/linux/device.h:25:1: warning: this is the location of the previous definition
/tmp/vmware-config1/vmmon-only/linux/driver.c:133: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:137: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function `Panic':
/tmp/vmware-config1/vmmon-only/linux/driver.c:1881: warning: implicit declaration of function `_exit'
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:41:
/tmp/vmware-config1/vmmon-only/linux/driver.h:66:1: warning: "DEVICE_NAME_SIZE" redefined
In file included from include/linux/miscdevice.h:5,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:12,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:41:
include/linux/device.h:25:1: warning: this is the location of the previous definition
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config1/vmmon-only/linux/hostif.c:57:
/tmp/vmware-config1/vmmon-only/linux/driver.h:66:1: warning: "DEVICE_NAME_SIZE" redefined
In file included from include/linux/miscdevice.h:5,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:12,
                 from /tmp/vmware-config1/vmmon-only/linux/hostif.c:57:
include/linux/device.h:25:1: warning: this is the location of the previous definition
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
*** Warning: "_exit" [/tmp/vmware-config1/vmmon-only/vmmon.ko] undefined!
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmmon.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by keltong on 2005-07-22
BTW I'm trying to install VMware Ver 4.5

---

### Post by i3dmaster on 2005-07-24
> 
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel. You may want to
rebuild a kernel based on that directory, or specify another directory.

use uname -a to see your running kernel. From the error message, looks like the header file version and your running kernel version is different...

---

### Post by petasques on 2005-08-13
mrbass simple few lines worked perfectly for my kubuntu 5.04! thanks!

...now going to try how does vmware its work, need different virtual machines for different developer profiles :)

---

### Post by -deadcats on 2005-08-14
Don't know if this will work in Ubuntu, but it works with SuSE:

cd /usr/src/linux
make cloneconfig
make modules_prepare

That should take care of the symbolic links, etcetera.  Good luck! :)

-dc

---

