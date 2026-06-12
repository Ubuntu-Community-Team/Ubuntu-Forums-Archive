---
title: "Ubuntu on Netbook"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-07-10
I have been requested by one of my friends to install Ubuntu on her netbook.
I tried searching the forum for minimum recomended spec for Ubuntu or Xubuntu but unfortunately could not find out any detailed info.
Does any one has any experience with this ? The spec of netbook is low (i will get to know the details tomorrow).
But meanwhile i wish to prepare some bootable usb flash-drives for the installation (as there is no CD drive).
Any suggession ?

---

### Post by mastablasta on 2013-07-10
depends on specs, but 1 GB and latest Atoms (but the ones with linux GPU driveres) or AMD E-300, 400 or higher is good should be ok for Ubuntu.

other options are of course Xubuntu, Lubuntu or KDE with netbook plasma interface.

---

### Post by 3dmatrix on 2013-07-10
I might even think of going down to 12.04 (if it helps). In that case any idea how much RAM is needed for smooth running of Ubuntu 12.04 or Xubuntu 12.04  ?

---

### Post by 3rdalbum on 2013-07-10
If it is one gig of RAM anf any Intel Atom then Ubuntu 13.04 will be just fine. Be aware 13.04 is only supported for another 7 months, so you would need to upgrade it then and again. Whereas 12.04 is good for nearly four more years due to it having long term support. You might prefer 12.04 for that reason.

---

### Post by wsxadf on 2013-07-10
I am currently using Ubuntu in my netbook with atom 1.6ghz with 1gb ram. I first tried default ubuntu 13.04. It worked, but quite slowly and heavily. I changed it to ubuntu minimal installation because I do not need fency gui. It works quite well now. :D

---

### Post by sudodus on 2013-07-10
See the first post in this link concerning what CPU horsepower, RAM size and Ubuntu version and flavour you might need: [Old hardware]("http://ubuntuforums.org/showthread.php?t=2130640")

I think Xubuntu 12.04.2 LTS with end of life April 2015 is a good choice. If you are prepared to help upgrading to new versions, Lubuntu 13.04 might be the best choice. Another alternative is to install Ubuntu 12.04.2 LTS and tweak it according to this link: [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

By the way, do you intend to make a dual boot install, or will it be *ubuntu only?

---

### Post by snowpine on 2013-07-10
Here is a list of some Ubuntu-certified netbooks: [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

If your netbook has comparable specs to the supported models, then you should be okay. :)

---

### Post by verymadpip on 2013-07-10
I think knowing the make & model of the graphics chip would be useful.
Bitter personal experience tells me so :)

I'm running Lubuntu 13.04 32 bit on my netbook very happily at the moment.

---

### Post by edb66083 on 2013-07-10
I agree with verymadpip. Some netbooks have trouble with their graphics cards playing nice with Ubuntu.

Can you provide the make and model and see if anyone has had a bad experience?

---

### Post by Vormeph on 2013-07-10
On my netbook I have Xubuntu 13.04 installed. I couldn't install the later version of Ubuntu past 12.04 for 32-bit. Xubuntu/Lubuntu tend to be more lighter versions of Ubuntu, which the base distro doesn't really embrace because of Unity. Good luck!

---

### Post by farrinux on 2013-07-10
I have a 4 year old Gateway LT20 that is currently dual booting win xp and Ubuntu 12.04LTS 32 bit. The specs on the netbook are cpu Intel atom N270 @1.6 ghz x 2, 1 gig of memory and Intel graphics 945GME x86/MMX/SSE2.  It does run Ubuntu 12.04 a little slow.  But it does not run win xp fast either.  They are about the same.  If you want it to be snappier try Xubuntu or I think Lubuntu is the other light desktop.  I would put a LTS version on though. IMHO.

---

### Post by HermanAB on 2013-07-10
Xubuntu should do fine, otherwise Fedora XFCE spin for a similar setup from a different distro house.

---

### Post by FiremanEd on 2013-07-10
Herman,  Have about the same specs on my netbook (Acer Aspire one) but added an additional 1GB ram.  I run Xubuntu 12.04 on it and it's snappy and very reliable.
Cheers.
Ed

