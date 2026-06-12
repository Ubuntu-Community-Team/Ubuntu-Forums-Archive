---
title: "Ubuntu 18.04.01 Youtube/Netflix stuttering"
date: 2019-06-25
forum: New to Ubuntu
---

### Post by tyrel771 on 2019-06-25
While I’m not an entirely new user of Linux, I am still inexperienced and new enough that I should be treated as a normie as much as possible (please). I recently replaced Windows 10 on one of my laptops with Ubuntu 18.04.01 (other than the bootable USB with Deepin, that’s all I had lying around at the time). 
Specs: Dell Inspiron 15 5565, Kernel: 4.15.0-52-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu3)
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: Dell product: Inspiron 5565 v: 1.1.1 serial: N/A
           Mobo: Dell model: 01WM1Y v: A00 serial: N/A
           UEFI: Dell v: 1.1.1 date: 07/17/2017
CPU:       Quad core AMD FX-9800P RADEON R7 12 COMPUTE CORES 4C+8G (-MCP-) 
           arch: Excavator rev.1 cache: 4096 KB
           
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 21557
           clock speeds: max: 2700 MHz 1: 2902 MHz 2: 2890 MHz 3: 2893 MHz
           4: 2893 MHz
 
I only have 3-4 issues left to sort out before the user experience will make it worthwhile to use the computer regularly. I would like to ask the community for help dealing with one of these issues which I have not yet managed to resolve (apparently a common problem, but that has resulted in making it even harder to find a hardware-specific solution). When streaming video (whether Youtube or Netflix), there is a consistent and constant micro-stutter which makes it nearly unwatchable (this doesn’t occur for the audio, but does for the video). I know my (dual?) graphics card(s) should be sufficient for this to be avoided. However, I do not remember whether I really do have dual graphics cards on this particular laptop (been out of use for a while). I have also noticed that, while the computer’s hardware should be more than good enough for certain games, there’s a huge loss of performance (for instance, whether I run Skyrim via Proton, or using Lutris (unless I’m not doing it properly, which is entirely possible) on ‘high’ graphics settings, there’s too much stutter for it to be playable). Let me be clear, though, that I’m not complaining about the gamer experience on Linux - I am merely trying to give a clearer picture of what, I believe, may be a failure to properly update the drivers for the graphics cards.  
 
As far as I can tell when going to Dell’s website and using my service tag, my graphics cards should be: AMD-Radeon-R2-R4-R5-R7-and-R5-M435-R8-M445DX-Graphics_P269Y
 
Using CPU-G gives me:
 
Graphic controller:  Advanced Micro Devices, Inc. [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics] (rev c8)
Open GL renderer: AMD Radeon R7 Graphics (CARRIZO, DRM 3.23.0, 4.15.0-52-generic, LLVM 7.0.0)
 
