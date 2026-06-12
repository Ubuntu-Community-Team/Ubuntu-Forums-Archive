---
title: "[SOLVED] Choppy Videos in 8.04"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by indiana_crook on 2008-05-04
Can anybody help?  Videos online are ok, but videos saved on my filesystem are very choppy and slow.  Particularly in Full Screen.  Anybody know what to do???

---

### Post by SunnyRabbiera on 2008-05-04
well if you are using gstreamer then no wonder, sometimes gstreamer is not the best solution.
you may want to check out the medibuntu page [here]("https://help.ubuntu.com/community/Medibuntu") and then use it to get you stuff like the windows codecs.

---

### Post by indiana_crook on 2008-05-04
> **SunnyRabbiera said:**
> well if you are using gstreamer then no wonder, sometimes gstreamer is not the best solution.
you may want to check out the medibuntu page [here]("https://help.ubuntu.com/community/Medibuntu") and then use it to get you stuff like the windows codecs.

still no luck.

---

### Post by SunnyRabbiera on 2008-05-04
what players have you tried so far?

---

### Post by starcannon on 2008-05-04
Lets have a peak and see what video card you have and what modules are being loaded for it. I'm guessing you may not have the drivers for your video card loaded and that would likely cause choppy video playback.

Post the results of:

```
sudo lshw -C Video
```

as well as the results of:

```
 lsmod | grep i2c_core && lsmod | grep agpgart
```

---

### Post by indiana_crook on 2008-05-04
> **starcannon said:**
> Lets have a peak and see what video card you have and what modules are being loaded for it. I'm guessing you may not have the drivers for your video card loaded and that would likely cause choppy video playback.

Post the results of:

```
sudo lshw -C Video
```

as well as the results of:

```
 lsmod | grep i2c_core && lsmod | grep agpgart
```

caleb@caleb-desktop:~$ sudo lshw -C Video
  *-display               
       description: VGA compatible controller
       product: RS690 [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=64 module=fglrx
caleb@caleb-desktop:~$  lsmod | grep i2c_core && lsmod | grep agpgart
i2c_core               28544  1 i2c_piix4
caleb@caleb-desktop:~$

---

### Post by SunnyRabbiera on 2008-05-04
aha! its your radeon, ATI doesn't play nice with us I am afraid.
If you run desktop effects its best you turn them off, I know the effects are fun to look at but if it interferes with the system then turn them off.

---

### Post by indiana_crook on 2008-05-04
> **SunnyRabbiera said:**
> aha! its your radeon, ATI doesn't play nice with us I am afraid.
If you run desktop effects its best you turn them off, I know the effects are fun to look at but if it interferes with the system then turn them off.

Well, that sounds logical, but if i turn off desktop effects, then the video is choppy all the time.  Right now it's just in full screen.  I don't understand.  Everything worked GREAT with Gutsy.Do you think it has something to do with Compiz???

---

### Post by SunnyRabbiera on 2008-05-04
I am unsure, but your card is definitely part of the blame.
But thats ATI for you, they have miserable linux support, thats why nvidia is uaually recommended more then them as nvidia support is much better...

---

### Post by indiana_crook on 2008-05-04
okay then, anyone know where to get a good nvidia card at a reasonable price???

---

### Post by starcannon on 2008-05-04
I use nvidia here, so I'm useless with ATi problems, however I googled and found this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope that gets you pointed in the right direction, I always figure if I know what questions to ask, the answers will come. So if nothing else hopefully it will help you form some questions.

GL sorry I couldn't help more.

---

### Post by indiana_crook on 2008-05-04
> **starcannon said:**
> I use nvidia here, so I'm useless with ATi problems, however I googled and found this:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope that gets you pointed in the right direction, I always figure if I know what questions to ask, the answers will come. So if nothing else hopefully it will help you form some questions.

GL sorry I couldn't help more.

It's all good.  I've been having ATI trouble since day 1.  Unless I missed something, it seems as though 8.04 hasn't developed much ati support like gutsy did.  I just might wait and see what comes of it.

---

### Post by SunnyRabbiera on 2008-05-04
well hardy is not a experimental as gutsy, thats why its LTS...
usually non LTS ubuntus are more daring

---

### Post by indiana_crook on 2008-05-04
So, if i were to purchase an nvidia card, which one should I get??

---

### Post by starcannon on 2008-05-04
> **indiana_crook said:**
> So, if i were to purchase an nvidia card, which one should I get??

Any newer Nvidia card will work great, my favorite Linux happy Nvidia card is the 7950gt a 6600gt is also excellent, really depends on your needs, and your motherboard. AGP boards will narrow the field for you, PCIE boards will offer you a nice choice on the newer cards.

Heres a place where you can look at the available Nvidia Linux Drivers.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

The only personal anecdote I can really pass on as a caveat is that latest cards sometimes don't work correctly right away, it was about 6 months of waiting for my 8400m gs card to be fully functional when I got it in our notebooks, but it works perfectly now. I haven't been keeping up on when things have been released, so I have no clue as to how well the 9 series cards are running. I'm sure a little googling or forum searching could get answers about the 9 series cards though.

I do know for sure that 6, 7, and 8 series cards are working great, if you go 7 series I advise the 7900 or 7950.

Just my 2 cents

---

### Post by saundesj on 2008-05-04
> **indiana_crook said:**
> Can anybody help?  Videos online are ok, but videos saved on my filesystem are very choppy and slow.  Particularly in Full Screen.  Anybody know what to do???

I had choppy video and sound until I used this workaround: [http://ubuntuforums.org/showpost.php?p=4831424&postcount=46](http://ubuntuforums.org/showpost.php?p=4831424&postcount=46)

I'm using an ATI Radeon Mobility 7500. Compiz and videos are fine now.

---

### Post by indiana_crook on 2008-05-04
> **saundesj said:**
> I had choppy video and sound until I used this workaround: [http://ubuntuforums.org/showpost.php?p=4831424&postcount=46](http://ubuntuforums.org/showpost.php?p=4831424&postcount=46)

I'm using an ATI Radeon Mobility 7500. Compiz and videos are fine now.

Still Choppy

---

### Post by jhunter on 2008-05-07
> **saundesj said:**
> I had choppy video and sound until I used this workaround: [http://ubuntuforums.org/showpost.php?p=4831424&postcount=46](http://ubuntuforums.org/showpost.php?p=4831424&postcount=46)

I'm using an ATI Radeon Mobility 7500. Compiz and videos are fine now.

That link is a fix for open drivers.  Will it work for using the ATI propriety driver?

I've run into the same problem.  Choppy video on fullscreen, fine in window when effects are cranked up to extra.  Everything is choppy without effects.  I have an ATI X1600 (Pro or XT, Ubuntu doesn't know and I forgot) and I don't want to drop money on a new card.  In all fairness, Gutsy with propriety ATI driver worked, so I may try to downgrade if a fix isn't on the way.

---

### Post by philinux on 2008-05-07
I'm using an NVidia 512meg 8600GT sli and it's excellent. Only £48

---

### Post by indiana_crook on 2008-05-07
> **jhunter said:**
> That link is a fix for open drivers.  Will it work for using the ATI propriety driver?

I've run into the same problem.  Choppy video on fullscreen, fine in window when effects are cranked up to extra.  Everything is choppy without effects.  I have an ATI X1600 (Pro or XT, Ubuntu doesn't know and I forgot) and I don't want to drop money on a new card.  In all fairness, Gutsy with propriety ATI driver worked, so I may try to downgrade if a fix isn't on the way.

I'm purchasing an Nvidia GEFORCE 7600.  Hope that does the trick.

---

