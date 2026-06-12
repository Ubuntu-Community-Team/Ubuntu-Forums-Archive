---
title: "How do I improve GUI responsiveness and fix sound?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by HolyDiver24 on 2008-11-21
Hi, I've visited this forum a lot over the last few years and have found it really helpful but never felt the need to register as almost all my questions have been asked by someone else. 
However, I've got some problems though that have me stumped and I haven't been able to find the answers using search. I figured the easiest way is to ask these questions myself.

_1. I find Linux feels slow compared to Windows._
Almost all interactions with the GUI in Linux feels slower than in Windows. This might be a non-issue for most people, but being somewhat of a perfectionist it bugs me that whenever I boot into my Windows partition I find everything to be more responsive.
I really believe Linux's design philosophy is fantastic and believe me, I really WANT to use it but I can't deny that Windows just responds faster.
To be specific, I notice Linux is slower than Windows every time I
[LIST]
[*]Resize a window
[*]Minimise/Maximize a window
[*]Drag a window
[*]Switch tabs in Firefox
[*]Scroll in any window
[*]Open a menu
[/LIST]

Now, to be fair, I run a fairly modified/tweaked installation of XP (with many unnecessary components/services stripped away) but I don't believe this accounts for the problem - there's no reason IMO why Linux shouldn't be just as responsive as (a tweaked) Windows if not more so.
I'm currently using Xubuntu (which, while a huge improvement over Gnome, is still slow). In the past I have tried ArchLinux and Openbox, which is about as lightweight as I can think of, and I *still* found the unresponsiveness of the GUI frustrating.
I've experienced this on three machines, too.

My current machine's specs are:
AMD Athlon64 3200+
1GB RAM
Nvidia GeForce 8600GT
320GB SATA HDD

The nearest I've come to an explanation is that Linux's GUI is slower than Windows because Window's GUI is built into the core of the OS whereas X sits on top (I'm not too clear on the details). If someone could confirm/deny/elaborate on this I would be grateful.

[U]
2. I can't get the sound to work properly. [/U]
I have spent hours configuring dmix, ALSA and whatnot and have always found sound performance to be worse on Linux than in Windows. It doesn't matter what distribution I use the problem is the same.
In Linux the sound always sounds tinny and clipped. I have tried adjusting the volume, bypassing dmix, using libsamplerate upsample to 48KHz and nothing seems to work. I'll admit it could be some strange placebo effect but I'm sure there's a difference.
I'm using an on-board soundcard (AC97') which, while admittedly crappy, still sounds to my ears better in Windows than in Linux.
(On a side note, in Windows I use foobar2000 as my audio player. I haven't been able to find a Linux equivalent so perhaps someone more knowledgeable on OSS could recommend something.)


If not for these two things I would gladly ditch Windows. I love tinkering and Linux really makes a lot of sense to me.

---

### Post by techrush on 2008-11-21
You wont find many people willing to admit it but your complaints about the GUI responsiveness are valid at least in my eyes. something ive found that helps is enabling  XGL or AIGLX to accelrate the rendering of the desktop with your gpu. im not sure how much it actually helps but it certainly "feels" better. 

As for your 2nd complaint: buy a decent soundcard if you are gonna be so picky about your sound. Ive produced and edited audio professionally under linux and am pretty sure the onboard audio is your problem.

---

### Post by grazed on 2008-11-21
have you turned off cpu scaling? that will just about always slow down quick-response type actions. right click a gnome panel and add the widget, you can set your processor to idle at its highest frequency, which is what windows does by default in most configurations. other than that, desktop effects (compiz/beryl) will also slow down window drawing speed. window's window manager doesn't use 3d rendering, or high quality effects, so that may be improved by turning them off.

ubuntu by nature is a bit more demanding than xp, if that is what you are comparing it to. to be fair, xp was a new OS almost 8 years ago, while ubuntu is current. thus, slightly more demanding.

in response to the whole desktop environment inner workings, windows handles it the same way, mostly all contained in explorer.exe, which sits on top of the NT kernel.

audio is an entire different story, and does work dramatically different from linux. although audio lag is usually issue. if you aren't getting decent quality from pulse audio, you may have a hardware compatibility issue. =/

most of this you probably already know, but hopefully some of it may have helped in understanding. =)

