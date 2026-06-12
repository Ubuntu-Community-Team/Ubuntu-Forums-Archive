---
title: "Cell support in linux; how?"
date: 2006-10-31
forum: Programming Talk
---

### Post by kcy29581 on 2006-10-31
Hi all,

I just downloaded the latest kernel from [www.kernel.org]("http://www.kernel.org") (2.6.18.1), just so I can see if the option to support Cell processors in there; I believe the kernel officially supports cell since 2.6.16.

However, I cannot see how Cell is supported! i.e. I have no clue what specific options via make menuconfig (or xconfig) need to be enabled.


Anyone out there know? Do I still need patches for Cell to work?

---

### Post by amo-ej1 on 2006-10-31
offcourse the question that i'm obligated to ask you is, where did you get one ;) 

But on the other hand: [http://www.bsc.es/projects/deepcomputing/linuxoncell/](http://www.bsc.es/projects/deepcomputing/linuxoncell/) there you can find a fc5 install image. 
Since i haven't got such a toy myself yet, I would initially try to fiddle around in the ppc64 branch, since the cell processor is mainly a ppc64 cpu with 8 SPE's around it ...

But I did some grepping and found:

```

e@lap:/usr/src/linux-2.6.17.11$ fgrep -r PPC_CELL *
arch/powerpc/configs/maple_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/configs/cell_defconfig:CONFIG_PPC_CELL=y
arch/powerpc/configs/g5_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/configs/pseries_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/configs/ppc64_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/platforms/cell/Kconfig:    depends on PPC_CELL
arch/powerpc/platforms/cell/Kconfig:    depends on PPC_CELL
arch/powerpc/platforms/Makefile:obj-$(CONFIG_PPC_CELL)          += cell/
arch/powerpc/Kconfig:config PPC_CELL
arch/powerpc/Kconfig:   depends on PPC_CELL
drivers/net/Kconfig:    depends on PCI && PPC_CELL

```

So it's only a matter of fiddling around, and now, where did you get the goodies ? ;)

---

### Post by kcy29581 on 2006-10-31
> **amo-ej1 said:**
> offcourse the question that i'm obligated to ask you is, where did you get one ;) 

But on the other hand: [http://www.bsc.es/projects/deepcomputing/linuxoncell/](http://www.bsc.es/projects/deepcomputing/linuxoncell/) there you can find a fc5 install image. 
Since i haven't got such a toy myself yet, I would initially try to fiddle around in the ppc64 branch, since the cell processor is mainly a ppc64 cpu with 8 SPE's around it ...

But I did some grepping and found:

```

e@lap:/usr/src/linux-2.6.17.11$ fgrep -r PPC_CELL *
arch/powerpc/configs/maple_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/configs/cell_defconfig:CONFIG_PPC_CELL=y
arch/powerpc/configs/g5_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/configs/pseries_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/configs/ppc64_defconfig:# CONFIG_PPC_CELL is not set
arch/powerpc/platforms/cell/Kconfig:    depends on PPC_CELL
arch/powerpc/platforms/cell/Kconfig:    depends on PPC_CELL
arch/powerpc/platforms/Makefile:obj-$(CONFIG_PPC_CELL)          += cell/
arch/powerpc/Kconfig:config PPC_CELL
arch/powerpc/Kconfig:   depends on PPC_CELL
drivers/net/Kconfig:    depends on PCI && PPC_CELL

```So it's only a matter of fiddling around, and now, where did you get the goodies ? ;)
mwahahahaha!!! I will never tell!

Seriously now, :), I work at a games company and I have my own lovely PS3 to play with. Hopefully one day I can get Ubuntu working on it!

On the issue, how do I get to the ppc branch in xconfig? I can't seem to see it in the "Processor type and features" part, neither in "Subarchitecture Type" nor in the "Processor Family". I did this in Gentoo ages ago, I know I'm missing something noobish...

---

### Post by Dual Cortex on 2006-10-31
> **kcy29581 said:**
> mwahahahaha!!! I will never tell!

Seriously now, :), I work at a games company and I have my own lovely PS3 to play with. Hopefully one day I can get Ubuntu working on it!

On the issue, how do I get to the ppc branch in xconfig? I can't seem to see it in the "Processor type and features" part, neither in "Subarchitecture Type" nor in the "Processor Family". I did this in Gentoo ages ago, I know I'm missing something noobish...

Nice, that sounds pretty cool. About 2 weeks ago Sony+Terrasfot announced that the PS3 support Yellow Dog Linux.

---

### Post by kcy29581 on 2006-10-31
> **Dual Cortex said:**
> Nice, that sounds pretty cool. About 2 weeks ago Sony+Terrasfot announced that the PS3 support Yellow Dog Linux.
I know; I'm trying to find out how exactly (i.e. what kernel they are using, patches, etc). Hopefully it's not toooooo hard!

---

