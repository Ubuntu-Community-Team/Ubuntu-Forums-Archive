---
title: "Another wifi question"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by tysonh on 2008-06-12
I have a wifi card that according to various sources doesn't work very well with ubuntu.  I have a new wifi card coming in the mail but I still want a shot at solving this problem.

I followed a how to from the forum but I got stuck.  In the read me file that came with the driver it says:

To compile the driver simply run make.

Note that the Makefile should work on kenrel 2.6 and 2.4. 
Anyway the old Makefile for 2.6 kernel is still included as Makefile26.

FOUR modules will be compiled: the ieee802.11 stack (3 modules) and the driver 
itself. You need to insmod ALL of them!

Here's my first problem.  I don't how or what run make means.

After this it says:

After insmod'ing ieee80211-r8180_crypt-r8180 ieee80211_crypt_wep-r8180 ieee80211-r8180.ko and r8180
the nic is sleeping.

Again I'm not sure what insmod is or what it does.  But I know from reading the instructions that "make" command or functions is supposed to combined file into four modules.(i think)

Then after I have the four modules insmod comes in somehow and then I can begin to compile a driver I guess.

So basically I need to know how to use make correctly.  In the driver download file there are files named "Makefile" but I don't know how to use them.

thanks in advance..........sorry for the long post

Oh and my wifi card is a netgear ma521

---

### Post by tysonh on 2008-06-12
I navigated to the driver folder and once in the folder I just typed in make with nothing else.  I thought it was working until I start seeing error codes.

Heres the output:

make -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/war/Desktop/rtl8180-0.21 MODVERDIR=/home/war/Desktop/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
scripts/Makefile.build:41: /home/war/Desktop/rtl8180-0.21/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/war/Desktop/rtl8180-0.21/Makefile'.  Stop.
make[1]: *** [_module_/home/war/Desktop/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [2.6] Error 2

no clue what any of this means.

---

