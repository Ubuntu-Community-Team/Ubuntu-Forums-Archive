---
title: "Installation on Dell Inspiron of Ubuntu"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by hramos04 on 2008-07-10
Hi, I am kind of new to Linux. I have been using it for the past 4 years at school but have limited experience on installations.

I just bought a Dell Inspiron with a core duo 2 processor. I am planning on dual boot with the current installed vista. I have chosen Ubuntu because it seems that dell is actually selling these machines with Ubuntu 7.02 already installed. I am not sure if its here in the US but i know is done in Europe. 

Which version of Ubuntu should I  install the 32 bit or 64 bit?
Has any one have any experience with it?
Any recommendation?

Any sort of help will be appreciated.


    * Intel® Core™2 Duo mobile processor T5750 with 2MB L2 cache and 2.0GHz processor speed
    * 3GB DDR2 memory for multitasking power, expandable to 4GB
    * Multiformat DVD±RW/CD-RW drive with double-layer support records up to 8.5GB of data or 4 hours of video using compatible media

    * The next-generation Intel® Core™2 Duo processor is based on the innovative Intel® Core™ microarchitecture, so it runs faster and is more energy-efficient for cooler, quieter operation
    * 15.4" XGA widescreen display with TrueLife technology and 1280 x 800 resolution
    * 250GB Serial ATA hard drive (5400 rpm)
    * Intel® Graphics Media Accelerator X3100 integrated graphics with up to 256MB graphics memory as allocated by Windows Vista; Intel® High-Definition 2.0 audio; S-video output
    * Top-side media buttons to easily play, pause, stop, fast-forward and rewind at the touch of a button
    * Built-in 2.0-megapixel webcam to liven up Internet chat, instant messaging and blogs with color photos and video
    * 8-in-1 digital media reader supports Secure Digital, Secure Digital High Density, Secure Digital High Capacity, MultiMediaCard, Memory Stick, Memory Stick PRO, xD-Picture Card and SDIO formats
    * IEEE 1394 (FireWire) interface and 4 high-speed USB 2.0 ports for fast digital video, audio and data transfer
    * Built-in Dell 1395 wireless networking mini-card (802.11b/g); Dell's advanced antenna design features 3 antennas to find and connect to networks with ease, delivering enhanced wireless reception; standard Wi-Fi Catcher to quickly locate wireless hotspots
    * Integrated 10/100 Ethernet network card; 56 Kbps modem

---

### Post by Dark_Stang on 2008-07-10
I'm running 32 bit, because there is still no 64bit support for flash or java plugins. On top of that, I'm a comptuer science student and my college's main language is java. So at this point, I recommend 32 bit.

Run the 8.04 live cd and see what hardware is working/isnt' working so you can get a better idea of what issues you're going to run into.

---

### Post by hramos04 on 2008-07-10
Is there any place where I can download the live cd image so I can test it? Im looking for it but i cant find it

thankks

---

### Post by Dark_Stang on 2008-07-10
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by hramos04 on 2008-07-10
That is what I am currently downloading. But isnt that the installation disk? can it be used as a live cd too?

thanks

---

### Post by Dark_Stang on 2008-07-10
Yes, the Ubuntu install disk is a Live CD. (except for the alternate install disk)

---

### Post by DGortze380 on 2008-07-10
64 bit is fine if everything you need is supported. Be prepared to compile from source often. Otherwise stick with 32 bit

---

### Post by snowpine on 2008-07-10
> **hramos04 said:**
> That is what I am currently downloading. But isnt that the installation disk? can it be used as a live cd too?

thanks

Yes.

---

### Post by bryncoles on 2008-07-11
im probably a little late coming in here but 

[http://linux.dell.com/wiki/index.php/Main_Page](http://linux.dell.com/wiki/index.php/Main_Page)

and you can download the 7:10 (the previous ubuntu release) from here. click desktops and notebooks, then ubuntu 7:10, then download dell recovery iso.

its especially good, because optimised for dell's hardware. burn it as a live dvd. then if you like it, you can install it and  upgrade to hardy following the advice and updates on dells own website to resolve any issues which crop up!

---

### Post by hyper_ch on 2008-07-11
> **Dark_Stang said:**
> I'm running 32 bit, because there is still no 64bit support for flash or java plugins. On top of that, I'm a comptuer science student and my college's main language is java. So at this point, I recommend 32 bit.
that all runs fine on 64bit in hardy

---

### Post by Cadmus on 2008-07-11
I'm in agreement with hyper_ch, I think it's only the less common/poorly maintained programs that don't work on 64-bit.

---

### Post by hyper_ch on 2008-07-11
well, I only have a 32bit single core but my boss needed a new notebook and he wanted to try linux... so it's dual setup win xp (32bit) / ubuntu (64bit) and a vbox with win xp (32bit) in it...

added repositories are: medibuntu and budgetdedicated (wine)

Flash and java run fine in ubuntu... even the governmental provided tax declaration program works perfectly... way faster than in win xp 32bit actually (at least that's my impression)

---

### Post by Sam Lars on 2008-07-17
I'm running 64 bit, and only special programs are not supported on 64 bit.  Almost everything else runs fine, and you can install most 32 bit programs that you need.
I can't get the program for my Epson scanner to install, and the PTStitcher engine from libpano won't work.  Other than that, no problems.

---

### Post by jecho3k on 2008-07-18
I have 2 questions:

1. The wireless card is supported in Ubuntu? If is supported, is with free/libre or propietary drivers?

2. If I bought this laptop in Europe the wireless card says Dell™ Wireless 1395 802.11b/g - Europe. Can I use in USA and Latinoamerica too?

thanks

---

### Post by SunnyRabbiera on 2008-07-18
Wireless cards can be a pain, depending on the type...
but you can find out if it works by default by trying the live CD.
as for the card itself... possibly not, for the us you may need a US specific card and such, not sure on how that part works.

---

### Post by PinkFloyd102489 on 2008-07-18
The Intel NextGen wireless card is supported natively. You're good to go with it.

64bit works fine for me. Only problem Ive had is with Mozilla Sunbird. Didnt have to compile, just had to download some files and make an executable linking to those files.

---

### Post by DGortze380 on 2008-07-18
> **SunnyRabbiera said:**
> Wireless cards can be a pain, depending on the type...
but you can find out if it works by default by trying the live CD.
as for the card itself... possibly not, for the us you may need a US specific card and such, not sure on how that part works.

Wireless cards are not specific to countries. Your card supports certain protocols. If it supports IEEE 802.11b/g/n then you should be able to use it anywhere in the US and most if not all places abroad where there is a wifi hotspot.

---

