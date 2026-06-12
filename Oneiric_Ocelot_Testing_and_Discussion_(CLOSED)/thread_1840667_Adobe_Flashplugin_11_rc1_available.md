---
title: "Adobe Flashplugin 11 rc1 available"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-08
Now the newest version (11.0.r1.129) is available both for 32-bit and native 64-bit architectures.

Here:
[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

This is very easy to install. For 64-bit systems you do not need any nspluginwrappers.
All you need is to move the downloaded libflashplayer.so file into this folder:
/usr/lib/mozilla/plugins
This is for Firefox. Althoug Chromium will find it there, you can copy the so file into this folder too:
/usr/lib/chromium-browser/plugins

---

### Post by effenberg0x0 on 2011-09-08
Just tested it. It seems to be better than previous versions. More fluid audio/video.

Still, I think it is amazing the way it just waste resources. 

My reasoning is the following: My work desktop is a fracking powerhouse comparing to the average low-end laptop that is considered by any software developer as the "standard PC". Its a Phenom II X6 1100T Black Edition, 6 cores overclocked at 4.2GHz plus 16GB of low latency RAM clocked at 1666MHz, 2 NVidia cards working together at 16X (SLI) with 1GB each with a bunch of other improvements and customizations. Benchmarking software ranks me above the performance of top Xeon and Opteron and only below overclocks based on liquid nitrogen cooling. All that meaning: There's currently no way for a standard commercial desktop PC to be more powerful than this.  

In this scenario:

- Flash 64 on W7 wastes less than 1% of CPU. No matter the complexity of the flash movie, You can run it for hours and you won't see it wasting more than 1%. It's not an integer, so it's hard to get an exact number. Lets accept 1%. 

- Flash 64 on Linux wastes an average of 21% of CPU (!?). It actually oscillates between 2% to 40%. I have logged it during access to a heavy flash site and made the statistics. So, a couple browser tabs running flash actually hogs my CPU lol.

- As a comparison, running VirtualBox on Linux and W7 64 Enterprise Edition as a Guest OS takes over an average of 3% of CPU. How can an entire OS, with antivirus, firewall, browser instances, flash (lol), memory resident apps and services, ms-office, etc with very large Excel, Powerpoint, PDF files being worked on at the same time, etc, waste almost 4 times less CPU resources than a single browser plugin on linux? 

Ok, I'm sure someone will say: Oh, but the modern CPU is optimized for virtualization. Come on, seriously: 1x Linux Firefox Plugin CPU usage = 4x VM with Full Windows Operating System, heavy apps running. It just makes no sense. So what the hell is going on inside flash code?

Regards,
Effenberg

---

### Post by MadCow108 on 2011-09-08
I don't know much about flash, but maybe just the hardware acceleration is better in windows.
how is the gpu load in windows compared to linux?

---

### Post by Harry33 on 2011-09-08
> **MadCow108 said:**
> I don't know much about flash, but maybe just the hardware acceleration is better in windows.
how is the gpu load in windows compared to linux?

Definitely a GPU acceleration issue.

---

### Post by lucazade on 2011-09-08
> **Harry33 said:**
> Definitely a GPU acceleration issue.

agreed.

windows implementation of flash is better than linux and osx, especially because it takes full gain of hw accel.. at the same time I'd say that linux flash outperforms osx one.
I made several tests on flash to build some giant touchscreen kiosks, while win could not be a choice cos of well-known issues, I had to choose linux over osx for it's flash plugin.

some benchs like this:
[http://www.snailsanimation.com/benchmark08_pres.php](http://www.snailsanimation.com/benchmark08_pres.php)
(monitoring also cpu usage)

nice thing, I'm able to watch youtube in HD using [flash-replacer plugin]("http://www.webgapps.org/add-ons/flashvideoreplacer") (it embeeds mplayer with vaapi support) on a low spec intel gma500 with cpu usage near 0% :D

---

### Post by pferraro on 2011-09-08
> **lucazade said:**
> agreed.

windows implementation of flash is better than linux and osx, especially because it takes full gain of hw accel.. at the same time I'd say that linux flash outperforms osx one.
I made several tests on flash to build some giant touchscreen kiosks, while win could not be a choice cos of well-known issues, I had to choose linux over osx for it's flash plugin.

some benchs like this:
[http://www.snailsanimation.com/benchmark08_pres.php](http://www.snailsanimation.com/benchmark08_pres.php)
(monitoring also cpu usage)

nice thing, I'm able to watch youtube in HD using [flash-replacer plugin]("http://www.webgapps.org/add-ons/flashvideoreplacer") (it embeeds mplayer with vaapi support) on a low spec intel gma500 with cpu usage near 0% :D

Have you tried viewing youtube videos using html5 ([http://youtube.com/html5)?](http://youtube.com/html5)?)  That should allow you to leverage va-api-based gpu acceleration, I think.

---

### Post by lucazade on 2011-09-08
> **pferraro said:**
> Have you tried viewing youtube videos using html5 ([http://youtube.com/html5)?](http://youtube.com/html5)?)  That should allow you to leverage va-api-based gpu acceleration, I think.

tried html5 youtube a lot of time ago but didn't know it could handle vdpau or va-api.
i'm googling everywhere but cannot find anything specific.. should give it a try again.

thanks for the info..

---

### Post by ratcheer on 2011-09-08
Got it. Things look fine in Firefox on Oneiric, but I can't say for sure it is better than before.

Tim

---

### Post by effenberg0x0 on 2011-09-08
Hey guys,
Agree with you all. Just checked that when booting a native W7 OS on this hardware, Flash is using the two NVidia cards memory and processing, thus the low impact on the main CPU and RAM. 

I can't really monitor it well on Linux: Have no app to see/log GPU/VRAM usage. But you are probably right.

Another thing I am thinking here. This version of Flash for Linux is probably not compiled to take advantage of this specific CPU features. I did compile the 3.0.4 kernel and some more relevant apps to take advantage of the X6 CPU, which is why everything is running very fast and optimized here. But, in the case of flash there's no source, so there's nothing to do anyway. I Hope flash dies soon.

Regards,
Effenberg

PS: Also, I had made a comparison to W7 as a guest on VirtualBox. However, we know that, to some extent, VirtualBox is capable of using hw acceleration, which should also reduce the footprint or VirtualBox on the host system. Again, that goes with your line of thought.

---

### Post by t1497f35 on 2011-09-08
Flash provides hw acceleration for nvidia >= GeForce 8 through VDPAU which is as good as the window (7) hw acceleration.

AMD (ati) & Intel video cards are not supported yet, because they don't support VDPAU.

---

### Post by effenberg0x0 on 2011-09-08
Sure. I have a Ubuntu XBMC-based HTPC with a GeForce 9500GT at home. Using NVidia proprietary drivers and VDPAU I can output 1080P content without any real stress in the machine. Most of the time coolers are off (passive cooling) which is great. NVidia + VDPAU is the way to go, definitely.

Still, I can't really believe Flash for Linux is making such good use of it, or such a good use as we see on the Windows platform. I mean, by the end of the day, I can see XBMC using less memory and CPU than Flash on this Linux machine. It's a fact.

Regards,
Effenberg

---

### Post by pqwoerituytrueiwoq on 2011-09-08
> **t1497f35 said:**
> Flash provides hw acceleration for nvidia >= GeForce 8 through VDPAU which is as good as the window (7) hw acceleration.

AMD (ati) & Intel video cards are not supported yet, because they don't support VDPAU.
then why is my cpu usage so dam high from flash (unless i play the video in totem)
nvidia geforce gt 430 (fermi) with nvidia driver version 280.13 
using 64bit

---

### Post by t1497f35 on 2011-09-08
> **pqwoerituytrueiwoq said:**
> then why is my cpu usage so dam high from flash (unless i play the video in totem)
nvidia geforce gt 430 (fermi) with nvidia driver version 280.13 
using 64bit
I'm not diagnosing computers remotely.
Using 9600gt & 560Ti here. No issues.
Unlike windows, VDPAU support shipped only starting with flash 10, so expect later versions of flash to improve on this front. Also, since flash 11 ships with Stage 3D etc and since youtube is gonna use it, there should be further benefits for nvidia linux users with newer video cards.

Currently using flash 11 RC amd64 and I haven't found anything to complain about.

But certain video cards are known to be supported less well by Nvidia, mainly those which introduced GL 4.0 which were very noisy and ppl didn't buy anyway.

---

### Post by pqwoerituytrueiwoq on 2011-09-08
> **t1497f35 said:**
> I'm not diagnosing computers remotely.
Using 9600gt & 560Ti here. No issues.
Unlike windows, VDPAU support shipped only starting with flash 10, so expect later versions of flash to improve on this front. Also, since flash 11 ships with Stage 3D etc and since youtube is gonna use it, there should be further benefits for nvidia linux users with newer video cards.

Currently using flash 11 RC amd64 and I haven't found anything to complain about.

But certain video cards are known to be supported less well by Nvidia, mainly those which introduced GL 4.0 which were very noisy and ppl didn't buy anyway.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162067](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162067) is the gpu i have
i don't think this should matter but i am running ubuntu 10.04
```
glxinfo | grep vdpau
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range,
```cpu usage is about 40% (full screen is 50-60%) with a 1080p video on youtube
full screen is a bit choppy

edit totem uses 30% cpu for 1080p so i guess that is not bad considering it is flash
edit 1080p flash improved in cpu usage

---

### Post by effenberg0x0 on 2011-09-08
See this comparison chart. The GT430 is not a powerful card for todays standards.
[http://www.tomshardware.com/forum/308790-33-gt240-gt430-gts450-hd5670](http://www.tomshardware.com/forum/308790-33-gt240-gt430-gts450-hd5670)
Current models are supposed to be 2.5 to 5.0 times more powerful (average, todays benchmarks for CPU/GPU are too complex/ abstract/ questionable).

Still, I really don't think one should need to have a powerful card to be able to have flash using reasonable CPU resources. 50%-60% for 1080P sound like too much for me. On a very standard PC (like a dual core) with a GeForce 9500/9600 you can expect CPU load to barely reach 10% when playing a 1080P mkv. 

The problem is when Flash is the interface for the video, not so much the video format / resolution IMHO. Which is why I started my random rant about it a few posts above lol.

Regards,
Effenberg

PS: Use something like xbmc to play a 1080P fullscreen video, enable VDPAU. Unless something is very wrong with your setup, I doubt you'll see anything close to 50%-60% CPU load. Which, once again, brings us to the topic, that meaning, Flash insanely eats resources.

---

### Post by lucazade on 2011-09-08
> **effenberg0x0 said:**
> .. Flash insanely eats resources.
.. and we can't stand it anymore :D

---

### Post by effenberg0x0 on 2011-09-08
> **lucazade said:**
> .. and we can't stand it anymore :D

Yeah, I mean, either they start taking performance on Linux seriously or they could provide code and support for the community. I trust Open Source devs could do a much better job. Adobe is behaving much like VIA in my opinion. Consider the whole iPhone issue, etc. 

I started a petition for VIA Open Source drivers a couple years ago ([http://www.petitiononline.com/mod_perl/signed.cgi?vialinux](http://www.petitiononline.com/mod_perl/signed.cgi?vialinux)) and honestly I feel too old to start a new fight against Adobe lol.

Regards,
Effenberg

---

### Post by lucazade on 2011-09-08
Let's hope html5 and friends could wipe out that sparklin-broken technology that is flash.
Maybe Adobe Edge will help this transition..

---

### Post by pqwoerituytrueiwoq on 2011-09-08
> **effenberg0x0 said:**
> See this comparison chart. The GT430 is not a powerful card for todays standards.
[http://www.tomshardware.com/forum/308790-33-gt240-gt430-gts450-hd5670](http://www.tomshardware.com/forum/308790-33-gt240-gt430-gts450-hd5670)
Current models are supposed to be 2.5 to 5.0 times more powerful (average, todays benchmarks for CPU/GPU are too complex/ abstract/ questionable).

Still, I really don't think one should need to have a powerful card to be able to have flash using reasonable CPU resources. 50%-60% for 1080P sound like too much for me. On a very standard PC (like a dual core) with a GeForce 9500/9600 you can expect CPU load to barely reach 10% when playing a 1080P mkv. 

The problem is when Flash is the interface for the video, not so much the video format / resolution IMHO. Which is why I started my random rant about it a few posts above lol.

Regards,
Effenberg

PS: Use something like xbmc to play a 1080P fullscreen video, enable VDPAU. Unless something is very wrong with your setup, I doubt you'll see anything close to 50%-60% CPU load. Which, once again, brings us to the topic, that meaning, Flash insanely eats resources.
thanks for the tip i found a ppa called "Nvidia Vdpau Team" installed [FONT=Courier New]libvdpau1 smplayer vdpauinfo smplayer-translations[/FONT]
and it plays 1080p with 10% cpu or less once i changed the driver it uses from xv to vdpau

---

### Post by chromatica86 on 2011-09-08
> **Harry33 said:**
> Now the newest version (11.0.r1.129) is available both for 32-bit and native 64-bit architectures.

Here:
[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

This is very easy to install. For 64-bit systems you do not need any nspluginwrappers.
All you need is to move the downloaded libflashplayer.so file into this folder:
/usr/lib/mozilla/plugins
This is for Firefox. Althoug Chromium will find it there, you can copy the so file into this folder too:
/usr/lib/chromium-browser/plugins
Do I need to delete the one that's already in that folder?

---

### Post by pqwoerituytrueiwoq on 2011-09-08
> **chromatica86 said:**
> Do I need to delete the one that's already in that folder?
assuming you are not using kde this is all you need from the file
(only the 1st 2 files changed since beta 2)
```
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/bin/flash-player-properties
/usr/share/applications/flash-player-properties.desktop
/usr/share/icons/hicolor/16x16/apps/flash-player-properties.png
/usr/share/icons/hicolor/22x22/apps/flash-player-properties.png
/usr/share/icons/hicolor/24x24/apps/flash-player-properties.png
/usr/share/icons/hicolor/32x32/apps/flash-player-properties.png
/usr/share/icons/hicolor/48x48/apps/flash-player-properties.png
/usr/share/pixmaps/flash-player-properties.png
```

---

### Post by ratcheer on 2011-09-08
> **chromatica86 said:**
> Do I need to delete the one that's already in that folder?

They have the same filename, so the new one should overwrite the old one.

Tim

---

### Post by t1497f35 on 2011-09-08
> **lucazade said:**
> Let's hope html5 and friends could wipe out that sparklin-broken technology that is flash.
Maybe Adobe Edge will help this transition..
Gee.. keep waiting.. I stopped waiting like a year ago.

---

### Post by lucazade on 2011-09-08
> **t1497f35 said:**
> Gee.. keep waiting.. I stopped waiting like a year ago.

:) 

If microsoft decided to kill InternetExplorer 6 (probably the worst browser ever and with the worst html implementation) with this initiative:
[http://www.ie6countdown.com/](http://www.ie6countdown.com/)
there is still a hope to see a web w/o flash!

---

### Post by xebian on 2011-09-08
> **pqwoerituytrueiwoq said:**
> assuming you are not using kde this is all you need from the file
(only the 1st 2 files changed since beta 2)
```
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/bin/flash-player-properties
/usr/share/applications/flash-player-properties.desktop
/usr/share/icons/hicolor/16x16/apps/flash-player-properties.png
/usr/share/icons/hicolor/22x22/apps/flash-player-properties.png
/usr/share/icons/hicolor/24x24/apps/flash-player-properties.png
/usr/share/icons/hicolor/32x32/apps/flash-player-properties.png
/usr/share/icons/hicolor/48x48/apps/flash-player-properties.png
/usr/share/pixmaps/flash-player-properties.png
```

You only need this

```
/usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by pqwoerituytrueiwoq on 2011-09-08
> **xebian said:**
> You only need this

```
/usr/lib/mozilla/plugins/libflashplayer.so
```
unless you want adobe flash preferences
right click some flash and try to open global preferences  my guess is yuo will get a error is you don't have [FONT="Courier New"]/usr/bin/flash-player-properties[/FONT]

---

### Post by pqwoerituytrueiwoq on 2011-09-08
> **lucazade said:**
> :) 

If microsoft decided to kill InternetExplorer 6 (probably the worst browser ever and with the worst html implementation) with this initiative:
[http://www.ie6countdown.com/](http://www.ie6countdown.com/)
there is still a hope to see a web w/o flash!
if we are lucky it will die with ipv4

---

### Post by jbicha on 2011-09-08
64-bit users, please use sevenmachines' PPA rather than downloading directly from Adobe. Adobe continually has security vulnerabilities which require updating and the automatic updates from a PPA are a big help in making sure you're secure. 32-bit users are probably better off just using the supported version 10 in the repositories for now.

[https://launchpad.net/~sevenmachines/+archive/flash]("https://launchpad.net/%7Esevenmachines/+archive/flash")

---

### Post by effenberg0x0 on 2011-09-09
Hey Jeremy, can you provide a little more info? I am curious as to why and how the files in this ppa would differ from the ones from Adobe (considering the ppa owner probably has no ability to fix any bug without the source code)? Unless he's Fravia+ himself, brushing bytes of the lib through obscure methods? :P


Thanks,
Effenberg

---

### Post by ft_ on 2011-09-09
imho, it should be a good idea to put the 64 bits beta release in ubuntu repos since it works much better than 32 bits 10.3 release ?

---

### Post by SevenMachines on 2011-09-09
> **effenberg0x0 said:**
> I am curious as to why and how the files in this ppa would differ from the ones from Adobe (considering the ppa owner probably has no ability to fix any bug without the source code)? 
Of course, theres no difference, binary patching is legally rocky ground depending on your geography so can't be done. As with all the proper flash packages, they just download from adobe on install. There may be a benefit in that the packages set up alternatives so that one install works with a variety of browsers, and will auto update your system ( as long as I keep regularly updating anyway :) )  But aside from that, theres no inherent benefit, in fact, if no-one was to use the ppa I could at last dump it after 2 frustrating adobe beta years!

---

### Post by SevenMachines on 2011-09-10
Oh, almost forgot, but just a quick mention for [lightspark]("http://sourceforge.net/apps/trac/lightspark"), flash will be around for a while yet and they're doing a good job of working away to provide an open source version for newer flash (gnash for older). Still a lot of work to do but its an active project so worth helping if anyone can...

---

### Post by _d_ on 2011-09-10
Can't wait for the full release of 11, seeing as how the RC is already working pretty much flawlessly on 64bit. :)

Can finally watch Hulu videos full screen without the chop that is appearing on 10, not to mention better performance on 720p and 1080p videos.

---

