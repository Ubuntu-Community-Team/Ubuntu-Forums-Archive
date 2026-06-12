---
title: "[SOLVED] installed ubuntu studio addons and realtime kernel which caused problems"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by simtaalo on 2008-10-24
i installed the ubuntu studio bits onto my comp using the following command

```
sudo aptitude update && sudo aptitude install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

since then ive had problems with the computer being glitchy n hanging for 5-10 seconds where i cant actually do anything, although the mouse will still move around.

i also ran the command to clean some stuff up

```
sudo apt-get autoremove
```

which proceeded to give this error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of solfege:
 solfege depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing solfege (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 solfege
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i can see the two are linked, but what would be the best way to sort this out?

do i need to change the realtime kernel back to what it was before, would that fix things?

EDIT : found deb files

---

### Post by simtaalo on 2008-10-25
anyone able to help?

---

### Post by RonDeMay on 2008-10-26
I had problems with Ubuntu Studio as well. The rt kernel doesn't even work for my machine, I try to boot it up and the screen does strange glitchy crazy things and I have to shut it down manually and go into the regular Ubuntu Studio kernel.
I wish I could help but I'm having similar problems.

---

### Post by simtaalo on 2008-10-27
can no one help? even if its just to tell me how to change kernel??

---

### Post by snowpine on 2008-10-27
You should be able to choose which kernel from Grub each time you boot up. The real time kernel is glitchy on some hardware. It gave me problems until I upgraded my ram from 512mb to 1.5gb. You also need to change your habits when you are using the real time kernel. It works best if you are working in one application at a time, rather than switching back and forth between multiple open applications. All of the Ubuntu Studio applications should work okay with the standard kernel as well; the real time kernel is recommended if you're doing audio production and need low latency.

---

### Post by simtaalo on 2008-10-27
well my ram is 2gigs so that isnt the problem. ive also run the rt kernel before but was before id switched to 64-bit o/s.

the kernel version running is 2.6.24-21-rt, would be good if i could change to the non-rt version of this kernel.

---

### Post by simtaalo on 2008-10-28
can anyone help me change back from the rt version of the kernel?? surely someone can?

---

### Post by simtaalo on 2008-11-06
well i didnt get any help with this, but today i went into synaptics and upgraded stuff and everything has been running smoothly since then so i think the update has sorted everything.

---