When opening a terminal and using the command ‘inxi -Fxz’ I get: 
 
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics]
           bus-ID: 00:01.0
           Card-2: Advanced Micro Devices [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
           bus-ID: 03:00.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: amdgpu,amdgpu
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: AMD Radeon R7 Graphics (CARRIZO, DRM 3.23.0, 4.15.0-52-generic, LLVM 7.0.0)
           version: 4.5 Mesa 18.2.8 Direct Render: Yes
 
 
Now, I found instructions for to update the graphics drivers:
[_[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)_]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD")
However, the instructions really are not clear to me at all (I don’t know anything about “fglrx” et alia). 
 
So, first, could somebody walk me through what to do in order to properly/optimally update my graphics cards?
Second, will/would that even help? I have seen a few suggestions online according to which Gnome is the problem. 
 
In fact, this thread seemed useful, but wasn’t specific to my hardware: [_[https://ubuntuforums.org/showthread.php?t=2393207](https://ubuntuforums.org/showthread.php?t=2393207)_]("https://ubuntuforums.org/showthread.php?t=2393207") 
 
I visited [_[https://wiki.archlinux.org/index.php/Intel_graphics#Xorg_configuration](https://wiki.archlinux.org/index.php/Intel_graphics#Xorg_configuration)_]("https://wiki.archlinux.org/index.php/Intel_graphics#Xorg_configuration") and [_[https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video](https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video)_]("https://wiki.archlinux.org/index.php/Intel_graphics#Tear-free_video") 
 
But none of this is clear to me. Anybody who can help, please do.

---

### Post by CatKiller on 2019-06-26
fglrx has been dead a long time. The drivers for AMD are open now.

None of the browser makers have enabled hardware accelerated decoding of video on Linux. It's all being done by your cpu, which is why it can stutter.

There's a build of Chromium that will enable it, though. More details [here](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html)

---

### Post by tyrel771 on 2019-06-26
Thanks. I tried getting the Chromium Beta branch PPA, but there is still some stuttering. So the issue hasn't been entirely resolved, but perhaps that's the best a Ubuntu user can hope for at this point? At least this was a step in the right direction, as it seems to have reduced the stuttering. 

Any further suggestions or thoughts about how to fix it?

---

### Post by tyrel771 on 2019-06-26
In particular, can anyone help me verify that my graphics cards' drivers are up to date, and/or help me figure out how to do that?

Cheers.

---

### Post by CatKiller on 2019-06-26
> **tyrel771 said:**
> Thanks. I tried getting the Chromium Beta branch PPA, but there is still some stuttering. So the issue hasn't been entirely resolved, but perhaps that's the best a Ubuntu user can hope for at this point? At least this was a step in the right direction, as it seems to have reduced the stuttering. 

Any further suggestions or thoughts about how to fix it?

As well as having the build that will use the hardware acceleration, you need the hardware acceleration to be there. I can't remember if AMD is best using VA-API or VDPAU, but you'll need one of them, I think. I have no idea if either of them are installed by default. Once you've got one, either, or both, installed you can use either vainfo or vdpauinfo to tell you which video formats your card can decode in hardware.

> **tyrel771 said:**
> In particular, can anyone help me verify that my graphics cards' drivers are up to date, and/or help me figure out how to do that?

Cheers.

I'm really hazy about which Radeon model number is which, since I use either nVidia or Intel on each of my computers, but support for AMD comes from both the kernel and Mesa.

If you've installed 18.04.1 you won't be on the latest versions of either. There is a Hardware Enablement Stack (hwe) that will pull in newer versions of the kernel, Mesa, and the X server. The HWE for 18.04 and 18.04.1 became the base version for 18.04.2, but people on those earlier versions wouldn't have been automatically upgraded since 18.04 is a Long-Term Support release and shunting people to a different kernel branch after install isn't very supportive.

If you need newer than that, there are some PPAs that provide cutting-edge versions.

The very newest AMD graphics adaptors really benefit from being on the newer stuff, since it took a little while for support to be added, and after the release of 18.04. I don't really know about the older stuff, and I don't know how new your graphics adaptor is.

---

### Post by QIII on 2019-06-26
If your GPU is supported, AMDGPU is active by default with 18.04.  If it is not supported, the Radeon driver is used.

In general, you can see if the AMDGPU module is loaded with 

```
lsmod | grep amdgpu
```

If you get no results, you are probably running the Radeon driver.  You can check that with:

```
lsmod | grep radeon
```

But in your first post, I see this:

> Display Server: x11 (X.Org 1.19.6 ) drivers: amdgpu,amdgpu

which is a pretty good indication that amdgpu is loaded and active for both GPUs.

I suspect that your issue is as a result of the "dual graphics", as AMD calls it, your machine sports.  Even with two GPUs from the same manufacturer, they may be competing.  That will often happen if the GPUs are not the same model.

I'd check your BIOS and see if there is a way to disable/blacklist one or set one as the preferred.  You will want to use the Topaz if you can and disable the one that is on-die with the CPU.


Please note:  I updated the [wiki article mentioned above]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") with the "Unsupported Version" tag and indicated that the entire article is obsolete.

---

### Post by tyrel771 on 2019-08-14
My apologies for not being on for a while, I left my Linux aside in part because I can't seem to fix this issue. I'm back at it now - I reread what you've said, but I don't follow it at all. I don't know what VA-API is, nor what VDPAU is, nor do I know how to install either or both, or check whether either is installed. I don't know what a Hardware Enablement Stack is, I don't know what Mesa is, I don't know what the X server is, and I don't know what PPAs are. 

I would appreciate it if somebody could take another shot at helping me out. Thank you.

---