---

### Post by 3dmatrix on 2013-07-12
I is a Toshiba NB 505-SP0114KL
Has Dual Core Intel Atom N455 @ 1.66
2064 Mb RAM
Mesa DRI Intel IGD x86
Audio HDA Intel

I have installed Xubuntu 12.04 on it. Its working but not too great. Movies are jerky. and at times some functions have lag and delay.
Any better alternative or anyway to improve performance ?

---

### Post by mastablasta on 2013-07-12
you ned to check which GPU chip is on that Atom. They outsourced some GOU chips and the partner never made linux drivers. so there are some nasty patches out there. but in any case they wouldn't work as well as in widnows.

---

### Post by edb66083 on 2013-07-12
If one of the functions that lagging is Thunar file manager, that is a bug. Thunar is trying to find all your networks, or something like that, and it takes forever to load. It can easily be fixed. If it is most of the functionality, then it is most likely your graphics card drivers.

---

### Post by verymadpip on 2013-07-12
Hi there.
+1 on the Thunar thing.

I have an MSI Wind U180 with GMA3600 (PowerVR based) graphics chip - quite problematic IMO. (N2600, 1.6GHz Atom CPU, 1Gb RAM).
Lubuntu 13.04 32 bit runs spectacularly well on the liitle thing, far more responsive than Win 7 Starter.

Whether this continues until LTS release in 2014 remains to be seen.  I remain hopeful.

---

### Post by 3dmatrix on 2013-07-12
The problem is in watching videos in browser (flash) and watching video in VLC. The problem is not with flash or internet, it must be somthing else, may be graphics.
For eg HD videos in VLC just can not run. Again no prob with codecs.
Though Ubuntu and its forks are my first choice but still just wish to know if there is any alternative to Xubuntu, which would be good in this case.

---

### Post by sudodus on 2013-07-13
Start with 12.04.
If Xubuntu will not work try Lubuntu!
If Lubuntu will not work, try Knoppix!

---

### Post by 3rdalbum on 2013-07-13
Netbooks are not very good at playing video. They are passable for DVD quality, but not for anything better than that.

---

### Post by Paqman on 2013-07-13
> **3rdalbum said:**
> Netbooks are not very good at playing video. They are passable for DVD quality, but not for anything better than that.

There wouldn't be any point in trying to play anything above that resolution, since most netbooks only have 600px of vertical resolution anyway.

[Arista]("apt:arista") is a good re-encoding tool that has presets for various devices, one of them being netbooks. Obviously you'll probably want to do the transcoding on a machine with a bit more horsepower than the netbook itself or it'll take forever.

---

### Post by verymadpip on 2013-07-13
> **3dmatrix said:**
> The problem is in watching videos in browser (flash) and watching video in VLC. The problem is not with flash or internet, it must be somthing else, may be graphics.
For eg HD videos in VLC just can not run. Again no prob with codecs.
Though Ubuntu and its forks are my first choice but still just wish to know if there is any alternative to Xubuntu, which would be good in this case.

Which browser do you use? Maybe try a different one?
Lubuntu is lighter than Xubuntu. (I know I'm pushing this - I've had a good result, which is meaningless to anyone else...)
There are lighter distros - Puppy, Slitaz etc, Knoppix has had a mention already.

---

### Post by Rob Sayer on 2013-07-13
That cpu apparently has the GMA 3150 gpu.  There apparently aren't any compatibility problems with the linux drivers like with my cedarview netbook but it's not a high performance graphics chip.

As mentioned, I wouldn't expect any netbook to have good performance with HD video.

I run kubuntu on my 1Gb atom 2600 equipped netbook.  It doesn't take that much more memory than xubuntu (which I had on there originally).  It runs a little bit slower than xubuntu but it has so many more features that for me it ends up running faster.

Especially since I won't use any other file manager except dolphin (which or course is the default kde manager) and that runs *extremely* slowly in xfce.

I've also found that kde has better video rendering performance than all the other desktops I've tried ... I haven't used lubuntu but I've tried all the other desktops ... as long as you go into effects -> advanced and tell it to turn off the compositor when going full screen.