---

### Post by handy on 2008-11-21
Are you using the proprietary nVidia drivers for your GPU?

Do you use compiz or similar?

I have instantaneous response to all of your display problems, on both of my machines; one running Arch/Xfce the other has Arch/Openbox, Sabayon/Gnome.  No compiz.

Both of my machines have lesser graphic cards than yours, one being an alu' 24" iMac (ATi) the other has a slightly better CPU, 2Gb RAM & a 7950gt/512 graphic card.

So If you too are using the proprietary drivers I don't know why your display is lagging.

Sound in Linux is not as good as it is on the windows or OS X, meaning the same hardware will sound better outside of Linux. That is just how it is at the moment, .

---

### Post by doorknob60 on 2008-11-21
YOu've installed the Nvidia binary driver correctly right? I don't see a reason for it going slow, see my specs in my sig (better than yours, but similar enough for comparison I guess). I use Openbox in Arch, and it's blazing fast, everything's a lot faster than Windows. Even the "clunky" distros (like Ubuntu and Kubuntu) worked better than Windows. For sound, maybe give OSS4 a shot. I've heard good things about it (literally if you know what I mean), but on my sound card it has minor problems so I stilll use ALSA< but I do think it might have sounded better still. Another thing you could try is Compiz because Nvidia 8xxx series supposedly has really bad xrender performance, which sounds like what you're experiencing. Try manually installing the very latest Nvidia driver from their site (if a beta one's out use that even). I haven't noticed it much, but quite a few people have complained about it. Compiz will eliminate the Xrender problems, but could use up more resources. Anyways, there's no reason that Windows should be that much faster.

---

### Post by Moustacha on 2008-11-21
2D acceleration on 8-series and up sucks pretty bad under linux. It's more nvidia's fault than linux. 7-series and down are better for nvidia.

---

### Post by HolyDiver24 on 2008-11-21
> **handy said:**
> Are you using the proprietary nVidia drivers for your GPU?
Yes - version 177

[quote=doorknob60]Another thing you could try is Compiz because Nvidia 8xxx series supposedly has really bad xrender performance, which sounds like what you're experiencing.[/quote]
That could be it. Things seem to improve somewhat with Compiz enabled.

Understand that this is not earth-shattering performance issues I'm talking about. The OS is perfectly usable. I wouldn't say anything is "broken" per se, I'm just trying to account for the difference.

Take resizing a window for example - in Windows* it is quite sensitive. As I resize the window gets redrawn so quickly that it appears smooth to the eye. Doing the same thing in X there always seems to be a kind of 'stutter'. It's quite exaggerated in  compiz (set the resize mode to "normal"): dragging the corner of the window results in a 100-200ms delay, then the new window size gets drawn and the text in the titlebar visibly "jerks" to the center.

I notice this with everything - from menus popping up to scrolling. Scrolling in Firefox is particularly visible - try autoscrolling the same page in Firefox in both Windows and Linux. In Windows, the scrolling is smooth and stutter free. In Linux there is occasional stutter and the page appears to be redrawn slower. 

Like I said, this stuff is fairly trivial. It's like the difference between playing DOOM 3 at 25FPS and 120FPS or the difference between a 128Kbps mp3 and CD quality.

*note that in Windows I use the "classic" theme without pixmaps

EDIT:
[quote=Moustacha]
2D acceleration on 8-series and up sucks pretty bad under linux. It's more nvidia's fault than linux. 7-series and down are better for nvidia.[/quote]
That would probably explain it.

---

### Post by cardinals_fan on 2008-11-21
I have very similar specs (slightly older video card), and my system *howls* with speed.  I use a lightweight distro (little included by default) and minimal software.

---

### Post by Grant A. on 2008-11-21
It's only slow depending on how you set it up. Ubuntu/Kubuntu (Even Xubuntu) come with a ton of bloat. If you want speed, try a standalone wm. Or even a tiling wm for real speed. I wouldn't recommend xmonad for the latter however, it's haskell deps make it a heavy install.

---

### Post by ZuLuuuuuu on 2008-11-21
For me:

When desktop effects are on: It is very slow, nearly as slow as Win XP but a little faster.
When desktop effects are off: It is a little slow, much faster than Win XP.

My main complaint is when surfing the web, it is very slow scrolling web pages with some flash animation or some fancy stuff on it. I tested it and I cannot even open more than 3 tabs on MySpace :) This is not the case on Win XP.