### Post by amo-ej1 on 2006-10-31
Okay, now I envy you :(

Well you'll need some crosscompilation set up, it is described for example at [http://infolinux.de/ppc/](http://infolinux.de/ppc/)

but basicly, in order to get a config right you should do something like

```

edb@lapedb:/usr/src/linux-2.6.17.11$ cp Makefile Makefile.prev
edb@lapedb:/usr/src/linux-2.6.17.11$ emacs Makefile
edb@lapedb:/usr/src/linux-2.6.17.11$ diff Makefile Makefile.prev 
175,176c175,176
< ARCH          := powerpc
< CROSS_COMPILE := powerpc-linux-
---
> ARCH          ?= $(SUBARCH)
> CROSS_COMPILE ?=

```

that will get you the powerpc arch and a make menuconfig will get you the ability to select: "Platform support" -> "Cell broadband processor architecture", and in order to set this select the first option in the main menu '64 bit kernel support'

```

Symbol: PPC_CELL [=y]                                                                                                                                                                                                          
Prompt:   Cell Broadband Processor Architecture                                                                                                                                                                                
Defined at arch/powerpc/Kconfig:393                                                                                                                                                                                           
Depends on: (PPC64 || CLASSIC32) && PPC_MULTIPLATFORM && PPC64                                                                                                                                                                
Location:                                                                                                                                                                                                                     
-> Platform support                                                                                                                                                                                                         
Selects: PPC_RTAS && MMIO_NVRAM && PPC_UDBG_16550     

```


(But you will also need a crosscompiler setup in order to have it compiled).

If you have some gory details keep em coming ;)
Btw weren't there rumors the ps3 would be running linux by default as firmware ? or at least a 'sortof' version of it ? 

Can't wait to get my hands on one of them myself but the launch in europe has been postponed ](*,)

---

### Post by amo-ej1 on 2006-10-31
[http://www.terrasoftsolutions.com/products/faq/ps3-general.shtml](http://www.terrasoftsolutions.com/products/faq/ps3-general.shtml)  states some info about the ydl / ps3 combo, guess it looks way more mature than the PS2 linux version however the ps2 linux version offered a lot of technical documentation while that will seem to be missing here :(

but ydl will provide their packages and sources in the public domain so any patch they will apply will be available so that won't be an issue. which also means it won't be extremely difficult to get something else, say ubutnu, running on there ;)

---

### Post by kcy29581 on 2006-10-31
> **amo-ej1 said:**
> [http://www.terrasoftsolutions.com/products/faq/ps3-general.shtml](http://www.terrasoftsolutions.com/products/faq/ps3-general.shtml)  states some info about the ydl / ps3 combo, guess it looks way more mature than the PS2 linux version however the ps2 linux version offered a lot of technical documentation while that will seem to be missing here :(

but ydl will provide their packages and sources in the public domain so any patch they will apply will be available so that won't be an issue. which also means it won't be extremely difficult to get something else, say ubutnu, running on there ;)thanks for all the help, if I can get this running you'll be the first to know!

About the firmware and linux, so far all we can see is the actual official frontend (looks almost exactly like the PSP menu); not sure if Linux is running underneath it, and I can't see a direct way of "bootloading".

However, there is an option to format and repartition the hard drive; whether or not this is just for test kits I don't know.

Once again, thanks for the help, but another question if I may: how did you know how to "switch" the kernel compiling to powerpc? I want to learn as much as possible about Linux, soooo how did you know that? It has to be in the kernel docs somewhere and I'm missing it.

---

### Post by amo-ej1 on 2006-11-01
Hehe,

well if you ever played with linux on multiple architectures, e.g. on a slow alpha or on a slow sun and you want to compile your own kernel, the make menuconfig shows you only questions on your current cpu so when you want to compile a kernel for a slow machine you are obligated to a) wait for too much in in order to see it fail in the last 5% ;-) b) setup some cross compilation and having to figure out the above, so I figured out the above 

But keep us posted if you encounter some nice thingies ;) but since the gameos is behaving like a firmware i doubt the it will contain something linux-y

---

### Post by kcy29581 on 2006-11-20
UPDATE: Now Sony have released the bootloader for the PS3, it's play time!

It seems the PS3 boots into a very basic command line linux; you can use a command called "kboot" in order to boot Linux (Fedora Core 5 installation, for example).

In order to get Ubuntu on here, I need to be able to install Ubuntu once the PS3 has booted. Situation is:

 - The PS3 boots up now, and stops at a Linux prompt and shows:
     kboot:
 - Is there a way to start Ubuntu's installation from the command line? Because the system will not boot cd's.

If anyone can help, great!

amo-ej1: I can get Fedora Core 5 installed on this thing (command line so far), but bloody Fedora has a bug, where you cannot install from media AFTER installing... It's also present in FC6 as well...
When I get Ubuntu working on this, I'll post screenshots!

---