Also, I don't think vlc would be the best choice in a lower performance machine.  As of v. 2.0 you can't set up file stream caching anymore and I find that makes a big difference.  God knows why they did that ...

I use smplayer with the local file stream cache set to 8192Kb, as recommended somewhere in doom9's forum.  It works very well, quite noticeably on a much more powerful machine.  I still have vlc installed but only use it if the file has some flaky codec that makes smplayer work less well, and that's rarely.  Vlc is overrated as the "play anything" video player.  Smplayer is better in that respect.

---

### Post by Grafens on 2013-07-13
For HD video as mentioned above a netbook just isn't powerful enough.
But if you want to do multitasking you'll get a noticeable boost if you install 2gigs of RAM. My netbook(dell inspiron mini 10) came with only one gig, searching the internet said it was non-upgradable but it is, it takes regular sodimm memory. Very tricky to take the thing apart though.

---

### Post by snowpine on 2013-07-13
My netbook does reasonably well up to 480p with mplayer. 
Higher quality than that, or streaming flash in the browser, nope.

---

### Post by 3dmatrix on 2013-07-14
I use Firefox and VLC player
The main problem is in playing online movies !
what can be done for that ?
Internet speed is not a problem.

---

### Post by sudodus on 2013-07-14
What resolution can you play and where do the problems start? Have you tried smplayer, recommended by *Rob Sayer*?

---

### Post by snowpine on 2013-07-14
> **3dmatrix said:**
> I use Firefox and VLC player
The main problem is in playing online movies !
what can be done for that ?
Internet speed is not a problem.

Your best option is to watch the movies on a faster computer.
If that is not an option, your 2nd best option is to download the video to your netbook hard drive and watch it with VLC or mplayer (instead of streaming in your browser).
The 3rd best option is to view the video at the lowest resolution/quality possible.

I say this based on my years of experience with two different models of Atom-processor, Intel graphics netbooks. :)

---

### Post by 3dmatrix on 2013-07-14
> **snowpine said:**
> Your best option is to watch the movies on a faster computer.
If that is not an option, your 2nd best option is to download the video to your netbook hard drive and watch it with VLC or mplayer (instead of streaming in your browser).
The 3rd best option is to view the video at the lowest resolution/quality possible.

I say this based on my years of experience with two different models of Atom-processor, Intel graphics netbooks. :)

Thanx ! I will have to give her the sad news   :)

---

### Post by Rob Sayer on 2013-07-14
While I agree that dl'ing the video and then watching it with a player with proper buffering is a vetter option, I think the OP said it's actually for a friend.  Who may not want to deal with all this.

Unfortunately I don't really think there's a perfect solution for watching 720p or better video on a netbook, running linux or whatever OS.  There's another thread on this board from someone who wanted to install xbmc on his netbook and use it as a media server.  It's a 1Gb atom 2600/cedarview netbook like mine, which *does* have hardware support problems unllike the one in this thread.  I don't know where to start with *that* case.

In this case, I'd suggest what snowpine said and stream in no more than 480p.

---

### Post by snowpine on 2013-07-14
Option #2 is not that hard; I belive there is a youtube download application in the Ubuntu Software Center. I have successfully viewed low-quality video even on my ancient Pentium 3 by watching it from the hard drive using mplayer. :)

---

### Post by 3dmatrix on 2013-07-14
> **Rob Sayer said:**
> While I agree that dl'ing the video and then watching it with a player with proper buffering is a vetter option, I think the OP said it's actually for a friend.  Who may not want to deal with all this.

Unfortunately I don't really think there's a perfect solution for watching 720p or better video on a netbook, running linux or whatever OS.  There's another thread on this board from someone who wanted to install xbmc on his netbook and use it as a media server.  It's a 1Gb atom 2600/cedarview netbook like mine, which *does* have hardware support problems unllike the one in this thread.  I don't know where to start with *that* case.

In this case, I'd suggest what snowpine said and stream in no more than 480p.

I think not much can be done in this case, Thanx all of you !
I think i will return the netbook.

---

