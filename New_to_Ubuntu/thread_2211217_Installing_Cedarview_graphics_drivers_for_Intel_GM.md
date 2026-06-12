---
title: "Installing Cedarview graphics drivers for Intel GMA 3600 on Ubuntu 12.04"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by matthew.humphreys on 2014-03-14
Hi,

I know that this has been dealt with in a variety of locations on the internet, but whenever I try to follow the guides, something ends up going wrong. There must be a step missed or something overlooked which results in the installation not working.

I am using a Samsung NC110 with an Intel GMA 3600 chip. I wish to install the proprietary drivers for the chip for use with 12.04. I understand that this potentially involves downgrading to an older kernel. What I require is a step-by-step guide detailing what is required in order to properly install the drivers (I know full graphics support may be out of the question, but any recognised driver is a start!). Currently, my attempts have been using 12.04.4, but if I require an earlier release, then please let me know.

Thanks

---

### Post by verymadpip on 2014-03-14
Hi matthew.
Is there any reason you couldn't use 13.10 until next month when 14.04, a LTS release becomes available?
I ask as I run Lubuntu 13.10 on an MSI netbook with the same graphics chip & all is well straight out of the box.  I am hopeful that the situation will be the same in 14.04.

---

### Post by matthew.humphreys on 2014-03-14
Not at all - I didn't realise it had out-of-the-box support for the Intel GMA 3600 chip! Does 3D hardware acceleration work with the most recent Ubuntu version? And are the drivers you are using open-source or proprietary?

---

### Post by thenh813 on 2014-03-14
EDIT: Someone posted before I was finished typing again. :)

If you want to use the official drivers, install 13.10 and install the appropriate DEB.
At least Intel provides source code and prebuilt binaries for the latest Ubuntu version and Fedora.

[Graphics Installer for Ubuntu* 13.10, 32-bit]("https://download.01.org/gfx/ubuntu/13.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.4-0intel1_i386.deb")[URL="https://download.01.org/gfx/ubuntu/13.10/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.4-0intel1_amd64.deb"]
Graphics Installer for Ubuntu* 13.10, 64-bit[/URL]


It requires these installed first, click the links for source code.
I will try compiling them for you, and will post DEBs if all goes well.


[LIST]
[*]   [Linux Kernel - 3.12.2]("https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.12.2.tar.xz") 
[*][Mesa - 10.0]("ftp://ftp.freedesktop.org/pub/mesa/10.0.4/MesaLib-10.0.4.tar.bz2") 
[*][xf86-video-intel - 2.99.906]("http://xorg.freedesktop.org/archive/individual/driver/xf86-video-intel-2.99.906.tar.gz") 
[*][Libdrm - 2.4.49]("http://dri.freedesktop.org/libdrm/libdrm-2.4.49.tar.gz") 
[*][Libva - 1.2.1]("http://www.freedesktop.org/software/vaapi/releases/libva/libva-1.2.1.tar.bz2") 
[*][vaapi intel-driver - 1.2.2]("http://www.freedesktop.org/software/vaapi/releases/libva-intel-driver/libva-intel-driver-1.2.2.tar.bz2") 
[*]   [Cairo - 1.12.16]("http://cairographics.org/releases/cairo-1.12.16.tar.xz") 
[*][Xserver Xorg - 1.14.5]("http://ftp.x.org/pub/individual/xserver/xorg-server-1.14.5.tar.bz2") 
[*][Intel-gpu-tools - 1.5]("http://xorg.freedesktop.org/archive/individual/app/intel-gpu-tools-1.5.tar.bz2") 
[/LIST]

