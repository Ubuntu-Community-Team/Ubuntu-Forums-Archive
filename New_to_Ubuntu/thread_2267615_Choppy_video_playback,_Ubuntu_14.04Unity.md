---
title: "Choppy video playback, Ubuntu 14.04/Unity"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by pmi2 on 2015-03-02
This relates to a fairly fresh Ubuntu/Unity 14.04 install:

I use Handbrake (v 10.0, 64-bit) to encode videos to X264/MKV format.  It basically takes as much processor time as it can get on all four cores of my processor, which is as it should - BUT - I have noticed that other desktop apps do not seem to get much priority, even on a i5 3.3GHz processor with plenty of RAM.

Video playback (VLC media Player) is  choppy when handbrake is running, and even moving an open file manager window around is not very smooth, the window jumps around as it is being dragged over the desktop.

I also have Linux Mint in a dual boot installation on the same system, and I do pretty much the same thing on a different and much slower system in Windows 7, and I don't see the same problem. (the comparison to Windows does not bother me much).

I would think that in this regard, Unity/Ubuntu would have about the same performance as Cinnamon/Mint, given the same hardware.

So, what am I missing here?

---

### Post by Vladlenin5000 on 2015-03-03
Graphics card/chip?
Open source or proprietary drivers?

---

### Post by pmi2 on 2015-03-03
> **Vladlenin5000 said:**
> Graphics card/chip?
Open source or proprietary drivers?Thanks for reading.

Intel motherboard, integrated graphics (Intel HD Graphics), description from Intel docs:
> The Intel HD graphics controller features the following:
&#8226; 3D Features
&#63719;Direct X 10.1 and Open GL 3.0 compliant
&#63719;DirectX 11.0* CS4.0 only
&#63719;Shader Model 4.0
&#8226; Video
&#63719;Hi-Definition content at up to 1080p resolution
&#63719;Hardware accelerated MPEG-2, VC-1/WMV and H.264/AVC Hi-Definition video formats
&#63719;Intel®HD Technology with Advanced Hardware Video Transcoding
&#63719;Blu-ray S3D via HDMI 1.4
&#63719;Dynamic Video Memory Technology (DVMT) 5.0 support
&#63719;Support of up to 1.7 GB Video Memory with 4 GB and above system memory configurationIntel i915 drivers installed with the OS, don't know if those are the proprietary drivers or not

edit: 

If it helps, lspci says:> 00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)

---

### Post by Vladlenin5000 on 2015-03-03
Intel drivers are all open source and should work. Certain Nvidia and certain AMD chips perform poorly with the respective open source drivers that are installed by default.
Something is definitely wrong because I never experienced the behavior you reported even in quite inferior hardware configurations with just integrated Intel Graphics, a few were older than the Intel HD Graphics generation.

Unfortunately I'm clueless.

---

### Post by pmi2 on 2015-03-03
Thanks for your reply, anyway.  I am definitely not any kind of graphics or video guru, but what puzzled me is that I have been doing the same thing - running the handbrake queue w. several videos being encoded, while watching a video using SMPlayer or VLC player - with no playback issues on the other half of my dual boot, Linux Mint.  

So I suspect this is due to something I don't know about my new Ubuntu/Unity install.  
The hardware may be a bit older, but adequate to do this.  When I run SMPlayer  only, it consumes barely 10% of the processor bandwidth, and I never felt the need to install a graphics card on this mobo before... :(

---

