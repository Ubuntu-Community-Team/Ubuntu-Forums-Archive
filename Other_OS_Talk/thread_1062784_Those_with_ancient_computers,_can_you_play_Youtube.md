---
title: "Those with ancient computers, can you play Youtube videos?"
date: 2009-02-07
forum: Other OS Talk
---

### Post by timzak on 2009-02-07
Just wondering how old/slow your computers are that can still watch a Youtube video at a decent framerate.

I've got an HP Pavilion 6535 that I rescued and loaded Debian Lenny on.  Did a minimal install with XFCE.  It uses about 44 MB of ram after a fresh boot.  Using Kazehakase and flash 10, Youtube videos play at basically 1 fps (slide show).

Specs:
Celeron 466 Mhz, 256 MB ram, 20 GB 7200 rpm hard drive, Voodoo3 PCI video card (disabled onboard Intel video).

I'm trying to find out if this is normal, expected performance for this machine.  Anybody with a similar spec machine able to play Youtube videos at a decent framerate?

---

### Post by Twitch6000 on 2009-02-07
> **timzak said:**
> Just wondering how old/slow your computers are that can still watch a Youtube video at a decent framerate.

I've got an HP Pavilion 6535 that I rescued and loaded Debian Lenny on.  Did a minimal install with XFCE.  It uses about 44 MB of ram after a fresh boot.  Using Kazehakase and flash 10, Youtube videos play at basically 1 fps (slide show).

Specs:
Celeron 466 Mhz, 256 MB ram, 20 GB 7200 rpm hard drive, Voodoo3 PCI video card (disabled onboard Intel video).

I'm trying to find out if this is normal, expected performance for this machine.  Anybody with a similar spec machine able to play Youtube videos at a decent framerate?

My friend has a similar spec machine and his frame rate is better when using DSL and Puppy Linux.

---

### Post by Ed. Yang on 2009-02-07
1FPS is too low...

I've on-hand experience with a Fujitsu laptop with only 500mhz cpu, and integrated video that's too old to play youtube flash vids smoothly. But i can still achieve roughly about 20fps or so with xubuntu.

I guess there might be something got to do with your screen size as well as it's video card...

---

### Post by khelben1979 on 2009-02-07
On my old Powerbook I finally could watch youtube videos with Debian Lenny for the first time. I'm not sure what the fps is but I would guess it lies around four or five.

I experience this as pretty cool that it's actually possible, although I prefer watching them on my other system which is far more powerful (5 year old PC).

---

### Post by nitehawk777 on 2009-02-07
It also depends on your internet connection.  I just have dialup,....so video doesn't work smooth, even on my better computer.  It will play for a second or two,...then take a second or so to stop and "load" some more,....etc. etc.

EDIT:  actually, I just installed Debian Etch on this "good" P4 computer,...so I'll have to test it on videos.  (Been using my older PIII).

---

### Post by dburnett77 on 2009-02-07
> **timzak said:**
> Just wondering how old/slow your computers are that can still watch a Youtube video at a decent framerate.

I've got an HP Pavilion 6535 that I rescued and loaded Debian Lenny on.  Did a minimal install with XFCE.  It uses about 44 MB of ram after a fresh boot.  Using Kazehakase and flash 10, Youtube videos play at basically 1 fps (slide show).

Specs:
Celeron 466 Mhz, 256 MB ram, 20 GB 7200 rpm hard drive, Voodoo3 PCI video card (disabled onboard Intel video).

I'm trying to find out if this is normal, expected performance for this machine.  Anybody with a similar spec machine able to play Youtube videos at a decent framerate?

Should work, watch out for misconfig.  Flash is not demanding on processors, as even a modern cell phone is acceptable.

I'd say there's viral activity, or some such.  Try a re-install, and don't touch anything.

---

### Post by timzak on 2009-02-07
Thanks for the replies...

Internet speed is not an issue as I'm on a 5 meg connection.  Right now this machine is playing OGG files through Audacious.  No other apps open or running, and it's using 19% cpu and 54.5 MB ram total according to conky.

While Kazehakase is running a Youtube video (search "marble run" and run the first video), cpu usage is pegged at 100% (kazehakase using about 90% and Xorg using the other 10%), total system ram usage is at about 85-90 MB.  So there's plenty of ram available.  I did notice if I play a video with no sound, the cpu usage is still at 100%, but kazehakase is using about 65-70% and Xorg is using 30-35%.  In the video with sound, the sound plays at normal rates, so the sound finishes ahead of the video, since the video is chopping along at 1-5 fps.

