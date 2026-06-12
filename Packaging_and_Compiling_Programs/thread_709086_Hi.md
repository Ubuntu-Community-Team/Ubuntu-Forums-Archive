---
title: "Hi"
date: 2008-02-27
forum: Packaging and Compiling Programs
---

### Post by odd1here on 2008-02-27
have 20 minutes battery left & on my neighbors wifi.
-disclaimer-
i'm totally stupid as yes they could read everything i write right now. 
once you realize the way the world really is you stop caring mostly,
we are all voyeurs in a mush! :D

i really need to compile alsa. i don't have everything.
i have all the stuff from the alsa site just i don't have all the kernel stuff, libs and such

i installed fiesty several months ago and then ubuntustudio on top when it dropped
an i can't figure out the realtime kernel stuff, or should i say what it is i need to compile alsa! & other stuff.


i know its not much i just can't get to it.
and i'm bigtime stuck.
i know the cl enough to use it. so shoot me some commands!
i promise i will go away if you help me.
:popcorn:

---

### Post by renzokuken on 2008-02-27
to compile alsa (and most other things) all you need is one package ..... **build-essential**

this will install all the compile tools

```
sudo apt-get install build-essential
```

then try compiling alsa

---

### Post by RJ Hythloday on 2008-02-27
> **odd1here said:**
> I promise i will go away if you help me.
:popcorn:
Stick around, sit a spell, take a load off.

---

### Post by odd1here on 2008-02-27
ah thanks for the gesture.
my trouble is, i can't locate the full kernel source for the realtime kernel used with ubuntustudio.

i've tried with apt-get source and with synaptic, both yield strange results.

synaptic is only installing the changelogs in usr/local/doc
and 
apt-get source apparently isn't getting the right package as it does not contain the /sound/acore or even /sound/

do i need a gpg for the repository?
maybe i am using the wrong repository?
i have it set for the security branch thinking that was optimal.
..consufed

---

### Post by odd1here on 2008-02-28
i used apt-get build-dep with all the alsa stuff, and installed 75 packages, that i'm not sure if i need or if this is the actual function of build-essentials.
i believe it may be, however i really have no idea

so while using modprobe on my card 

i think i am getting down to where the trouble came from.



somehow, i emptied out my /lib/modules/2.6.22-14-rt/kernel/sound/core

```
\WARNING: Could not open '/lib/modules/2.6.22-14-rt/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-rt/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-rt/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-rt/kernel/sound/core/snd-pcm.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.22-14-rt/kernel/sound/pci/echoaudio/snd-indigoio.ko': No such file or directory

```

i reinstalled linux-rt & linux-image-rt
about to reboot. hopefully i'm not back on a mac!

---

### Post by odd1here on 2008-02-28
maybe the trouble is, i don't drink coffee eh much!

---

### Post by odd1here on 2008-02-28
i think i may have fixed it by reinstalling linux-image-2.6.22-14-rt
still can't find The file /lib/modules/2.6.22-14-rt/build/include/linux/version.h

but if i did this right, i should have both onboard and pcmcia card running.
i cross fingers while reboot.

---

