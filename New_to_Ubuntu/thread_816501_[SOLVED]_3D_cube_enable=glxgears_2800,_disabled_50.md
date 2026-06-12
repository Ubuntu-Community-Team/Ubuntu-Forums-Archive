---
title: "[SOLVED] 3D cube enable=glxgears 2800, disabled 5000 fps."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by philinux on 2008-06-02
Still got expo and effects etc

I dont think I'll be turning it back on.

Everything is much snappier without it.

---

### Post by EXCiD3 on 2008-06-02
Well, when you think about it, compiz is rendering everything itself and without compiz nothing is going through compiz. No extra effects is going to give much more power and speed to your applications when compiz is turned off.

---

### Post by sdennie on 2008-06-03
I don't see how enabling the cube would cause any drop in FPS.  Although, if you've set the cube to be transparent in any way, that could certainly do it.

---

### Post by EXCiD3 on 2008-06-03
Well, it does because everything has to be run through compiz instead of directly to the xserver. You are essentially adding another layer between the kernel and what you see and this will affect everything that requires any sort of graphics such as glxgears and videogames.

---

### Post by sdennie on 2008-06-03
> **EXCiD3 said:**
> Well, it does because everything has to be run through compiz instead of directly to the xserver. You are essentially adding another layer between the kernel and what you see and this will affect everything that requires any sort of graphics such as glxgears and videogames.

I kind of agree with that but, if I read the original post correctly, he's saying that compiz + cube is slower than compiz - cube.  The only way I can see how that's possible is if the cube is using transparency.

---

### Post by EXCiD3 on 2008-06-03
Didnt read it well enough i guess lol. its late, ill blame it on that. ;)

I would say transparency would make the most difference since i think compiz is coded well enough that not actually moving the cube would not make much of a drop in performance. The fps difference there is quite impressive, but you have to remember glxgears is **NO **way a benchmark. If you really want to test, anything based of quake 3 has a builtin benchmark and even nexuiz does too if im not mistaken.

---

### Post by philinux on 2008-06-03
Thanks for replies. I did have a transparent cube.

I'll try it without.

Is there a linux stand alone benchmark test we can use.

---

### Post by philinux on 2008-06-03
Setting transparency when not rotating to 100 restores the frame rate.

But this setting makes no sense. If it's not rotating you can't see it.

---

### Post by sdennie on 2008-06-03
Sure but, if you have what I'd call "idle transparency" set, it means that it has to render each side of the cube at all times and it has to filter it through some sort of transparency filter.  That is a huge drop in FPS.

---

### Post by Tomatz on 2008-06-03
> **philinux said:**
> Thanks for replies. I did have a transparent cube.

I'll try it without.

Is there a linux stand alone benchmark test we can use.

I have a amdx2 4200 2gb ddr2 800 and an nvidia geforce 8600gt 256 and i get about 7000fps with cube enabled and glx gears.

Something must be wrong with your gpu drivers???

---

### Post by Tomatz on 2008-06-03
```
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 2027MB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          version: 15.11.2
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-cdrom
                product: LITE-ON LTR-32123S
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capabilities: packet
           *-disk
                product: Maxtor 2B020H1
                vendor: Maxtor
                physical id: 1
                bus info: ide@0.1
                logical name: /dev/hdb
                capacity: 19GB
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:19:66:36:c7:28
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=192.168.2.3 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: GeForce 8600 GT
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

```

```
tommi@tommi-desktop:~$ glxgears
36226 frames in 5.0 seconds = 7245.102 FPS
39069 frames in 5.0 seconds = 7813.695 FPS
40040 frames in 5.0 seconds = 8007.925 FPS
39363 frames in 5.0 seconds = 7872.425 FPS
38639 frames in 5.0 seconds = 7727.735 FPS
X connection to :0.0 broken (explicit kill or server shutdown).


```

That is with compiz and almost all the plugins enabled.

---

### Post by philinux on 2008-06-03
I'm using nvidia-glx-new