### Post by amo-ej1 on 2006-11-20
Hehe i was thinking about it today, this morning i read a slashdot post about running fc5 on ps3: [http://games.slashdot.org/games/06/11/20/0313222.shtml](http://games.slashdot.org/games/06/11/20/0313222.shtml)  unfortunately the person doesn't know what he's talking about he's talking **** about compiling a kernel while it's simply loading and nagging about 'loading drivers' whil it's simply launching daemons after that i stopped listening and turned my sound off ;-)

As for fedora you have no network connectivity ? and you probably can't access the blu ray drive yet ? Can't you hook anything else up ? usb devices etc ?

---

### Post by kcy29581 on 2006-11-20
> **amo-ej1 said:**
> Hehe i was thinking about it today, this morning i read a slashdot post about running fc5 on ps3: [http://games.slashdot.org/games/06/11/20/0313222.shtml](http://games.slashdot.org/games/06/11/20/0313222.shtml)  unfortunately the person doesn't know what he's talking about he's talking **** about compiling a kernel while it's simply loading and nagging about 'loading drivers' whil it's simply launching daemons after that i stopped listening and turned my sound off ;-)

As for fedora you have no network connectivity ? and you probably can't access the blu ray drive yet ? Can't you hook anything else up ? usb devices etc ?
No network connectivity, but that could be due to me using FC6 rather than FC5, as suggested. If I knew which module I was supposed to load...
I can access the blu-ray drive! :), and it seems like the usb ports fully work.

I wish I could just "boot" the Ubuntu cd from this darn command line...

---

### Post by amo-ej1 on 2006-11-20
what is the output of lspci and lspci -v i guess we'll be able to find the module name from there ;)

---

### Post by kcy29581 on 2006-11-20
> **amo-ej1 said:**
> what is the output of lspci and lspci -v i guess we'll be able to find the module name from there ;)my bad: works fine with FC5! Gnome up and running nicely :)

I'm trying to find a way at work to get hi-def screenshots, rather than crappy standard definition shots.

---

### Post by amo-ej1 on 2006-11-21
nevertheless i'm still interested in a lspci, lspci -v, cat /proc/cpuinfo outputs ;-)

argl, stupid sony i want my own ps3 :'(

---

### Post by kcy29581 on 2006-11-22
amo-ej1:

I'm about to try and get Ubuntu on this by modifying the kernel on the Ubuntu CD. Before I do, here's the output of the commands you'd like to see:

```
lspci
00:01.0 USB Controller: Toshiba America Unknown device 01b6 (rev 01)
00:01.1 USB Controller: Toshiba America Unknown device 01b5 (rev 01)
00:02.0 USB Controller: Toshiba America Unknown device 01b6 (rev 01)
00:02.1 USB Controller: Toshiba America Unknown device 01b5 (rev 01)

```

```

lspci -v
00:01.0 USB Controller: Toshiba America Unknown device 01b6 (rev 01) (prog-if 10 [OHCI])
        Flags: fast devsel, IRQ 16
        [virtual] Memory at 4000001a0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2

00:01.1 USB Controller: Toshiba America Unknown device 01b5 (rev 01) (prog-if 20 [EHCI])
        Flags: fast devsel, IRQ 10
        [virtual] Memory at 4000001b0000 (32-bit, non-prefetchable) [disabled] [size=64K]

00:02.0 USB Controller: Toshiba America Unknown device 01b6 (rev 01) (prog-if 10 [OHCI])
        Flags: fast devsel, IRQ 17
        [virtual] Memory at 4000001c0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [dc] Power Management version 2

00:02.1 USB Controller: Toshiba America Unknown device 01b5 (rev 01) (prog-if 20 [EHCI])
        Flags: fast devsel, IRQ 11
        [virtual] Memory at 4000001d0000 (32-bit, non-prefetchable) [disabled] [size=64K]

```

```

cat /proc/cpuinfo
processor       : 0
cpu             : Cell Broadband Engine, altivec supported
clock           : 3192.000000MHz
revision        : 5.1 (pvr 0070 0501)

processor       : 1
cpu             : Cell Broadband Engine, altivec supported
clock           : 3192.000000MHz
revision        : 5.1 (pvr 0070 0501)

timebase        : 79800000
machine         : PS3PF

```


May I suggest you take a look at [http://ps3.qj.net]("http://ps3.qj.net/")? Lots of topics to read up there.

I know you can only see 2 cores for now; apparently with SPU development tools you should be able to access the other cores.

Hope this helps. :)

---

### Post by Yogarine on 2006-11-22
I believe you need to prepare a special kboot image specifically for Ubuntu, and prepare Ubuntu with a patched Linux 2.6.19 kernel so it supports the Cell and PS3 hardware. (Actually, Linux on the PS3 runs virtualized, so the patch also contains drivers for the virtualized hardware.) I wish I had a PS3 to try it out.

I've created a spec that covers making PS3 compatible with the Cell out-of-the-box. Basicly everything I discovered about running Ubuntu on the PS3 is written down in the spec's wiki page: [https://wiki.ubuntu.com/PS3Compatibility](https://wiki.ubuntu.com/PS3Compatibility). Check it out, it contains links to the patches and some very informative documentation.

And make sure you write up new discoveries there. ;-)

---

