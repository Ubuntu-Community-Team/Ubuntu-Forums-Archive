---
title: "HOWTO: Build and Install the Developmental ALSA Drivers"
date: 2007-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mbsullivan on 2007-08-27
HOWTO get the development ALSA drivers built and installed:

The developmental ALSA drivers may be needed to get a new sound chip working before they have been built into the stable ALSA releases.  Here is how to acquire, compile and install the developmental release of the ALSA sound drivers.

(1) install some packages to support the ALSA CVS build system:

```
sudo aptitude install mercurial autoconf libncurses5 libncurses5-dev
```

(2) download the newest ALSA development drivers (available [here]("http://hg-mirror.alsa-project.org/")):

```
hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver
hg clone http://hg-mirror.alsa-project.org/alsa-kernel alsa-kernel
```

The ALSA-Kernel code is linked to from within the development release of the ALSA drivers (so no separate build/install is necessary).

(3) download the latest stable versions of the ALSA libraries and utilities (available [here]("http://www.alsa-project.org/main/index.php/Download")):

```
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2
```

(4) untar and unzip the ALSA libraries and utilities: 

```
tar -xjf alsa-lib-1.0.14a.tar.bz2
tar -xjf alsa-utils-1.0.14.tar.bz2
```

(5) build and install the development ALSA drivers:

```
cd alsa-driver; ./cvscompile; sudo make install;
```

(6) build and install the ALSA libraries:

```
cd ../alsa-lib-1.0.14a/; ./configure; make -j 3; sudo make install;
```

(7) build and install the ALSA utilities:

```
cd ../alsa-utils-1.0.14/; ./configure; make -j 3; sudo make install;
```

(8 ) reboot

Afterwards, ensure that the volume is turned up and the speakers are unmuted (in alsamixer or another mixer program), because the speakers are muted by default by a new ALSA installation.  A new line may have to be added to /etc/modprobe.d/alsa-base in order to ensure proper operation on a specific sound card, but this step has been omitted since it is machine specific.

I hope this helps!  Let me know if you have any problems.
Mike

---

### Post by brad103 on 2007-09-04
Hi Mike

Thanks a lot for this - it was exactly what I was looking for after reading elsewhere that my Intel HDA ICH8 (Realtek ALC262 chipset) is not supported by the current stable ALSA drivers. I followed all the instructions on this page but still no sound!

lspci:
```
...
[   14.848000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   14.848000] ALSA /tmp/alsa/alsa-driver/pci/hda/hda_codec.c:2745: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   14.848000] ALSA /tmp/alsa/alsa-driver/pci/hda/hda_codec.c:2749:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.848000] ALSA /tmp/alsa/alsa-driver/pci/hda/hda_codec.c:2753:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   14.848000] ALSA /tmp/alsa/alsa-driver/pci/hda/hda_codec.c:2761:    inputs: mic=0x19, fmic=0x18, line=0x0, fline=0x0, cd=0x
0, aux=0x0
...
```
Everything here after the first line is new since following your instructions, so looks like progress has been made.

cat /proc/asound/oss/sndstat
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.14 emulation code)
Kernel: Linux cyborg 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xca000000 irq 23

Audio devices:
0: ALC262 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC262

```
The mixer has changed from being Intel (something or rather) as well.

Could it be that I need to edit /etc/modprobe.d/alsa-base as you suggest?

Thanks a lot
Brad

---

### Post by brad103 on 2007-09-04
Accidental duplicate post here...

---

### Post by mbsullivan on 2007-09-06
> Could it be that I need to edit /etc/modprobe.d/alsa-base as you suggest?

I'm gonna be honest with you... I haven't a clue.  Give it a go and add the following to the end of alsa-base if it's not there already:

```
options snd-hda-intel index=0
```

You'll probably have to do more research with your particular sound card to get it working.  I think the newest ALSA drivers have as good of chance as any to get you to a working state, though.  Good luck!

Mike

---

### Post by brad103 on 2007-09-11
Thanks Mike

I tried adding that line, but still go. I'll keep searching...

Cheers
Brad

EDIT 31-10-07: Ignore me. I had a hardware fault that had to go back to the supplier for! Cheers :)

---

### Post by cwhitehouse on 2007-09-22
Thank you very much for this post.  It worked like a chart and was very helpful after lots of searching.

---

### Post by mbsullivan on 2007-10-04
> Thank you very much for this post. It worked like a chart and was very helpful after lots of searching.

Glad to hear it!  I was a bit surprised that there weren't others like it when I had a problem with my sound card.

Mike

---

### Post by kooseefoo on 2007-10-08
Thanks a lot! Worked great. I had to make one slight change though.

Since I was making the install to fix issues with my ICH8 family sound card (Dell Latitude D830 laptop), the file
```
/lib/modules/`uname -r`/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
``` had to be moved or removed. Not sure why... haha. But, it fixed it. My guess is that it, being the default snd-hda-intel kernel module, was conflicting with the developmental ALSA install.
Thanks!

---

### Post by stevie_velvet on 2007-10-30
I have installed the latets ALSA 1.0.15, but my #lspci reveals only the Intel HD Audio Controller

fudge!

---

### Post by caramelsoul on 2007-12-11
> cd alsa-driver; ./cvscompile; sudo make install;
bash: cd: alsa-driver: No such file or directory
bash: ./cvscompile: No such file or directory
make: *** No rule to make target `install'.  Stop.


This is what i get after step 5. I have changed the numbers from 14 to 15 to indicate newer versions.

Any body help?

---

### Post by mbsullivan on 2008-02-06
Sorry for not getting back to you sooner...

> This is what i get after step 5. I have changed the numbers from 14 to 15 to indicate newer versions.

Any body help?

The "alsa-driver" directory is dependent on step 2:

```
hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver
```

Did this part go okay?  What folders do you have in the current working directory after Part 4?

As an aside, Ubuntu Hardy is now working off of Alsa-Base 1.16, so it may behoove people to try and download from the Hardy repositories if installing the true developmental drivers doesn't work out.

Hope this helps!
Mike

---