At no point is the ram close to being maxed out.  Even if I replay the same video (so it's cached, eliminating the internet connection), I get similar performance as described above.

The sound card is an original Sound Blaster Live! PCI card.  The Voodoo3 PCI card is set up properly for 3D performance (whatever it's capable of) according to this post:
[http://ubuntuforums.org/showpost.php?p=84530&postcount=1](http://ubuntuforums.org/showpost.php?p=84530&postcount=1)

---

### Post by cmat on 2009-02-07
I'm thinking it's the ancient video chipset. There is no hardware acceleration given the default drivers and video is slow. I have a ATI Mach64 in a 333Mhz PII and it plays Youtube videos well. Even though the card is 14 years old.

---

### Post by khelben1979 on 2009-02-07
In my case it's because YouTube uses gnash and not the flash player from Adobe since it doesn't support this architecture.

I also do recall that when Debian chose to leave the XFree86 server in favour of x.org, 3d acceleration got slower when I was to play movies with Mplayer. Nowadays I don't know which one of these 2 x-servers which is the fastest.

---

### Post by K.Mandla on 2009-02-07
Flash 10 at 450Mhz on a K6-2 works well enough for me. I don't watch YouTube except once in a while, so it's acceptable.

[http://kmandla.wordpress.com/2008/12/19/case-in-point-crux-25-on-a-k6-2/](http://kmandla.wordpress.com/2008/12/19/case-in-point-crux-25-on-a-k6-2/)

---

### Post by timzak on 2009-02-07
Okay, so it sounds like the Voodoo3 chipset doesn't handle video acceleration.  In its heyday, it was a decent 3D accelerator, and 2D performance is fine, just the videos that don't work well.

Thanks for the help everyone.

---

### Post by timzak on 2009-02-07
I found a couple of other PCI video cards that might do better.  An S3 Virge and a Matrox Millennium.  Any opinions on which would be a better choice?

---

### Post by dmizer on 2009-02-07
> **timzak said:**
> I found a couple of other PCI video cards that might do better.  An S3 Virge and a Matrox Millennium.  Any opinions on which would be a better choice?

I have gotten the S3 Virge to work without too much fuss. It played flash just fine on my 650 MHz PIII. I don't know anything about Matrox Millennium though.

---

### Post by timzak on 2009-02-08
> **dmizer said:**
> I have gotten the S3 Virge to work without too much fuss. It played flash just fine on my 650 MHz PIII. I don't know anything about Matrox Millennium though.

Hmmm...just tried both the S3 Virge and the Millennium and both played flash just as poorly as the Voodoo3.  :(

Any trouble-shooting ideas from anyone?  Would the output of ```
lshw
``` provide any useful info?

---

### Post by LiamWilson on 2009-02-08
I'm running a Dell Optiplex GX1 with a 6gb Hard drive, with 192 gb of ram, and Running Xubuntu 8.10
It isn't currently connected to the internet, but when i do connect it, and play videos, it is extremely slow, running at about 5fps. But other than that, it's great!

---

### Post by timzak on 2009-02-08
Well, here is the output of lshw if it helps:

```
zane@debian:~$ lshw
WARNING: you should run this program as super-user.
debian                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MiB
     *-cpu
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.5
          size: 450MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KiB
     *-pci
          description: Host bridge
          product: 82810 GMCH (Graphics Memory Controller Hub)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-pci
             description: PCI bridge
             product: 82801AB PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: MX987x5
                vendor: Macronix, Inc. [MXIC]
                physical id: b
                bus info: pci@0000:01:0b.0
                logical name: eth0
                version: 25
                serial: 00:80:c6:f9:47:df
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tulip driverversion=1.1.15-NAPI ip=192.168.0.102 latency=66 maxlatency=56 mingnt=8 module=tulip multicast=yes
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: d
                bus info: pci@0000:01:0d.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: d.1
                bus info: pci@0000:01:0d.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64 module=emu10k1_gp
           *-display UNCLAIMED
                description: VGA compatible controller
                product: MGA 2064W [Millennium]
                vendor: Matrox Graphics, Inc.
                physical id: e
                bus info: pci@0000:01:0e.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801AB ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801AB IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=0 module=piix
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD200BB-00CFC0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 18GiB (20GB)
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: JLMS XJ-HD163
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82801AB USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.26-1-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 5-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-serial
             description: SMBus
             product: 82801AB SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0 module=i2c_i801
zane@debian:~$
```

I wonder if the video adaptor being "unclaimed" is significant?  The first video is the i810 onboard, which is disabled in the BIOS.

---

### Post by cmay on 2009-02-08
all my older computers i use debian lenny the lxde + openbox cd image and i can watch dvd and you tube just fine on them. the really old one i got 14 years ago still works great using this lenny cd version . i used it for a while just for internet usage and i did not have any problems with it. i have a new laptop which i use instead now.

---

### Post by timzak on 2009-02-09
As far as I can tell, I have everything configured correctly, and the poor flash performance is with three different video cards, so I'm guessing the motherboard on this computer has a poor implementation of the PCI bus.  Since a few of you have said that flash performs decently on your similar systems, that's the only explanation I can come up with.  Anyone else have any suggestions?

---

### Post by Sunflower1970 on 2009-02-09
Using Arch with LXDE on the old Compaq PII 400MHZ, 384MB RAM,with an old nVida GeForce3 Ti 500. Plays youtube vids or other vids fairly well. Not smooth-smooth, but still okay enough to watch. 

(shocked me it even worked to tell the truth...)

---

### Post by mips on 2009-02-09
What happens if you download the video first, close the web browser and then play it with a media player like vlc for example?

---

### Post by timzak on 2009-02-09
> **mips said:**
> What happens if you download the video first, close the web browser and then play it with a media player like vlc for example?

Hmmm...good question.  I've never tried to download a YouTube video.  Is there a preferred method?

---

### Post by kk0sse54 on 2009-02-09
> Hmmm...good question. I've never tried to download a YouTube video. Is there a preferred method? 
I've always liked youtube-dl, it's a nice minimal CLI app for downloading youtube videos

---

### Post by mips on 2009-02-09
> **timzak said:**
> Hmmm...good question.  I've never tried to download a YouTube video.  Is there a preferred method?

I just use a browser plugin like DownloadHelper for example.

---

### Post by dmizer on 2009-02-09
> **timzak said:**
> Specs:
Celeron 466 Mhz, 256 MB ram, 20 GB 7200 rpm hard drive, Voodoo3 PCI video card (disabled onboard Intel video).

Frankly, I think that Xubuntu may be too heavy for that computer. Something like [U-lite](http://u-lite.org/) or [fluxbuntu](http://fluxbuntu.org/) would probably work better for you. You could try a [DSL](http://www.damnsmalllinux.org/) live CD to see if things improve for you.

---

### Post by timzak on 2009-02-09
> **dmizer said:**
> Frankly, I think that Xubuntu may be too heavy for that computer. Something like [U-lite](http://u-lite.org/) or [fluxbuntu](http://fluxbuntu.org/) would probably work better for you. You could try a [DSL](http://www.damnsmalllinux.org/) live CD to see if things improve for you.

Yeah, I tried Xubuntu on this system and it IS too heavy.  But I'm actually using Debian Lenny with minimal xfce.  It uses about 1/3 the ram.

I'll give youtube-dl a shot first, then downloadhelper if I have probs.

Thanks, I'll report back.

---

### Post by timzak on 2009-02-10
> **mips said:**
> I just use a browser plugin like DownloadHelper for example.

Thanks for the tip, mips.  Xfmedia was able to play a downloaded .flv video from Youtube at normal framerates.  CPU load during playback was at 22%.  Playing the same video through Youtube with either Iceweasel or Kaz web browser pegged the cpu at 100% and produced the slideshow framerates.  

Is it possible to make the videos play smoother from within a web browser?

FYI, ram usage is <100MB with a web browser open, and the system has 256MB so there's no swapping going on.  

Normal web browsing does not peg the cpu at 100%...Ie, Ubuntu forums is fairly navigable.  I haven't checked cpu usage, but it's not 100%.

---

### Post by jrusso2 on 2009-02-10
> **timzak said:**
> Just wondering how old/slow your computers are that can still watch a Youtube video at a decent framerate.

I've got an HP Pavilion 6535 that I rescued and loaded Debian Lenny on.  Did a minimal install with XFCE.  It uses about 44 MB of ram after a fresh boot.  Using Kazehakase and flash 10, Youtube videos play at basically 1 fps (slide show).

Specs:
Celeron 466 Mhz, 256 MB ram, 20 GB 7200 rpm hard drive, Voodoo3 PCI video card (disabled onboard Intel video).

I'm trying to find out if this is normal, expected performance for this machine.  Anybody with a similar spec machine able to play Youtube videos at a decent framerate?

Are you using wireless?  I noticed flash being very slow on wireless.  Other than that it uses a lot of CPU.

---

### Post by mips on 2009-02-10
> **timzak said:**
> Thanks for the tip, mips.  Xfmedia was able to play a downloaded .flv video from Youtube at normal framerates.  CPU load during playback was at 22%.  Playing the same video through Youtube with either Iceweasel or Kaz web browser pegged the cpu at 100% and produced the slideshow framerates.  

Is it possible to make the videos play smoother from within a web browser?


I honestly do not know why playing the video in a browser is so slow.

If you don't find a fix for the problem I do have a suggestion for you though.

I recall in the earlier days of 64-bit linux flash was sometimes an issue in a browser. One of the workarounds at the time was to tell the browser to use a media player (mplayer I think) to handle the flash content. The video would still appear in the browser but it was actually played via the media player. This however is a workaround (and a good one) but not a fix. Sorry but I do not recall any more details though.

---

### Post by dmizer on 2009-02-10
> **mips said:**
> I recall in the earlier days of 64-bit linux flash was sometimes an issue in a browser. One of the workarounds at the time was to tell the browser to use a media player (mplayer I think) to handle the flash content. The video would still appear in the browser but it was actually played via the media player. This however is a workaround (and a good one) but not a fix. Sorry but I do not recall any more details though.

I found some discussion at the Arch linux forum regarding this possible solution here: [http://bbs.archlinux.org/viewtopic.php?id=35041](http://bbs.archlinux.org/viewtopic.php?id=35041)

I would suggest using that as a guide rather than a howto, as it's old, and not Ubuntu based.

---

### Post by mips on 2009-02-10
> **dmizer said:**
> I found some discussion at the Arch linux forum regarding this possible solution here: [http://bbs.archlinux.org/viewtopic.php?id=35041](http://bbs.archlinux.org/viewtopic.php?id=35041)

I would suggest using that as a guide rather than a howto, as it's old, and not Ubuntu based.

Nice find dmizer!

My recollection was that it was part of the Arch wiki on *one* of the ways to get flash working in 64bit.

For those not familair with pacman I'll do a quick translation,
```
sudo pacman -S mplayer-plugin or sudo pacman -S vlc-plugin
```would be the same as,
```
sudo apt-get install mplayer-plugin or sudo apt-get install vlc-plugin
```

---

### Post by timzak on 2009-02-10
> **dmizer said:**
> I found some discussion at the Arch linux forum regarding this possible solution here: [http://bbs.archlinux.org/viewtopic.php?id=35041](http://bbs.archlinux.org/viewtopic.php?id=35041)

I would suggest using that as a guide rather than a howto, as it's old, and not Ubuntu based.

Thanks, I'll give it a try.  Makes me wonder, though, about all the replies to this thread that seem to indicate that even slower systems are capable of playing YouTube videos smoothly.

I'll post back after I try this in case it'll help anyone else.

---

### Post by timzak on 2009-02-12
The mplayer plugin does not play videos consistently...sometimes it gets stuck at 97% when loading, and does not begin playing the movie until it is 100% loaded...BUT.  When it is successful in playing a Youtube video, the playback is very smooth.

I got some great feedback from Biotube at the Debian forums...he felt that the lack of SSE instructions in the Celeron 466Mhz processer might be the root cause.  He suggested that VLC knows "how to fall back to x87 instructions" while Flash doesn't.  Seems to make sense to me.

At any rate, this might be the catalyst to find a midtower case so I can use a slightly faster motherboard/cpu combo.  This Celeron 466 is part of a microATX system from HP, completely non-upgradeable.  I have components but no case/power supply for a Pentium III 733Mhz system that should have no problems handling Flash.

Thanks for everyone's help.

---