```


**Release description**

 The 2013Q4 highlights are: OpenGL 3.3 API support, Fast Boot support and, power savings features. 
 OpenGL 3.3 API supported landed in Mesa 10 along with new GL extensions.
 Fast Boot support on 2D side had already being released on  previous 2013Q3, but now it is fully functional with Kernel support. It  might be need require to enable it on your BIOS configuration.
 The power features PC8+ and eDP Panel Self Refresh (PSR) landed on this kernel for 4th Generation Intel® Core&#8482; processors with Intel HD Graphics. 
 **Highlighted new features or fixed bugs**

 **Kernel**

 
[LIST]
[*] Fast Boot . 
[*] Haswell PC8+. 
[*] eDP Panel Self Refresh (PSR) support for Haswell. 
[*] Added eLLC cache support for 4th Generation Intel® Core&#8482; processors with Intel® Iris&#8482; Pro Graphics 5200. 
[*] Atomic page flipping. 
[*] Introduction of VMA objects. 
[*] Graphics stolen memory properly reserved (fix). 
[/LIST]
 Complete and detailed list can be found at Maintainer's (Daniel Vetter) announcements:
 
[LIST]
[*] [Neat drm/i915 stuff for 3.12]("http://blog.ffwll.ch/2013/09/neat-drmi915-stuff-for-312.html") 
[/LIST]
 **2D Drivers**

 
[LIST]
[*] Fix VSync on Haswell. 
[*] Disable Y-tiling on gen4. 
[*] Avoid issuing multiple DPMS requests to the same encoder (alised to multiple connectors) to avoid upsetting Haswell and leaving the screens blank. 
[*] Honour the user preferrence for the initial mode. 
[*] Fix video output using sprites when changing the image size. 
[*] Apply more restrictive tile constaints for 915g class devices. 
[*] Ensure all overlapping rectangles are drawn for XRenderFillRectangles. 
[*] Prevent discarding active upload buffers, causing glitches in chromium. 
[*] Promote the Ironlake pipecontrol to be a full pipeline flush to prevent render cache corruption. 
[*] Never pass an invalid trapezoid to pixman. 
[*] Make sure the current mode is always listed amongst the output modes. 
[*] Prevent a crash when starting with a user specified mode or position. 
[*] Pad GETCONNECTOR ioctl for compatability between 32/64-bit userspace and kernel. 
[*] Handle long glyph runs correctly. 
[*] Fix clipping of stippled rectangles against clip regions. 
[*] Support TearFree rendering of rotated outputs. 
[/LIST]
 Complete and detailed list can be found at Maintainer's (Chris Wilson) [announcements]("http://lists.x.org/archives/xorg-announce/").
 **3D Drivers**

 
[LIST]
[*] OpenGL 3.3 API support added. 
[*] GL_AMD_seamless_cubemap_per_texture. 
[*] GL_ARB_conservative_depth. 
[*] GL_ARB_texture_gather. 
[*] GL_ARB_texture_query_levels. 
[*] GL_ARB_texture_mirror_clamp_to_edge. 
[*] GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, and GL_ARB_transform_feedback_instanced on Gen7. 
[*] GL_ARB_sample_shading. 
[*] GL_ARB_shader_atomic_counters. 
[*] GL_ARB_vertex_attrib_binding. 
[*] GL_ARB_vertex_type_10f_11f_11f_rev. 
[*] GL_KHR_debug. 
[*] GLX_MESA_query_renderer. 
[/LIST]
 Complete and detailed list can be found at all [Mesa's 10 release notes]("http://www.mesa3d.org/relnotes/10.0.html").
 **Media Drivers - Libva/Intel-vaapi-driver**

 
[LIST]
[*] Motion compensation DI on HSW. 
[*] Optimization of FPS for H.264 encoding on HSW. 
[*] Add brightness/contrast/hue/saturation support for rendering. 
[*] Support BT601/BT709/SMPTE240 in vaPutSurface(). 
[*] Expose Constrained Baseline Profile instead of Baseline Profile for H.264. 
[*] Bug fixes. 
[/LIST]
 **Known issues**

 Intel® Celeron® N2810 processor with Intel® HD  Graphics had a critical regression on 3.12 Kernel that came in this  stack release. eDPs panel on this machine with this kernel verion cannot  be detected. The issue is described here [https://bugs.freedesktop.org/show_bug.cgi?id=69204](https://bugs.freedesktop.org/show_bug.cgi?id=69204) and  was already fixed on our development trees. Fix will land with Linux  kernel 3.13 soon and will be part of next stack release 2014Q1.
 On this stack it was also identified that GPU peak frequency can't reach peak immediately as exceptedly on 4th Generation Intel Core with Intel HD Graphics ([Bug 72385]("https://bugs.freedesktop.org/show_bug.cgi?id=72385")), and that FBC can increase power for libva video workload ([Bug 65396]("https://bugs.freedesktop.org/show_bug.cgi?id=65396")) on 3rd Generation Intel Core with Intel HD Graphics.


```

---

