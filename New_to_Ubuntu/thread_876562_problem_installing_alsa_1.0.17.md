---
title: "problem installing alsa 1.0.17"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by abonon on 2008-07-31
i downloaded the latest alsa file/driver alsa-driver-1.0.17 in hopes that i could possibly get my mic to work in ubuntu 8.04 64-bit.

i could get it to config (./configure) but when I do the make command I get this:

/home/abonon/Desktop/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: implicit declaration of function &#8216;strict_strtoul&#8217;
make[3]: *** [/home/abonon/Desktop/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/home/abonon/Desktop/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/home/abonon/Desktop/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2

i have looked around for a way to fix this so that I can install it via the [make install] command in the terminal.

The sound card I have is the [ATI Technologies Inc SBx00 Azalia] and everything else works fine except for the mic.  I am currently using the alsa-base 1.0.16 driver.

when I do make install i get this:

everything looks fine until
...
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/abonon/Desktop/alsa-driver-1.0.17/acore'
make: *** [install-modules] Error 1

any help is appreciated.  :)

---

### Post by Trollslayer on 2008-08-01
The second section is caused by the driver fiels not being built by the first section.
As to the first section, it may be a problem working with 64 bit mode.

---

### Post by abonon on 2008-08-01
more 64-bit fun eh...  hehe i am really beginning to regret install this 64-bit OS.  It is a real hassle for a newbie.  :|

---

### Post by pantherattack on 2008-08-04
I got the same (or very similar) error yesterday when I was trying to install alsa 1.0.17 from source, and I am on 32-bit hardy.

My microphone also doesn't work yet (internal mike on an acer aspire one).

Any other suggestions?

---

### Post by leaphion on 2008-09-04
I have very similar problem with my Ubuntu 8.04 32-bit. Is there anyone able to help?

---

### Post by haroldo on 2008-09-12
I've succeeded in installing alsa 1.0.18 rc, some audio glitches were solved, but I still cannot use my internal mic !  Tried different settings in alsamixer.
If someone solve these audio problems, I'll be very happy to see an answer !

---

