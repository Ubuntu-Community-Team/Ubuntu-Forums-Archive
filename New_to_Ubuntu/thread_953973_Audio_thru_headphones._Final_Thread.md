---
title: "Audio thru headphones. Final Thread"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Kosimo on 2008-10-20
First word: HELP!
I've been asking for help for a long time, receiving answers that linked me on other threads that didn't work at at all.
I am sticky with windows for the most stupid issue I've ever had.
I bough a new laptop (Sony Vaio VGN-FZ335) That works gorgeous with Intrepid. Everything but the sound card. 
This laptop has a Stigmatel High Definition audio (I really don't know if hardware or software emulated) soundcard that is properly detected by Ubuntu. 
But, the mini-jack out (analog) doesn't works. When I plug headphones it doesn't do anything, and the laptop speakers are still sounding. It is a serious issue for me guys as I need to use them for VoIP, listen my music without pissing off my flatmates, and many other reasons. 
I haven't been able to solve it and now, I have to use windows everyday.

Does anyone on this forum thinks that is possible to make it working, and wants to help me step by step? I would really appreciate it and I promise to do my best effort to be back in Linux.

Thank you in advance guys.

---

### Post by Kosimo on 2008-10-20
Here the first screenshot:

Hope it helps

[IMG]http://kosimo.googlepages.com/soundcard[/IMG]

---

### Post by igknighted on 2008-10-20
Don't take this the wrong way, but I think this far too specific of an issue (on what I suspect to be a rather rare piece of hardware), so I think you will probably not get the best responses here.  I would ask a mod to move this into the hardware forum so it will be seen by those with the most expertise.

---

### Post by Kosimo on 2008-10-20
> **igknighted said:**
> Don't take this the wrong way, but I think this far too specific of an issue (on what I suspect to be a rather rare piece of hardware), so I think you will probably not get the best responses here.  I would ask a mod to move this into the hardware forum so it will be seen by those with the most expertise.

I didn't know where to create this thread, I guess that going to a specific one will be better. 
Thank you

---

### Post by Kosimo on 2008-10-20
Any help?

---

### Post by Kosimo on 2008-10-21
Up :(

---

### Post by Nepherte on 2008-10-21
Look at the output of:
```
cat /proc/asound/card0/codec#* | grep Codec
```
It will return the chipset model of your sound card, for example ```
Codec: Sigmatel STAC9872
```

Now browse to this alsa documentation page: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)  Search this document for (a part of) your model, for example ALC260. This will probaby list a couple of model options. Pick the one that comes closest to the one you have. Now open up /etc/modprobe.d/alsa-base:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
 and paste the following at the end of this file:
```
options snd-yourcard model=MODEL
```
where MODEL is the model option you picked earlier (I'll make a wild guess: vaio). You should have sound the next time you startup your computer.

---

### Post by tgalati4 on 2008-10-21
Nepherte has given useful advice.  If "vaio" doesn't work, try the other STAC options.  There are many variations in sound hardware.  You just need one to work:

9		STAC9220/9221
990		  ref		Reference board
991		  3stack	D945 3stack
992		  5stack	D945 5stack + SPDIF
993		  intel-mac-v1	Intel Mac Type 1
994		  intel-mac-v2	Intel Mac Type 2
995		  intel-mac-v3	Intel Mac Type 3
996		  intel-mac-v4	Intel Mac Type 4
997		  intel-mac-v5	Intel Mac Type 5
998		  macmini	Intel Mac Mini (equivalent with type 3)
999		  macbook	Intel Mac Book (eq. type 5)
1000		  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
1001		  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
1002		  imac-intel	Intel iMac (eq. type 2)
1003		  imac-intel-20	Intel iMac (newer version) (eq. type 3)
1004		  dell-d81	Dell (unknown)
1005		  dell-d82	Dell (unknown)
1006		  dell-m81	Dell (unknown)
1007		  dell-m82	Dell XPS M1210
1008	
1009		STAC9202/9250/9251
1010		  ref		Reference board, base config
1011		  m2-2		Some Gateway MX series laptops
1012		  m6		Some Gateway NX series laptops
1013		  pa6		Gateway NX860 series
1014	
1015		STAC9227/9228/9229/927x
1016		  ref		Reference board
1017		  3stack	D965 3stack
1018		  5stack	D965 5stack + SPDIF
1019		  dell-3stack	Dell Dimension E520
1020	
1021		STAC9872
1022		  vaio		Setup for VAIO FE550G/SZ110
1023		  vaio-ar Setup for VAIO AR

---

### Post by Kosimo on 2008-10-22
> **Nepherte said:**
> Look at the output of:
```
cat /proc/asound/card0/codec#* | grep Codec
```
It will return the chipset model of your sound card, for example ```
Codec: Sigmatel STAC9872
```

Now browse to this alsa documentation page: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)  Search this document for (a part of) your model, for example ALC260. This will probaby list a couple of model options. Pick the one that comes closest to the one you have. Now open up /etc/modprobe.d/alsa-base:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
 and paste the following at the end of this file:
```
options snd-yourcard model=MODEL
```
where MODEL is the model option you picked earlier (I'll make a wild guess: vaio). You should have sound the next time you startup your computer.


Thank you very, very, very very much!

Following your help with [other help]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/audio-out-port-doesnt-work-with-sigmatel-stac9872ak-611462/") I could MAKE IT WORKING!!!
Guys, I'm annoucing that I am 100% back to Ubuntu... I feel free again! :)

This is what it worked for me:
```
cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9872AK
Codec: Conexant ID 2c06

```


I added this line to /etc/modprobe.d/alsa-base: 

```
options snd-hda-intel model=vaio
```

And then installed ```
sudo apt-get install linux-backports-modules-$(uname -r)
```

Now is perfectly working.
I love ubuntuforums.

:guitar:
A happy free human being.

---

