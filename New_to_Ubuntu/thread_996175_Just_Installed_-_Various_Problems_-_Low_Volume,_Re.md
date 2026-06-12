---
title: "Just Installed - Various Problems - Low Volume, Restricted Drivers Wont Activate!"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Orkin on 2008-11-28
Ok, so I've just installed Kubuntu (8.10), as usual I'm having a problem with audio, I have never actually installed any distribution of Ubuntu and managed to get the audio working first time round on my system over the course of several computers with various default intel or soundblaster chips. Bummer.

This time I've got the sound there at least, but the volume is so low its a problem. I'm using an Intel HDA, I've tried adding 

"options snd-hda-intel model=" with various endings from [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

My card is a Intel Hda ALC662 specifically. Also tried to build various versions of the ALSA drivers, but I get to the make section and always get this error:

```
owen@owen-desktop:~/Desktop/alsa-driver-1.0.18a$ make
make dep
make[1]: Entering directory `/home/owen/Desktop/alsa-driver-1.0.18a'
make[2]: Entering directory `/home/owen/Desktop/alsa-driver-1.0.18a/acore'
copying file alsa-kernel/core/info.c
/home/owen/Desktop/alsa-driver-1.0.18a/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/owen/Desktop/alsa-driver-1.0.18a/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/owen/Desktop/alsa-driver-1.0.18a'
make: *** [include/sndversions.h] Error 2

```

:( So I have no idea what is up with that.

As far as other obvious options are concerned yes the volume is full way up on alsamixer etc on all various channels.

My other problem is that the system wont let me apply the restricted drivers for my ati Hd2600Pro, I I click on "activate" and it just doesnt do anything, quite useless.

So yep, Help plz! :)

---

### Post by lemming465 on 2008-11-29
> patch: not found
The /usr/bin/patch utility is often used to apply changes to source code.  If you don't have it, try installing the *build-essentials* metapackage.  E.g.```
sudo apt-get install build-essential
```
That will bring in patch, make, and a bunch of other stuff typically needed to build things from source.
> wont let me apply the restricted drivers for my ati Hd2600Pro
How recent does update-manager think your package lists are?  If you get any errors from *sudo apt-get update* you may have invalid repositories listed in /etc/apt/sources.list.  Try commenting out any 3rd party ones you added which aren't from ubuntu.com or canonical.com.  You can either uncheck them in System->Administration->Software Sources (GUI) or use a text editor to prefix the offending "deb ..." lines with a comment character '#'.

---

