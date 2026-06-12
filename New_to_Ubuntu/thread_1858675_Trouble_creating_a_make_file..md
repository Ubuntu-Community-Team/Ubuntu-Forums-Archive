---
title: "Trouble creating a make file."
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Zinja on 2011-10-12
I've got a problem when it comes to creating the makefile for compat-wireless, I have downloaded the package ([http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/10/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/10/)), I am in the right directory, I've been following the information from aircrack-ng wiki ([http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)).

This is the problem when I am creating the make file.

> make -C /lib/modules/2.6.32-34-generic-pae/build M=/home/steven/compat-wireless-2011-10-09 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-34-generic-pae'
  CC [M]  /home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas/if_usb.o
/home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas/if_usb.c:5:1: warning: "pr_fmt" redefined
In file included from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:124,
                 from include/linux/netdevice.h:29,
                 from /home/steven/compat-wireless-2011-10-09/include/linux/compat-2.6.29.h:5,
                 from /home/steven/compat-wireless-2011-10-09/include/linux/compat-2.6.h:24,
                 from <command-line>:0:
include/linux/kernel.h:366:1: warning: this is the location of the previous definition
/home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas/if_usb.c: In function ‘if_usb_suspend’:
/home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas/if_usb.c:1139: error: implicit declaration of function ‘olpc_ec_wakeup_clear’
/home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas/if_usb.c:1141: error: implicit declaration of function ‘olpc_ec_wakeup_set’
make[4]: *** [/home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/steven/compat-wireless-2011-10-09/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/steven/compat-wireless-2011-10-09/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/steven/compat-wireless-2011-10-09] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-34-generic-pae'
make: *** [modules] Error 2


Looks like a horrible error. :(

I just do not have a clue what it's about.

---

### Post by Lisiano on 2011-10-12
Question, are you trying to patch the drivers to support injection or are you trying to compile newer drivers and use them with Ubuntu?
If the later, this command should do the trick
```
sudo apt-get install linux-backports-modules-cw-3.0.0-natty-generic
``` This command will install the Compat Wireless drivers that Ubuntu 11.10 is using. Btw I should thank you since I didn't know the 11.10 CW drivers are available now in Natty (I have a WiFi adapter with N but it fails to work on anything beside 1Mbit/s, 11.10 works ideally and even gives N, also the Master (AP) mode is supported AFAIK)

---

### Post by Zinja on 2011-10-12
I am using ubuntu 10.04, I have tried what you said but it tells me it couldn't find the package.

---

### Post by SeijiSensei on 2011-10-12
The compilation might be failing because you don't have the kernel headers installed.  Try

```
sudo apt-get install linux-headers-something
```

where "something" corresponds to the value returned by the command "uname -r". 

You should have a directory called /usr/src/linux-headers-something/. For instance, I'm running kernel 2.6.35-30-generic and have a /usr/src/linux-headers-2.6.35-30-generic/ directory.

I presume you ran "./configure" before "make".

---

### Post by Lisiano on 2011-10-12
Ah. Then the command is different. I don't remember on top of my head but if no one replies in a while, I might have the time to find out. For the mean time, try opening Synaptic and look for "backports" you want the ones that say wireless or cw AND says it's for generic, not server. The ending probably should be lucid-generic

---

### Post by Zinja on 2011-10-12
> **SeijiSensei said:**
> The compilation might be failing because you don't have the kernel headers installed.  Try

```
sudo apt-get install linux-headers-something
```where "something" corresponds to the value returned by the command "uname -r". 

You should have a directory called /usr/src/linux-headers-something/. For instance, I'm running kernel 2.6.35-30-generic and have a /usr/src/linux-headers-2.6.35-30-generic/ directory.

I presume you ran "./configure" before "make".

I haven't ran ./configure before make, I thought that my wireless card would stop working if I ran that command, well anyway I have two wireless devices (Atheros & ALFA AWUS036NH), would I be able to configure multiple drivers so I could have both of these working? Would I do this with ./configure?

---

### Post by SeijiSensei on 2011-10-12
> **Zinja said:**
> I haven't ran ./configure before make, I thought that my wireless card would stop working if I ran that command

If this is your first attempt at compiling software, you should [read this first]("https://help.ubuntu.com/community/CompilingSoftware#Three_Stages_to_Compiling_Packages").

You're trying to compile additional drivers for the Linux kernel.  That means you need a bunch of header files that correspond to your kernel.  If you have all the prerequisites, you typically then run ./configure.  This is a remarkable program that looks at the source code you need to compile and determines whether you have everything you need.  It also sets up the "build environment" for the software you are compiling.

Compiling software on your machine in no way affects the way the machine is running currently.  Only if you install the compiled software (typically via the "make install" command) might something be changed.  In the case of the Linux kernel, you won't even see the results of your installation unless you reboot.

---

### Post by Zinja on 2011-10-13
I've checked which headers I have on my computer, they are:

linux-headers-2.6.32-33
linux-headers-2.6.32-33-generic
linux-headers-2.6.32-34
linux-headers-2.6.32-34-generic
linux-headers-2.6.32-34-generic-pae

I'm assuming that I would need to install the last header on the list, the others I think were already installed.

---