### Post by thenh813 on 2014-03-14
Nope, cannot compile drivers without replacing many libraries on my PC with debian testing versions. It would not be very stable, so I would not reccommend it. Sorry for fail, but you will have have to install 13.10 as [**[COLOR=#000000]verymadpip[/COLOR]**]("http://ubuntuforums.org/member.php?u=1010639") suggested. I will be doing likewise.

---

### Post by matthew.humphreys on 2014-03-15
Thank you very much for your efforts thenh813. It is unfortunate that Intel have not provided ongoing Linux support for their drivers.

If i do go ahead and install 13.10, what sort of graphics support will I have? Will I get any 3d rendering? Or will I only be able to run unity in 2d mode?

---

### Post by Rob Sayer on 2014-03-15
> **matthew.humphreys said:**
> ... It is unfortunate that Intel have not provided ongoing Linux support for their drivers.

I have a 1Gb Acer netbook with the atom 2600/gma3600 combo, so I have some experience with this.  It's not intel's fault that the drivers aren't updated per se.  Intel is generally pretty much the best at linux support.  The problem is that for some hardware they outsourced the video adapter, and this is one of them.  The manufacturer won't release the source code.

All that stuff you read about downgrading the kernel in 12.04 is wrong and at best out of date.  The kernel driver patch was moved upstream, and it can be used in 12.04 if you update it thoroughly after install.

However, it works a lot better in 13.04 and better, so the 13.10 recommendation is what I'd suggest too.

> If i do go ahead and install 13.10, what sort of graphics support will I have? Will I get any 3d rendering? Or will I only be able to run unity in 2d mode?

Don't install unity in a 2Gb ram netbook with the gma3600 adapter.  Period.  It won't run well.  I wouldn't install it in any 2Gb machine, let alone one with that hardware.  By linux standards unity is a memory hog, 2D or not.

The bad news with linux on a gma3600 equipped machine is that there is no 3D hardware acceleration whatsoever, and there isn't going to be in the foreseeable future.  I'd avoid unity or any other desktop that requires 3D accel.  Actually any Gnome 3 based desktop.

This isn't  a big problem for me because it's on a netbook, which I don't use at home much.  I got it because it's easier to carry around and saves knocking my more powerful laptop about.  I don't use it for video processing.

But I know there are people who've installed ubuntu on a netbook with the gma3600 thinking of watching HD video and finding it's not up to scratch.  There's no way it'll play 1080p or even 720p very well.  You can get it relatively smooth with judicous software choices and settings but it's still not that great.

I can see where they'd be a wee bit ticked at the whole experience.

I'm running lubuntu 13.10 now on this 1Gb netbook.  It's what most people here would recommend, or xubuntu.  I've tried both on it and lubuntu is definitely faster.  But it's a bit harder for newbies to configure.  I actually prefer kde and kubuntu runs surprisingly well in 1GB ram if set up properly.  But lubuntu is so much faster than even xfce (let alone kde) that I'm willing to forgive some rough edges.  I may put in another 1Gb ram and install kubuntu 14.04 later.

One thing about linux is that there's more to it than how much RAM the OS and desktop take.  Linux has more sophisticated memory management than windows.  It doesn't leave RAM unused ... it uses free memory as a file cache.  So having lots of memory makes a *huge* performance difference.  The more the better.

---

### Post by verymadpip on 2014-03-15
Hi again.
I should have added that I run 32 bit Lubuntu on the MSI U180 (1Gb RAM) as it's the lightest *buntu available & the performance is excellent for my needs using the open source driver included in the kernel.

All I actually need the U180 to do is surf, send the odd email, pretty much just "grandparents" stuff.  

I agree with Rob Sayer on this one, the performance makes the Lubuntu "rougher edges" worth it.

By the way, when you ask about 3D rendering you don't mean 3D modelling do you?  I wouldn't even install anything like Blender on my U180, I just don't think it has the horses.  I assume you're talking about your desktop environment, but you never know :)

---

### Post by Rob Sayer on 2014-03-15
> **verymadpip said:**
> ... when you ask about 3D rendering you don't mean 3D modelling do you?... 

Nope, 3D video hardware acceleration.  It doesn't work.  You can run a 3D test like glxgears (which isn't a good benchmark) and it'lll run but with very, very slow speed.  But it's being done by the CPU.

I think xubuntu is worth trying too.  Actually, for a beginner I'm having doubts about lubuntu's suitability for linux newbies.  There's generally some configuration required and lubuntu is *much* more difficult in that respect.

In fact I used to run kubuntu on this netbook ... BTW KDE in 1Gb is not usually recommended but unlike unity you can speed it up considerably ... and all the time I've spent trying to do simple setup and other tasks in LXDE has *more* than made up for the extra speed.  

For example, just copying from the terminal has been a joke.  Just trying to figure that out in itself has taken up more time than LXDE has saved me.

Forn that reason, I think the OP may want to try xfce first.

Just download both live cd iso's ... as mentioned, 32 bit would be the one to get ... and do the md5sum's.  Then burn to USB stick and try each desktop for yourself.

---

