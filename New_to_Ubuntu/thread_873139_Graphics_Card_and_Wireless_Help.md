---
title: "Graphics Card and Wireless Help"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ergonomicdesign on 2008-07-28
So, I'm not sure exactly how to begin. I stopped using Ubuntu (Hardy Heron, 8.04) for about 3 months because I just couldn't get the graphics card or the wireless card to work on my laptop but wanted to give it a second go before school began. 

Right now, I'm on a Toshiba Satellite (A205-S5803) with the following features: 
Intel Pentium dual-core processor T2330 operating at 1.6GHz
Operating System – Windows Vista Home Basic
1 MB L2 cache
Up to 533 MHz Frontside bus
1GB of PC2-5300 DDR2 SDRAM memory (2 x 512MB); maximum memory capacity: 2GB
Realtek® 802.11b/g wireless LAN
ExpressCard/54 slot: also compatible with ExpressCard/34
Intel Graphics Media Accelerator X3100 with from 128MB to 251MB shared memory

Out of box, Ubuntu does work for the most part. I can surf the internet (I'm using it right now after all) but only through a hard-wired ethernet cord. The wireless doesn't work. I remember I tried to find the windows version of the driver for the Realtek Wireless card, but couldn't (it came as an .exe file) and when I tried extracting it, and using "Windows Wireless Drivers," it detected that the right driver was present, but I couldn't connect to any networks because none would be detect. (There are 5 networks around my house, and the router for my personal one is 3 feet from my computer). That's my first problem. 

But the more challenging one for me is that there's something wrong with my graphics card. If I play a video, only half the video would be displayed (if the player is in windowed mode) or (if the player is in maximized mode) the entire system would crash. I just don't know where to start with this problem. Flash based videos (i.e. youtube) would play fine more or less, but .avi or dvd's would cause a crash. 

What to do? Where to begin? Any help would be greatly appreciated!

Thank you.

---

### Post by echo314 on 2008-07-28
What method did you use to get your wireless working in the past? Did you try ndiswrapper? If not I would highly suggest looking into it. My friend had the same brand graphics card, and after a while I was able to get it working just following README files and the like. Try it out and tell is if you get stuck of course. 

Best of luck.

---

### Post by A4006 on 2008-07-28
I would tell you to use Envy to install proper video card drivers, but it only works on nVidia and ATI cards... perhaps check the manufacturer's web site for linux drivers?  For your wireless card, if you can find the windows drivers you can use NDISwrapper to get them working in Ubuntu.  I'll look around a bit and see if I can find any video drivers... hope this helps,
A4006

---

### Post by A4006 on 2008-07-28
This guide [http://ubuntuforums.org/showthread.php?t=506744]("http://ubuntuforums.org/showthread.php?t=506744") may help with installing some new video card drivers, which *hopefully* would make all your video issues go away. Be warned, you can hose up your system messing around with drivers, so be careful.  I've done it before (numerous times... I'm a slow learner), and it's not much fun.

---

### Post by papsynot on 2008-07-28
Note - my Ubuntu and Gnu/Linux's know-how rank: amateur

I got mad after a month of on and off testing with Linux distros. However I found how to make my Intel video card ( GMA 950 ) working great! 

First, disable Compiz-Fusion then update Intel drivers with this package (I still don't realize I was able to make one - lol)
[http://spazioinwind.libero.it/densou/xf86-video-intel_2.3.2-1_i386.deb](http://spazioinwind.libero.it/densou/xf86-video-intel_2.3.2-1_i386.deb) 
(please download with Right Click + Save As... or it won't start) and replace your xorg.conf with [mine](http://spazioinwind.libero.it/densou/xorg.conf) (before doing it check that your /etc/modules contains "agpgart", "intel-agp", "drm" and "i915"; they should be all built inside the kernel but I also add them in that modules list)
errr ... maybe skip to paste my monitor section because I customized it for an old CRT and I'm not sure how to set up for a laptop screen :(


Regarding video playback issue: I think the best choice would be Flash Player 10 (beta 1 dated May) and Gecko Media Player 0.63.3 or above (CAREFUL: avaiable ONLY on intrepid repositories) because the last one
contains Quicktime 7.4.5 plugin for Firefox .... and HD .mov Trailers are fully playable !

Also, this afternoon I tried to compile and to create a .deb for the new Intel 2.4.0 release but I had no luck. Checkinstall gave me an error output similar to "Error on Debian compiling policy, package creation failed". I heard that this version needs Xorg 1.4.x only but why worrying, my desktop pc works fine now ;) :P

---

### Post by Tom--d on 2008-07-28
Wireless, look below this.

And Graphics card, its been blacklisted, [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

But it shouldnt be that bad, at all!
Flash is not based on your gpu, it uses the cpu to render the video. (I think, correct me if im wrong)
Press ALT+F2 on the desktop. and type in gstreamer-properties
and on Video. Play around with it. (output)

---

### Post by ergonomicdesign on 2008-08-04
So, I used the gstreamer-properties, and when I went to video and hit test, my screen crashed. >< I couldn't click, just the empty void of blackness. 

I could only restart because I hit alt f2 --> sudo shutdown -r now.

oh well, any other tips?

---

### Post by ergonomicdesign on 2008-08-04
I'm scared to try that...because I have no idea how to undo it. 
<--- compelte novice at linux/ubuntu. Before this past year....I think the last linux-ish experience was when I had dos and windows 3.1

*edit* oh yeah, I fixed the wireless card problem.

---