---

### Post by Tomatz on 2008-06-03
This might help:

[http://ubuntuforums.org/showthread.php?p=4978329#post4978329](http://ubuntuforums.org/showthread.php?p=4978329#post4978329)

---

### Post by sdennie on 2008-06-03
philinux: I honestly wouldn't worry about it.  Googling for "glxgears" will probably bringup a billion posts saying, "glxgears isn't a benchmark".  If you like the cube and you like having the transparency on at all times then go for it.  Your monitor probably only refreshes 60 times a second so, 2800fps or 5000fps makes no appreciable difference.

---

### Post by philinux on 2008-06-03
Thanks for replies, I think I'll leave the driver alone for now. A new one is bound to filter through soon.

"transparency when not rotating"

I'd love to know what purpose this setting has though.

---

### Post by sdennie on 2008-06-03
> **philinux said:**
> Thanks for replies, I think I'll leave the driver alone for now. A new one is bound to filter through soon.


Probably not (maybe in 8.04.1 though) and, they aren't noticeably better for 3D performance I don't think (at least they aren't for me).  The experimental InitialPixmapPlacement=2, GlyphCache=1 and PixmapCacheSize are very cool but don't seem to be stable at the moment.

> 
"transparency when not rotating"

I'd love to know what purpose this setting has though.

Try setting that to something super low (like 0).  It should make the cube transparent even when you aren't rotating.

---

### Post by philinux on 2008-06-03
See what you mean. Ahh.

The cube does impress windows user though. Hah.

---

### Post by sdennie on 2008-06-03
> **philinux said:**
> That's it though, you cant see the cube unless it is rotating. :confused:

The cube does impress windows user though. Hah.

Haha. It does indeed.  When I used the cube a long time ago (maybe it was even Beryl), setting the non-rotating transparency to something < 100 would cause the wallpaper to become transparent and so you could see the other sides of the cube without actually switching to them.

---

### Post by philinux on 2008-06-03
Could someone explain this.

I'm now getting 11000 fps, has my gpu just got a kickstart.

---

### Post by saratchandra on 2008-06-03
> **philinux said:**
> Could someone explain this.

I'm now getting 11000 fps, has my gpu just got a kickstart.

Thats because you minimised the gears window :P

---

### Post by philinux on 2008-06-03
AAArrrgghh my bad. :lolflag:

---

### Post by Tomatz on 2008-06-03
Do you use the skydome if so try disabling it and run glxgears again ;)

---

### Post by philinux on 2008-06-03
Did that and same 5000 fps with opacity while not rotating set to 100.

What difference will the beta nvidia driver make.

By the way with nvidia-glx-new I don't get an nvidia splash screen.

---

### Post by Tomatz on 2008-06-03
> **philinux said:**
> Did that and same 5000 fps with opacity while not rotating set to 100.

What difference will the beta nvidia driver make.

By the way with nvidia-glx-new I don't get an nvidia splash screen.

The nvidia driver in the hardy repos seems to be buggy when used with the 8600-8800.

You can set the **No Logo** to **"false"** in */etc/X11/xorg.conf* (to get the splash). If that is what you wanted to do?

If you ane not experencing any lag, jolting etc with your current setup, i suggest you just leave it as it is.

An old man once said "if it ain't broke don't fix it" ;)

---

### Post by philinux on 2008-06-03
Google earth seems fine and I can play open-arena alien-arean and Tomb raider anniversary fine.

---

### Post by EXCiD3 on 2008-06-03
Just so you know there was a new Nvidia driver released on May 28th. You have to compile it from source and make sure you blacklist the "nv" driver or else it wont even acknowledge the nvidia driver. Here's a quick step by step on everything you need to do to install it from nvidia site: [http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

---

### Post by philinux on 2008-06-03
> **Tomatz said:**
> 
If you ane not experencing any lag, jolting etc with your current setup, i suggest you just leave it as it is.

An old man once said "if it ain't broke don't fix it" ;)

