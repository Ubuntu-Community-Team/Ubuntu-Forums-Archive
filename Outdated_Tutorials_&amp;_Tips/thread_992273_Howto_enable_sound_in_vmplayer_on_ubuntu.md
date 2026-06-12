---
title: "Howto enable sound in vmplayer on ubuntu"
date: 2008-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by bamboomy on 2008-11-24
Not much a full tutorial but might be helpfull for the many users that seemed to have the same problem (as I found while googling the net).

Problem: When trying to 'connect' the sound device in vmware player on (in my case) ubuntu 8.10 the player responds with 

```

Cannot connect virtual device sound. 
No corresponding device is available on the host.

```

or 

```

Failed to open sound device /dev/dsp1: 
Invalid argument Failed to connect virtual device sound.

```

or 

```

Failed to open sound device /dev/dsp1: No such file or directory

```

After some googling I learned that vmware uses oss and ubuntu uses alsa as standard. oss and alsa are different ways of getting sound out of your linux box, which one is best is in my point of view irrelevant, the fact is that vmware wants oss, so we give it oss.

I found a nice tutorial on help.ubuntu.com: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) on switching from alsa to oss, it's quite an adventure because you have to reboot your machine (in my case twice) to get to the end, I also don't think it's for the 'average joe' who uses ubuntu because you loose you startup sounds and stuff and the new sound system in 8.10 is build on solely alsa and there is no support for oss for system sounds.

Don't get me wrong, you can still use audacious and stuff but I don't guarantee that you will have the full ubuntu sound experience after using this guide. (More info on the given link.)

One last note, after installing oss there are numerous /dev/dsp* files in you dev directory, the truth is, no one will work with vmware player, what you have to do is give the full path to the new oss sound device, to obtain that device execute:

```

ls -l /dev/dsp*

```

Once you've done that all of the /dev/dsp files will reveal themselves as symlinks to, in my case:

```

/dev/oss/oss_hdaudio0/pcm0

```

If you fill in that value in the OurVmx.vmx file under:
```

sound.fileName = "/dev/oss/oss_hdaudio0/pcm0"

```

I don't know if the default value "-1" works also but this definitely works.

Disclaimer:
It is uttered by many that the solution that others proposed does not cover all of the cases in which the problem raises. As such I cannot claim that my solution will work for everyone, but it seems logic to me that if vmware wants oss, and if I give it oss, and it works on my system, it should work on everyones. This is not writing a little hack or changing some properties, this is fundamentally changing sound architecture (oss even asked whether alsa was build in in the kernel, (which is luckily not the case in ubuntu)) so this should work, but if it doesn't, it's not my fault.

---

