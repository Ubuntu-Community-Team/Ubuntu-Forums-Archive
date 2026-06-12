---
title: "Digital Output"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by jkettles16 on 2008-08-18
I tried a move to linux before with my current setup but digital sound didn't work and forced me back to Xp/Vista. I'm attempting the move again and this is a critical feature for me. As a bit of research I'm looking into the matter in various places, but there doesn't seem to be any really good sources that tell me exactly whether digital out is supported and if so on what cards exactly.

My hardware setup:

Intel BLKD975XBX2KR LGA 775 Intel 975X ATX Intel Motherboard
Broadway Com Corp Okia-black-650 650W ATX Power Supply
Intel Core 2 Duo E4500 Allendale 2.2GHz LGA 775 65W Dual-Core Processor Model BX80557E4500
Patriot Extreme Performance 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model PDC24G6400ELK
Western Digital Caviar SE WD1600AAJS 160GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM
EVGA 256-P2-N445-LX GeForce 7300GT 256MB 128-bit GDDR2 PCI Express x16 SLI Supported Video Card - Retail

I built this system primarily to create a hackintosh, which worked to an extent but also didn't have sound. I'm willing to try a different distro or a sound card that has known optical digital out support if that is necessary. Just need a helping hand to point me to the right resources.

---

### Post by markbuntu on 2008-08-18
Do you know which sound chip is on the mobo?

---

### Post by jkettles16 on 2008-10-23
The SigmaTel STAC9271D.

---

### Post by markbuntu on 2008-10-23
The STAC9271 is supported by the alsa snd_had_intel driver. You need to use the 5stack option to enable the digital output port if one is available. more on that here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

To get the digital output working:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

If you need a new card for digital output, cards using the c-media chipsets work out of the box with Ubuntu and have good specs at a low price.

---