Well said.

Mind you it says screen refresh rate 51hz. LCD monitor

---

### Post by EXCiD3 on 2008-06-03
> **philinux said:**
> Well said.

Mind you it says screen refresh rate 51hz. LCD monitor

My monitor shows the same thing. It has to do with the exact refresh rate of the monitor actually. Mine has a refresh rate of exactly 59.89 hz and the application has trouble detecting this for some reason. Just use nvidia-settings to configure your monitor and never go back to displayconfig-gtk. At least you know its correct when you use nvida-settings.

---

### Post by philinux on 2008-06-03
Just used nvidia-settings, it wasn't installed so set the thing to auto and now I've 75 hz refresh.

---

### Post by EXCiD3 on 2008-06-03
> **philinux said:**
> Just used nvidia-settings, it wasn't installed so set the thing to auto and now I've 75 hz refresh.

That the correct refresh? I never have gotten anything good to come out of the Screen Resolution application...ever. Just ended up ruining my configuration. You should aslo try the new nvidia driver I posted about earlier. You will probably see better framerates too.

---

### Post by philinux on 2008-06-03
> **EXCiD3 said:**
> That the correct refresh? I never have gotten anything good to come out of the Screen Resolution application...ever. Just ended up ruining my configuration. You should aslo try the new nvidia driver I posted about earlier. You will probably see better framerates too.

Just checked again and it says 76hz. Close enough. 
These instruction seem different to what I've seen today on the forums.

STEP 2: Download the Driver File
Download - NVIDIA-Linux-x86_64-173.14.05-pkg2.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server configuration file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

---

### Post by EXCiD3 on 2008-06-03
The thing is, you have to blacklist the "nv" driver (open source 2D driver) in order for it to work. The installation instructions on nvidia's site are very general for ANY distro however the ones i posted are specific to Hardy. If you don't follow the instructions you will get what I had the first time and that is a xorg that is blank and you won't be able to use the nvidia driver. It has to do with conflicting names in the new driver I think and the work around i posted gets it up and running in no time. It is the exact same steps you would take to install the graphics driver normally (from their site) except you just add the blacklist.

---

### Post by philinux on 2008-06-03
Couple of questions.

1. I downloaded the driver to my desktop so I'll cd Desktop first.

2. How and when do you do the blacklist.

3. What happens to the nvidia-glx-new - will it then be disabled?

---

### Post by EXCiD3 on 2008-06-03
Compiling the driver will uninstall your old drivers and any files that might be conflicting. You will blacklist the "nv" driver before you try installing. Just so you know. You won't be able to install with the xserver running. You will have to go hit Ctrl-F1 and do your work from a console there (you can blacklist from the xserver, it just wont take effect until you restart it) but you need to be in the Ctrl-F1 screen in order to compile the drivers. Its all step by step in the tutorial. You might want to print it off since you wont be able to read it while you are compiling the driver.

If you have any problems, just install the driver again (sh command) and it should be fine. I had to compile it twice for some reason it had errors the first time, but i just tried it again and it went perfect.

---

### Post by philinux on 2008-06-03
> **EXCiD3 said:**
> Compiling the driver will uninstall your old drivers and any files that might be conflicting. You will blacklist the "nv" driver before you try installing. Just so you know. You won't be able to install with the xserver running. You will have to go hit Ctrl-F1 and do your work from a console there (you can blacklist from the xserver, it just wont take effect until you restart it) but you need to be in the Ctrl-F1 screen in order to compile the drivers. Its all step by step in the tutorial. You might want to print it off since you wont be able to read it while you are compiling the driver.

If you have any problems, just install the driver again (sh command) and it should be fine. I had to compile it twice for some reason it had errors the first time, but i just tried it again and it went perfect.

I tried it and ended up with 800x600 vesa. I'm on 64 bit will this be the problem?

---

### Post by EXCiD3 on 2008-06-03
It should make no difference. Try compiling it again, i had that problem a couple of times but then it just worked. Not sure why it doesnt work the first time...

