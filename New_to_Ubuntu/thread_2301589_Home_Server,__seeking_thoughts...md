---
title: "Home Server,  seeking thoughts.."
date: 2015-11-03
forum: New to Ubuntu
---

### Post by andrew268 on 2015-11-03
Greetings! 

I am looking at what methods I could use to breathe life into an AMD Phenom 2 based former gaming desktop. 

As of yet,  my Ubuntu (and linux in general)  experience is limited to a couple dabblings in the past on a laptop. 

My goals-
Local network file server for use by connected windows 10 machines. 
A Booru style image board accessible through the internet to remote family members..  We have been wanting to collaberate family pictures for decades. 
A modded minecraft server available for a small group of friends via internet. 
Streaming media (Netflix,  Hulu,  Amazon,  etc.) to the entertainment center where the computer will reside.  

Would Ubuntu be a reasonable choice to persue?

Thanks in advance for any advice. 

A.

---

### Post by TheFu on 2015-11-03
Please post exact  CPU, GPU, RAM, and disks.

With a $140 current-generation box, the answer is a clearly yes. Can't say anything about this old equipment. too many unknowns, especially for video processing. That is much more dependent on the GPU  **and** available video codec drivers.

For a simple CIFS server, almost anything is fine if performance is not a big deal. Note that Win10 CIFS appears to work differently-there's some settings on the Win10 side to make it work better.
Mindcraft is a hog - RAM and CPU.
Photo sharing is easy, but placing any "service" on the internet is opening the door for some nasty attacks.  Security skills are required. As someone new-to-linux, you really need to have a plan for what you'll do when (not  if) this system is hacked and pwn'd remotely.  I have a plan for when my  systems get cracked and I've been running internet Unix servers for almost 25 years.   Got hacked (servers) twice that I know. Last  time was 2002. Being paranoid is an important skill.  I see attacks on my servers constantly. For example, the reverse proxy that catches most of these cracker attempts currently has approximately ...
```
$ sudo iptables-save |wc  -l
6787
```
that number of firewall rules  - really  about 5-10 less.

I'd recommend that you run this server on the LAN only for 6-12 months before putting it on  the internet. Get a little practice, hands-on experience. Right now you don't know what  you don't know.  Nothing is hard, but there are just lots of new  skills  to be  learned.

Plan for the worst, but hope for the best.

---

### Post by eddiefiggie on 2015-11-03
I'm in a similar place as the OP.  

And as TheFu has suggested, I haven't exposed my server to the internet just yet.  I'll tell you it has been fun learning!

I initially went down the Samba path for file sharing.  Meh, perhaps it was my expertise but it felt too complicated for my skill set and I didn't care for the interface I was using.

I have opted into using "owncloud".  I highly suggest you look into this.  I'm working on building mine this week, but everything I've read so far seems to be good stuff.

Hope this feedback helps.

---

### Post by sandyd on 2015-11-03
Some software reccomendations:

Local network file server for use by connected windows 10 machines. 
A Booru style image board accessible through the internet to remote family members.. We have been wanting to collaberate family pictures for decades.
[LIST]
[*]Gallery
[*]Pwigo
[/LIST]

A modded minecraft server available for a small group of friends via internet. 
Test first. Your CPU must provide adequate single-thread performance.

Streaming media (Netflix, Hulu, Amazon, etc.) to the entertainment center where the computer will reside.
Note that this becomes tricky if you want to use something like Kodi. So far, just playing it in chrome seems to be most reliable.
If you watch all your content over Netflix/Hulu/Amazon/etc, I recommend simply using chrome with a wireless remote/keyboard.

Netflix Options:
[NetfliXBMC]("http://forum.kodi.tv/showthread.php?tid=211574") works, though a bit iffy and breaks once in a while
[Advanced Launcher ]("https://github.com/Angelscry/plugin.program.advanced.launcher")- NetFlix works in chrome.
Hulu Options:
[Advanced Launcher ]("https://github.com/Angelscry/plugin.program.advanced.launcher")- Hulu works in chrome.
There used to be a [hulu plugin]("http://kodi.wiki/view/Add-on:Hulu"), but it has since stopped working.
Amazon Options:
[Advanced Launcher ]("https://github.com/Angelscry/plugin.program.advanced.launcher")- Amazon works in browser. Not tested myself, don't have amazon prime
There used to be a [amazon plugin]("http://forum.kodi.tv/showthread.php?tid=215255"), but it no longer works.

---

### Post by andrew268 on 2015-11-05
Thank you for all the replies!  I appreciatenthe input. 

Hardware- 
ASUS M4A79T Deluxe
AMD Phenom 2 x3 black
8GB RAM
GeForce GTX660 video
smattering of older SATA drives between 300GB and 1TB
IDE DVD drive

I do like the idea of just uding Chrome for streaming,  that would be a simple method. 

A.

---

### Post by TheFu on 2015-11-05
Is the "black" a 720 model? I tried to look up the performance and there were multiple options.  Regardless, this CPU should be able to transcode multiple HiDef video streams for playback by devices on your network.

For the DRM content, Chromium/Chrome or a Roku is probably best. Roku being the least-hassle solution. The roku Plex-app requires signup with the Plex website, which I've never done.

The cooling for that box must be noisy. I'd put it in a closet somewhere and use a Raspberry-Pi 2 as the display. OTOH, if you are used to the noise from any Xbox, then this probably doesn't matter. I really love the Kodi interface. Much nicer than anything else I've seen - nicer than a Roku by far but it doesn't handle DRM as well.

Actually, a box like this can be a VM host quite easily which will let you logically segment the security aspects - like the photo gallery. Put that inside a web-server VM and lock it down.

---

### Post by gordintoronto on 2015-11-05
I have a somewhat similar computer which is still my "high performance" computer. I dual boot Linux Mint 13, which is based on Ubuntu 12.04, and Xubuntu 15.10. Both provide excellent performance. I dabble in a little video editing, and have no complaints. I also do a little file serving.

Your ISP might block your attempts to host Internet services.

My system: Phenom II X2 550, 16 GB of memory (I was testing Windows Server booting from a separate hard drive) Geforce 9400 GT, WD Black 640 GB.

I recently cleaned the CPU heat sink and replaced the CPU thermal paste, which cleared up some overheating problems. Now the system idles at 39 C.

With multiple hard drives, after installing Linux, you should spend 20 minutes figuring out how fstab works.


> **andrew268 said:**
> Thank you for all the replies!  I appreciatenthe input. 

Hardware- 
ASUS M4A79T Deluxe
AMD Phenom 2 x3 black
8GB RAM
GeForce GTX660 video
smattering of older SATA drives between 300GB and 1TB
IDE DVD drive

I do like the idea of just uding Chrome for streaming,  that would be a simple method. 

A.

---

