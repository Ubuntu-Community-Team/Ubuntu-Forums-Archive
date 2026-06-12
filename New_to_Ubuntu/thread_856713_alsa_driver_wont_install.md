---
title: "alsa driver wont install"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Kedster on 2008-07-11
```
harry@harry-laptop:~$ cd /home/harry/Desktop/alsa-driver-1.0.16
harry@harry-laptop:~/Desktop/alsa-driver-1.0.16$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/harry/Desktop/alsa-driver-1.0.16
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

---

### Post by PriceChild on 2008-07-11
Why do you think you need to do this?

---

### Post by Kedster on 2008-07-12
i had no sound at all and like tha volume controller had the mute sign on it all the time and when i would click on it would give an error message and then i thought id try that driver but i dicided that id judt do a clean install because my install had lots of problems that i dint with my last install on the same computer

---

### Post by PriceChild on 2008-07-12
[ubottu(n=supybot@unaffiliated/jussi01/bot/ubottu )]

If you're having problems with sound, first ensure ALSA is selected, by double clicking on the volume control, then File -> Change Device (ALSA Mixer). If that fails, see [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) - [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) - [http://alsa.opensrc.org/DmixPlugin](http://alsa.opensrc.org/DmixPlugin) - For playing audio files, see !Players and !MP3

---