---

### Post by philinux on 2008-06-03
Compliled it again same result low graphics mode.

It has done it as when I run it again it says it's installed.

I think I missed the step 
remove --purge nvidia*

It wanted to remove loads of stuff.

---

### Post by EXCiD3 on 2008-06-03
Yeah make sure you do all the steps. The --purge is important so that none of the new stuff is conflicting.

---

### Post by philinux on 2008-06-03
> **EXCiD3 said:**
> Yeah make sure you do all the steps. The --purge is important so that none of the new stuff is conflicting.

Yep I realised that when the forums where down.

I've now got full res back.

I've got nvidia xserver settings in system tools which reports the correct new driver.

When I hit the quit button shutdown and restart have vanished.

---

### Post by EXCiD3 on 2008-06-03
of course, fix one thing, break another! I'll see what i can find about that...thats awful weird!

**EDIT:** Oh you know what...did you start the xserver with "startx"? That removes the shutdown options. You need to go back and shutdown xserver with the etc/init.d/gdm stop command and start it with "sudo /etc/init.d/gdm start" instead and you should have the options back.

---

### Post by philinux on 2008-06-03
> **EXCiD3 said:**
> of course, fix one thing, break another! I'll see what i can find about that...thats awful weird!

**EDIT:** Oh you know what...did you start the xserver with "startx"? That removes the shutdown options. You need to go back and shutdown xserver with the etc/init.d/gdm stop command and start it with "sudo /etc/init.d/gdm start" instead and you should have the options back.

solved that. login session changed to xclient instead of last session.

Guess what glxgears 4800 fps. :( :lolflag:

---

### Post by EXCiD3 on 2008-06-03
Haha well think of it this way...at least you know how to compile the drivers yourself now. Thats too bad you didnt get any better frame rates. My 7600go 256mb is getting 4500 with compiz running. I've gotten up to 16,000 (no typo there :D) back in feisty. There are several xorg tweaks you can use too...Let me try to dig those up.

---

### Post by philinux on 2008-06-03
Yep I'd like to know why tomatz is getting so much higher fps then me.

Is it the case that I'd never notice the difference anyway with the monitor at 75hz refresh.

---

### Post by Tomatz on 2008-06-03
You may want to:

```
sudo apt-get remove --purge nvidia-glx-new
```

First ;)

---

### Post by Tomatz on 2008-06-03
> **philinux said:**
> Yep I'd like to know why tomatz is getting so much higher fps then me.

Is it the case that I'd never notice the difference anyway with the monitor at 75hz refresh.

You have to remember that glxgears is a simple animation so you will get a high fps reading. When you are trying to run something more complex, then you will notice the difference.

---

### Post by EXCiD3 on 2008-06-03
The framerate difference could be due to configuration differences in compiz. You might have more stuff enabled that he doesnt etc.

Well i sure cant seem to find those xorg settings. They probably dont have much of an effect on the newer drivers and compiz versions anyways.

Don't forget the glxgears is NOT a benchmark. If you really do want to compare your framerates try something else that can qualify as a benchmark like the benchmark abilities in the quake 3 engine.

---

### Post by philinux on 2008-06-03
> **EXCiD3 said:**
> The framerate difference could be due to configuration differences in compiz. You might have more stuff enabled that he doesnt etc.

Well i sure cant seem to find those xorg settings. They probably dont have much of an effect on the newer drivers and compiz versions anyways.

Don't forget the glxgears is NOT a benchmark. If you really do want to compare your framerates try something else that can qualify as a benchmark like the benchmark abilities in the quake 3 engine.

Thanks All

Where is the benchmark test in alien-arena or open-arena. Cant seem to find it in the setup.

---

### Post by Tomatz on 2008-06-03
> **EXCiD3 said:**
> The framerate difference could be due to configuration differences in compiz. You might have more stuff enabled that he doesnt etc.

