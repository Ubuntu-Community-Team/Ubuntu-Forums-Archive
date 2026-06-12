---
title: "Tearing video with intel x3100"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by occams_beard on 2008-05-16
I just installed hardy 64bit, and noticed that I am getting really bad video performance with an onboard intel GMA x3100.  Moving windows around, scrolling in firefox, etc produces a really horrible tearing effect.  

As far as I know I have the newest version of xserver-xorg-video-intel 2.2.1. 

I have also tried enabling sync-to-vblank in compiz, which seems to have no effect. And sadly, I get the same tearing effect with visual effects turned off.

Any ideas? Really sucks to use a state of the art OS with video that looks like its from 1994.

My specs are Intel Q6600 core 2 quad, 3GB RAM, 1650x1050 resolution.

---

### Post by shifty_powers on 2008-05-16
erm, will get back to you on the main q, but gien a quad core processor, and 3 gig of ram, could you not spare £20/$30 odd dollars and just buy a low end nvidia card?

nvidia has by far and away the best driver support on linux for gcards, and any will give you better performance than the x3100....

---

### Post by occams_beard on 2008-05-16
No, not at the moment I cannot afford an nvida card. This current rig left me totally broke as it is. And I don't play video games, so I figure the onboard intel should be sufficient for my needs. 

Anyway, spending money to fix something like tearing video, seems a little unreasonable.

---

### Post by shifty_powers on 2008-05-16
heh, sorry wasn't being rude or anything ;) and believe me would love a rig like that when i am running a socket 939 3200+ and 1 gig of ram ;)

anyways, the only reason i mentioned it is becasue the x3100 is notorious for being buggy on linuxin general and on ubuntu. there is a way of clearing up the video, iirc, but it causes other problems.

unfortunatley, the bottom line is that the driver support for your graphics chipset is poor.

brb

---

### Post by shifty_powers on 2008-05-16
[http://ubuntuforums.org/showthread.php?t=695195&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=695195&highlight=gma+3100)

[http://ubuntuforums.org/showthread.php?t=494943&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=494943&highlight=gma+3100)

[http://ubuntuforums.org/showthread.php?t=582873&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=582873&highlight=gma+3100)

[http://ubuntuforums.org/showthread.php?t=493738&highlight=gma+3100](http://ubuntuforums.org/showthread.php?t=493738&highlight=gma+3100)

---

### Post by shifty_powers on 2008-05-16
you're not running compiz with that are you? i know for a fact that it causes issues with the 3100. Also, as one of the above threads states, the proper driver for the 3100 is blacklisted as it does not play nice with ubuntu ;)

some reading to start you off anyways ;)

---

### Post by occams_beard on 2008-05-16
Thanks, I'll check those out!

Compiz works just fine with it, except for the tearing video. I get the tearing with or without it enabled. It even tears on metacity.

I wonder if there is another distro that is more intel gma friendly?

---

### Post by shifty_powers on 2008-05-16
might be, but i think the problem is not with ubuntu as such, but with the drivers that intel provide for that chipset for linux. still, worth having a look around ;)

i hear linux mint, which is based on ubuntu, is a bit better in this regard...

---

### Post by ThaRabbit on 2008-12-27
either use the sync feature and switch to GL output in your media player (mplayer?) or:

```
xvinfo
```

```
Adaptor #1: "Intel(R) Video Overlay"
    number of ports: 1
    port base: 82
```

then start mplayer with:
```
gmplayer -vo xv:port=82
```

solved the tearing for me with mplayer, though did result in the "blue" issue. It seems this is an issue with the intel driver.

---

### Post by Tom--d on 2008-12-27
I would either update to Ubuntu 8.10 and use the Texture Video as its a LOT better in Compiz.

I'm on 8.04 and my Intel x3100 works fine. No tearing at all. Video works fine with Compiz on. (Compiz is on all the time, I even use Xv for the GPU support. Works fine).
Scrolling is fine. 2D performance is good as far as I know.

But my advice is to upgrade to the new Ubuntu. There are Intel driver updates there.

---

### Post by sebrock on 2009-01-03
I have this massive tearing since upgrading from 8.04.1 to 8.10.

Worked just fine before... sucks.

---

### Post by cprofitt on 2009-01-03
> **sebrock said:**
> I have this massive tearing since upgrading from 8.04.1 to 8.10.

Worked just fine before... sucks.

What sucks even worse is that the Windows driver does not suffer this way... and Intel (as a completely open source driver) should be a flagship for Linux... and it is not.

---

### Post by ^^Snoop^^ on 2009-01-08
Until this gets fixed, Ubuntu is pretty much useless for me. I spend most of my time browsing the internet and watching videos. If I can't even watch videos properly, then it doesn't exactly make me warm to Ubuntu in its current state.

---

### Post by nr152522 on 2009-01-10
Hi there,

I seem to be suffering from the same tearing problem with my intel GMAX3100.

I am using Ubuntu 8.10 and it very noticeable on video playback.

I don't have compiz running...

It seems that some people have no problems yet others do.  Out of interest what device id does everyone have?

From output of **lspci -vvnn** I see that mine is: **8086:2A12**

I am guessing that a most people will have device id of: **8086:2012** 

So I am wondering if people having trouble have the same device-id as myself.

Any comments?

---

### Post by occams_beard on 2009-01-14
I've also noticed some people claim that they don't have any tearing with the X3100.  This totally mystifies me as I have two computers with an x3100 and they both tear horribly. It's frustrating and makes Ubuntu too annoying to use.

Here's what lspci -vvnn says about my X3100. My device id is 8086:29c2

```

00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 02)
	Subsystem: Dell Device [1028:020d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ff00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-


```

---

### Post by keypox on 2009-01-31
> **occams_beard said:**
> I've also noticed some people claim that they don't have any tearing with the X3100.  This totally mystifies me as I have two computers with an x3100 and they both tear horribly. It's frustrating and makes Ubuntu too annoying to use.

Here's what lspci -vvnn says about my X3100. My device id is 8086:29c2

```

00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 02)
	Subsystem: Dell Device [1028:020d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ff00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-


```

i doubt some people can see it... i have never seen an ubuntu system play hd videos without some tearing.  Was hoping this new ati driver came out yester day would fix it for me but nope.  But its a bit better.

---

### Post by stats on 2009-02-28
textured video did mess things up for those of us who have gm965 (X3100). i upgraded to intrepid, tried a whole bunch of "solutions". if i forced xv the system would hang on 20% of the videos i tried to open. 

finally reinstalled hardy and everything works fine in it.

recently tried jaunty, but it has the same issues as intrepid. so until they fix the tearing problem im stuck to hardy i guess

---

### Post by occams_beard on 2009-03-01
Yeah, I too see the tearing situation isn't any better in jaunty. I filled a bug on launchpad and it was confirmed... But I don't think it'll ever get fixed since it's just never worked properly and they can't even seem to sort out whether to leave textured video enabled or not.. The sad thing is there are more intel gfx chipsets in use than anything else, and they work great under Windows.

Anyway, I finally got fed up with the tearing and broke down and bought an nVidia card. Video is absolutely flawless with their proprietary driver.

---

