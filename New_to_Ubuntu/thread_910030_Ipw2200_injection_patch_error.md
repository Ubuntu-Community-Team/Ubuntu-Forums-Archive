---
title: "Ipw2200 injection patch error"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by newcomer_ on 2008-09-04
Hi all, 
I'm a newbie to Linux/Ubuntu and I've been trying to install the necessary patch for the Aircrack-ng. My Ubuntu dist is the 8.04, the last steps i made are the following:

[I]#patch ipw2200-1.2.1/ipw2200.c ipw2200-1.2.1-inject.patch
#patch ipw2200-1.2.1/Makefile ipw2200-1.2.1-make.patch

now we will remove the old driver then make and install the new one

#cd ipw2200-1.2.2
#sudo ./remove-old[/I]

Then, when I continue with

*#sudo make*

this is the result:
[I]root@noise-laptop:/home/marvin/ipw2200-1.2.2# patch ipw2200.c ipw2200-1.2.2-inject.patch
patching file ipw2200.c
Hunk #1 succeeded at 2017 with fuzz 2 (offset 46 lines).
Hunk #2 succeeded at 11801 (offset 53 lines).
root@noise-laptop:/home/marvin/ipw2200-1.2.2# patch Makefile ipw2200-1.2.2-make.patch
patching file Makefile
root@noise-laptop:/home/marvin/ipw2200-1.2.2# sudo ./remove-old
Checking in /lib/modules/2.6.24-19-generic/build/ for ipw2x00 components...
root@noise-laptop:/home/marvin/ipw2200-1.2.2# sudo make
mkdir -p /home/marvin/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.24-19-generic/build M=/home/marvin/ipw2200-1.2.2 MODVERDIR=/home/marvin/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/marvin/ipw2200-1.2.2/ipw2200.o
/home/marvin/ipw2200-1.2.2/ipw2200.c: In function &#8216;ipw_pci_probe&#8217;:
/home/marvin/ipw2200-1.2.2/ipw2200.c:11998: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
make[2]: *** [/home/marvin/ipw2200-1.2.2/ipw2200.o] Error 1
make[1]: *** [_module_/home/marvin/ipw2200-1.2.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2[/I]

Could you help me please? It's very important and urgent.
Thanks a lot

---

### Post by dtunget on 2008-09-07
home/marvin/ipw2200-1.2.2/ipw2200.c and comment out the line with SET_MODULE_OWNER

it should look something like this now:

SET_MODULE_OWNER

and when you're done:

/*SET_MODULE_OWNER*/

just make sure you catch the whole line.

You should be able to compile properly after that.

---

### Post by newcomer_ on 2008-09-07
Now I'm going to modify the file as you wrote..another question for you..is it necessary to use the backtrack or may i use the ubuntu 8.04 distribution for my purpose?
Thank you!!!

P.S.: I have an Intel 2200BG wifi

---

