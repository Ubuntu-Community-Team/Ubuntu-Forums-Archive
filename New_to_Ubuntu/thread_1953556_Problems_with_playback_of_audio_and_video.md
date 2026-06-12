---
title: "Problems with playback of audio and video"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by fertj on 2012-04-06
Hi!!
The video and audio playback is continuous cuts. I've tried different programs other than those that come with Ubuntu, such as: VLC and mplayer.  It also happen when I play youtube video or a dvd.

I have installed the lastet version of Ubuntu, 11.10 64 bits, in a PC with this characteristics:
 Atom 330 1,6 Ghz dual core, video GeForce 9400M, DDR2 2 GB, 500 GB hard disk.

I appreciate any help.

Thanks in advance.

---

### Post by PhantomTurtle on 2012-04-06
Has it always been like this or did this just start to happen. Also I'm just curious, why did you install the 64-bit version of Ubuntu. I used to have the 64-bit version on my computer but it was really slow and sluggish. That might not even be related but I just wanted to put it out there. Also do you have the proprietary drivers installed?

---

### Post by fertj on 2012-04-07
Thanks for your quick response. 
This has happened from the beginning to install, less than a week. 
Install 64-bit version because the PC's processor is 64 bits, but after seeing your comment I installed the 32 bit version. 
I think if I have installed the proprietary drivers, because when ubuntu starts,  after install, gave me the option and I did.
 With 32-bit version is working on the same way...
 Any idea?
 Thanks again!

---

### Post by alphacrucis2 on 2012-04-07
64bit version is best for 64bit capable CPU. In any case one thing to try is install any proprietary drivers for your system. Type add in the dash and it should find the Additional Drivers icon. Run it and let it install any applicable drivers for your hardware.

---

### Post by SeijiSensei on 2012-04-07
An Atom, even a dual-core one, will have problems with H.264-encoded video at high definitions like 720p or 1080p.  

Luckily for you you also have an NVIDIA card installed.  In 11.10, you should find the Additional Drivers application under System.  Run that and see if you have the current proprietary NVIDIA driver; if not, it will install it for you.

You're not done yet, though, because you need to tell your player software to use the "VDPAU" video output driver.  This will off-load the video decoding task to the video card.  I use smplayer, an excellent front-end to mplayer.  You can tell it to use the VDPAU driver by selecting Options > Preferences > Video and choosing vdpau from the drop-down box at the top.  

smplayer is in the repositories.  You can install it by typing "sudo apt-get install smplayer" at a Terminal prompt, or by selecting it from the package manager.

---

### Post by d4m1r on 2012-04-07
1) If you have 2GB of RAM, you should stick to the 32 bit version even if your CPU supports 64 bit.

2) Because of the low power of that PC (netbook?) I am not surprised video is choppy, especially if you are trying to watch 720P or even DVD media.

I'd recommend upgrading the PC if you can, or install an older version of Ubuntu designed to run with old hardware like 10.10 LTS.

---

### Post by SeijiSensei on 2012-04-07
> **d4m1r said:**
> I'd recommend upgrading the PC if you can, or install an older version of Ubuntu designed to run with old hardware like 10.10 LTS.

I have an ASUS 1201n netbook with a dual-core Atom and an NVIDIA adapter.  It can play h.264 HD encodes just fine using the VDPAU interface.

---

### Post by fertj on 2012-04-08
Hi!!
Thanks for all your responses. 
I tried what SeijiSensei indicated and now I get to play quite well, even with HD video.
 Again thank you very much for the help

---