Well i sure cant seem to find those xorg settings. They probably dont have much of an effect on the newer drivers and compiz versions anyways.

Don't forget the glxgears is NOT a benchmark. If you really do want to compare your framerates try something else that can qualify as a benchmark like the benchmark abilities in the quake 3 engine.


I have (almost) all plugins enabled also i run awn curves and screenlets.

---

### Post by Tomatz on 2008-06-03
BTW: Do you have *amd cool n quiet* enabled in the bios?

When i turned it off it gave me quite a performance boost.

---

### Post by EXCiD3 on 2008-06-03
If you want to compare your guys' computers reliably try the Linux Benchmark Suite: [http://lbs.sourceforge.net/](http://lbs.sourceforge.net/)

---

### Post by philinux on 2008-06-03
Thanks again, it's a new base unit with just ubuntu so was trying to find out how it compares etc.

---

### Post by philinux on 2008-06-03
> **Tomatz said:**
> BTW: Do you have *amd cool n quiet* enabled in the bios?

When i turned it off it gave me quite a performance boost.

I'll check, but why turn it off? isn't it supposed to be cool n quiet ?

---

### Post by EXCiD3 on 2008-06-03
> **philinux said:**
> I'll check, but why turn it off? isn't it supposed to be cool n quiet ?

It underclocks the processor to give you a cooler and quieter running cpu but it also affects the performance of your pc.

---

### Post by Tomatz on 2008-06-03
> **EXCiD3 said:**
> It underclocks the processor to give you a cooler and quieter running cpu but it also affects the performance of your pc.

Exactly it makes your pc/cpu consume the least power possible.

---

### Post by philinux on 2008-06-03
Turned it off - no difference.

In fact this doesn't work whereas before,as in before new nvidia driver etc., it did.

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
cat: /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq: No such file or directory

```

---

### Post by Tomatz on 2008-06-03
> **philinux said:**
> Turned it off - no difference.

In fact this doesn't work whereas before,as in before new nvidia driver etc., it did.

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
cat: /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq: No such file or directory

```

That is because it disables throttling as it runs at full speed constantly with cool n quiet disabled.

---

### Post by philinux on 2008-06-03
Ah right. But I've not really noticed much difference.

---

### Post by EXCiD3 on 2008-06-03
If you havent noticed much difference you might just want to re-enable it because all its going to do is make your computer run hotter seeing that you don't get any performance boosts.

---

### Post by philinux on 2008-06-03
Firefox from cold fires up slightly quicker but thats all really.

If anything on system monitor the cpu's are at a lower level.

Less than 5% and memory is less weird.

---

### Post by philinux on 2008-06-03
Turned cool n quiet back on.

Added cpu scaling to the panel and you can see that if you do anything the cpu goes to max 2.7 Mhz. When idle it drops back to 1 Mhz. So I'll leave it enabled. As temps much cooler too.

Thanks I'll mark this thread solved. Sort of.

---

### Post by EXCiD3 on 2008-06-03
> **philinux said:**
> Turned cool n quiet back on.

Added cpu scaling to the panel and you can see that if you do anything the cpu goes to max 2.7 Mhz. When idle it drops back to 1 Mhz. So I'll leave it enabled. As temps much cooler too.

Thanks I'll mark this thread solved. Sort of.

2.7**Mhz** and 1 **Mhz** eh? how old is this computer?!! :lolflag:

and I dont think Forum Tools has the option for "[SOLVED...sort of]" Maybe i wasnt looking hard enough ;)

My laptop uses scaling and i get it up to the max 1.83ghz whenever im doing something and drops to 1ghz when its idle.

---

### Post by philinux on 2008-06-03
4 weeks.
Base unit cost me £300

---

### Post by EXCiD3 on 2008-06-03
I'm sure you meant Ghz ;) If it was actually Mhz you sure got a ripoff!

---

### Post by philinux on 2008-06-03
Ha :lolflag: to late, need some sleep.

Thanks for your help. Obviously glxgears in no benchmark.

---

