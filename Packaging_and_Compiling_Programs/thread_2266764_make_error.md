---
title: "make error"
date: 2015-02-25
forum: Packaging and Compiling Programs
---

### Post by zkab on 2015-02-25
I am trying to install Digital Devices Cine S2 V6.5 according to [http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner](http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner).
I have Ubuntu server 64-bits 14.10 (uname -r gives 3.16.0-30-generic)

During make I get this error:

rajan@tv-server:~/v4l-dvb$ sudo make
make -C /home/rajan/v4l-dvb/v4l 
make[1]: Entering directory '/home/rajan/v4l-dvb/v4l'
No version yet, using 3.16.0-30-generic
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 3.6.0
File not found: /lib/modules/3.6.0-30-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
Updating/Creating .config
Preparing to compile for kernel version 3.6.0
File not found: /lib/modules/3.6.0-30-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target '.config', needed by '.myconfig'.  Stop.
make[1]: Leaving directory '/home/rajan/v4l-dvb/v4l'
Makefile:27: recipe for target 'all' failed
make: *** [all] Error 2
rajan@tv-server:~/v4l-dvb$ 

I have file 3.16.0-30-generic and not 3.6.0-30-generic in /lib/modules/
How can it be fixed ?

---

### Post by oldos2er on 2015-02-25
Moved to Packaging & Compiling Programs.

---