By the way, Intel drivers are installed (onboard graphics card).

---

### Post by FuturePilot on 2008-11-21
> **HolyDiver24 said:**
> 

Take resizing a window for example - in Windows* it is quite sensitive. As I resize the window gets redrawn so quickly that it appears smooth to the eye. Doing the same thing in X there always seems to be a kind of 'stutter'. It's quite exaggerated in  compiz (set the resize mode to "normal"): dragging the corner of the window results in a 100-200ms delay, then the new window size gets drawn and the text in the titlebar visibly "jerks" to the center.

What you described with Compiz is a known bug with the bad resizing performance.

---

### Post by -grubby on 2008-11-21
It largely depends on hardware, and video card drivers are often to blame. Compiz was never brilliantly fast for me, neither gnome.

---

### Post by grazed on 2008-11-21
> **ZuLuuuuuu said:**
> 

My main complaint is when surfing the web, it is very slow scrolling web pages with some flash animation or some fancy stuff on it. I tested it and I cannot even open more than 3 tabs on MySpace :) This is not the case on Win XP.

yeah, unfortunately that's just adobe's crappy flash implementation in linux. hogs a ton of cpu.

---

### Post by OffHand on 2008-11-22
> **ZuLuuuuuu said:**
> For me:

When desktop effects are on: It is very slow, nearly as slow as Win XP but a little faster.
When desktop effects are off: It is a little slow, much faster than Win XP.

My main complaint is when surfing the web, it is very slow scrolling web pages with some flash animation or some fancy stuff on it. I tested it and I cannot even open more than 3 tabs on MySpace :) This is not the case on Win XP.

By the way, Intel drivers are installed (onboard graphics card).

That is probably this [bug]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/223238")

---

### Post by Pogeymanz on 2008-11-22
Unfortunately, I also have an 8-series Nvidia card and it does stutter on some of those simple things like resizing windows. Like you said, it isn't earth-shattering and I usually don't even notice it, but it is a little annoying. I always hope the next nvidia driver will fix it, but it hasn't yet...

And it has nothing to do with the settings. I tried using the built-in intel graphics on this same machine and the 2D stuff did work better, but of course compositing and 3D was no good.

---

### Post by Ub1476 on 2008-11-22
Linux is very fast, but what you enconter is issues which you can relate to the nvidia driver. Graphic drivers for Linux is much worse than Windows atm. At least they're getting better and better.

---

### Post by inigomontoya on 2008-11-22
Try using the 180.08 beta drivers. [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by argie on 2008-11-22
> **HolyDiver24 said:**
> 
I notice this with everything - from menus popping up to scrolling. Scrolling in Firefox is particularly visible - try autoscrolling the same page in Firefox in both Windows and Linux. In Windows, the scrolling is smooth and stutter free. In Linux there is occasional stutter and the page appears to be redrawn slower. 


There are many bugs in Firefox on Linux that aren't present in the Windows version which directly affect scrolling speed. I have the same problem (but much worse, on a rather more powerful computer) and it hasn't been fixed yet.

---

### Post by GrantsV on 2008-12-13
Hi there,

Just a quick message to let you know NVidia 8 series is frustratingly SLOW on Linux with or without new drivers - even 180.00+ with all the Xorg options.  Its a known issue to the driver team at nvnews.net forums.  

I have run linux distos on many other machines, with new onboard NVidia video and also intel, ATI and they are pretty as fast.  But still I havent experienced anything is as fast as slimline fresh install of XP.

But Linux GUI response on NVidia 8600 is intolerable, with other graphics cards and Linux works nicely enough to not be an issue.

PS. Have you tried i686 version????  You never know.

All the best,
GrantsV

---