### Post by thenh813 on 2014-03-15
[**[COLOR=#000000]Rob Sayer[/COLOR]**]("http://ubuntuforums.org/member.php?u=1678250") has said it all. I couldnt put it better myself.
I would DEFINITELY go with 13.10, I am trying it right now, and it is faster that 12.10 13.04 (the reason I kept 12.04). I think the kernel has something to do with it.
[URL="http://ubuntuforums.org/member.php?u=1910851"][B][COLOR=#000000]
@matthew.humphreys[/COLOR][/B][/URL] Intel has some of the best support on Linux. Its just that (like Rob Sayer said) some of the companies that worked on a few adaptors want to keep their code to themselves. Newer versions of Ubuntu support it because the Open Source written-from-scratch drivers work well. Its just that the older versions of Ubuntu cannot run the libraries required without braking dependancies left and right (I had this problem compiling them, I would have to get libraries from Debian Jessie, and I dont want to risk that. Support in 14.04 should be the same or better when it is released. I found out that even 14.04 works pretty good in Live mode. Suprisingly, I havent found a bug LOL, im not gonna install it though, its 13.10 till its released for real.

I agree on the XFCE point also, Xubuntu 13.10 runs amazing on my parent's laptop (Iv been too lazy to spend 8 hours fixing Windows and getting the drivers working). What I like is I can install it as a emergency OS and set Windows 7 as default. If something dies, hold left shift, select Xubuntu from grub and run grub-set-default 0 once booted. Then it can run till I have time to fix it. Everyone seems fine with it, for the past 6 months, and it does all they need. Who knows, Windows may become the secondary OS haha.

---

### Post by Rob Sayer on 2014-03-17
> **thenh813 said:**
> ... I found out that even 14.04 works pretty good in Live mode....

It may work fine in live mode.

It may work just as well if you install it.

*But* there's a very good chance ... probably 100% by the time the stable is released ... that after you do an update you'll have a system crash.  And there 

And when it does crash it won't do elegantly as it does in the stable versions, with a nice notification in the panel with all other programs still running.  It will bork catastrophically.

At this point you will need serious command line skills.  Which is why suggesting pre stable ubuntu releases to newbies is so ridiculous.

---

### Post by matthew.humphreys on 2014-03-18
Thanks for all your responses. I have tried 13.10 and I have to agree with the poster who commented that Unity requires too many system resources to run smoothly on the netbook I have. Having looked around, I researched lubuntu, and actually ended up settling with linux mint xfce, which runs perfectly and quickly on the netbook. Although the xfce desktop isn't as aesthetically appealing as its cinnamon counterpart, it is extremely functional and uses linux software packages which means that I have had to make few changes to my everyday use.

---

### Post by maestrobwh1 on 2014-04-25
Almost a necropost: If you install Kubuntu 14.04 instead of Ubuntu 14.04 (I tried Ubuntu first), you will be surprised on how responsive KDE is compared to Unity these days.  I was shocked.  My experimental machine is one of those cheap ASUS X101CH EEEPC with this notoriously unsupported card (not Linux's fault apparently, Intel just really isn't open with the source code), and 1 GB RAM that is soldered to the board.  Unity is not usable.  Looks nice but seriously, they have a lot of work to do.  KDE used to be the resource hog (I never thought it was actually).  There are no lags.

I have had Bodhi (Enlightenment Ubuntu derivative) built on 12.04 running the cedarview-drm drivers but it kept locking up.  Kubuntu 14.04 is as least as snappy AND well, it is running compositing, and it is a full, non stripped down desktop, using the GMA 500 driver (which is less than ideal) and somehow KDE is able to deal with software rendering and Unity seriously can't without crippling performance.  :o

---

### Post by damasco on 2014-09-12
Eu tenho netbook acer aspire one d270 com um chip Intel GMA 3600 COM [SIZE=3]**UBUNTU 12.04.00**[/SIZE] COM UNITY FUNCIONANDO CORRETAMENTE COM CONTROLE DE BRILHO OK
OBSERVE  QUE APENAS CONSEGUI UTILIZADO O UBUNTU [SIZE=3]**12.04.00[SIZE=3], [/SIZE]**[SIZE=3][SIZE=2]APOS INSTAL[SIZE=2]AR  O SISTEMA  ME DIRECION[SIZE=2]OU AUTO[SIZE=2]MATICAMENTE PARA INSTAL[SIZE=2]AÇÃO DE UM DRIVER GRAFICO PROP[SIZE=2]RIETARIO, APOS INSTAL[SIZE=2]A[SIZE=2]DO  FUNCIONOU CORRENTAMENTE, **NÃO POSSO FAZER A**[SIZE=2]**TUALIZAÇÃO DO KE**[SIZE=2]**RNEL** POIS [SIZE=2]PODERÁ FICAR LENTO.

RESUMO É ISSO IN[SIZE=2]STALE A [SIZE=2]PRIMEIRA VERSÃO DO **UBUNTU 1**[SIZE=2]**2.04.00** SEM FAZER [SIZE=2]ATUALIZAÇ[SIZE=2]ÕES(**NÃO**[SIZE=2]** FA**[SIZE=2]**ÇA A**[SIZE=2]**TUALIZAÇÃO DURANTE A INSTALAÇÃO**)[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

