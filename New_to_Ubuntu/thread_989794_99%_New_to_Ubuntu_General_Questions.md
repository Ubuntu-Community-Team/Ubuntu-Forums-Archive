---
title: "99% New to Ubuntu: General Questions"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by ugly_duckling492 on 2008-11-22
I'm about to install Ubuntu on my computer and I want to know if there's anything you wish someone told YOU before you installed it. I also have my own questions:

Do I need to worry about drivers for the following hardware:
- Mouse Pads
- DVD/CD Drives
- Keyboards
- Bluetooth Devices 


I have a friend who told me he has a friend, who can play windows games on his linux computer. He didn't say how. Is it a virtual machine? I'm a gamer that needs to convert to Linux (don't talk me out of it, you don't know the whole story.) How would I do my gaming?

How problematic is dual booting windows and ubuntu? what are the pros and cons? 

This questions kind of ties in to the gaming one. What if I wanted to run Windows/Mac only software? (Yes, I know there are opensource alternatives to just about everything)

Hmm... I'll post more questions later on.

---

### Post by nhasian on 2008-11-22
i recommend downloading and burning the Ubuntu 8.10 liveCD.  then you can boot off the CD and test ubuntu without installing it.  if all your hardware works then you can proceed with the installation.

here's a great guide to installing with dual booting:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by sqrooup on 2008-11-22
You should have no problems with Keyboards or CD/DVDs, and I noticed some Bluetooth applications are available.

Not sure about "mouse pads" though, do you mean "graphic tablets"?

---

### Post by Gone fishing on 2008-11-22
Dual booting would be a good option then you could play games in Windows although although there are alternatives see:

[http://maketecheasier.com/4-ways-to-play-windows-game-on-linux/2008/08/19](http://maketecheasier.com/4-ways-to-play-windows-game-on-linux/2008/08/19)

Crossover office allows a large number of productivity applications such as MS Office, Dreamweaver to run well on linux.

Curious to know what your end of Windows experience was 	:grin:

---

### Post by jimmy the saint on 2008-11-22
The problem with a virtual machine is that you will not have 3d acceleration.  You will be VERY limitied in the Games you can reasonably play.  That said, unless you are a hardcore gamer, there are good games that are native to linux.  I don't play games except to kill some time now and then or distract myself, but when I do, I play alien arena and UrbanTerror.  Both fun Multiplayer games.  If you really need the popular new games though, dual booting is probably for you.

---

### Post by mbsullivan on 2008-11-22
> **ugly_duckling492 said:**
> 
- Mouse Pads
- DVD/CD Drives
- Keyboards
- Bluetooth Devices 
[\QUOTE]

You shouldn't... For the bluetooth devices, there is good bluetooth protocol support in Linux, but it doesn't mean that there are necessarily applications to support all of your devices! Something simple (like a bluetooth headset) shouldn't pose any problem so long as you have a Linux app you want to interact with.

> I have a friend who told me he has a friend, who can play windows games on his linux computer. He didn't say how. Is it a virtual machine?

As somebody else said, a VM probably wouldn't be a good choice for gaming, due to (1) generally poor latency and (2) no 3D acceleration. So, unless your definition of "gaming" is ski free, you'd probably have to try one of two things:

(1) Use a program to natively execute windows programs under Linux. The two most popular apps for games are Wine (free) and Cedega (proprietary, but based off of Wine). If these work for your games, great... they'll probably run as fast or faster than under Windows. However, they are not (even close to) perfect, and introduce lots of bugs to many games. You can judge this for any given game from the [Wine app database]("http://appdb.winehq.org/") and/or [Cedega database]("http://www.cedega.com/gamesdb/").

(2) Dual boot. This isn't really that big of pain (much easier than it used to be). If you had the option, I might suggest putting each OS on a different harddrive, just to minimize the chance that you might hose one from the other. The biggest downside, probably, is the time required to setup, maintain, and switch between your two operating systems. Biggest upside (regrettably) is that it's the most flexible solution for gaming.

[QUOTE]What if I wanted to run Windows/Mac only software?

This is similar to the gaming question. Two options are basically either to try it under Wine or run it in a VM. I'm not aware of any way to install Mac applications, but you could run them under a VM.

Mike

---

### Post by HittingSmoke on 2008-11-22
> **ugly_duckling492 said:**
> I'm about to install Ubuntu on my computer and I want to know if there's anything you wish someone told YOU before you installed it. I also have my own questions:

Do I need to worry about drivers for the following hardware:
- Mouse Pads
- DVD/CD Drives
- Keyboards
- Bluetooth Devices 


I have a friend who told me he has a friend, who can play windows games on his linux computer. He didn't say how. Is it a virtual machine? I'm a gamer that needs to convert to Linux (don't talk me out of it, you don't know the whole story.) How would I do my gaming?

How problematic is dual booting windows and ubuntu? what are the pros and cons? 

This questions kind of ties in to the gaming one. What if I wanted to run Windows/Mac only software? (Yes, I know there are opensource alternatives to just about everything)

Hmm... I'll post more questions later on.

I'm an ex-Windows-gamer turned Ubuntu freak recently as well. There are quite a few popular titles that run on Linux under WINE. Not a lot by any means, but enough to satisfy me. I actually started getting more into console gaming after switching to Ubuntu. Since the advent of Xbox live, the PC isnt the only multiplayer platform.

I tried dual booting but I always just booted into Windows and never really had a chance to appreciate Ubuntu. (Rebooting every time I decide to switch what I'm doing strikes me as ridiculous) So eventually I just went straight Ubuntu.

Like what has been said. Burn a Live CD. Get an 8.10 CD and try that. If everything works great go with it. I've had some bad luck so far with 8.10 no non Nvidia based graphics. If anything doesn't work, try 8.04 instead.

---

### Post by 3rdalbum on 2008-11-22
I'll answer your first question. There are two things that I wish someone had told me before I started with Ubuntu:

1. Don't expect it to work like Windows. Linux is an independent operating system that has roots in an operating system that is decades older than Windows. So, for instance, you don't have a C:\ drive in Linux. You rarely need to install "drivers" in Linux, and you especially don't need "anti-virus".

Ubuntu has a security system that prevents ordinary users from making system-wide changes. By default, you run as an ordinary user. If you want to run a command that requires low-level access to the hardware, or that will change system files, you need to prefix it with the word "sudo". Sudo tells Ubuntu to run the command as the root (administrator) user. By the same token, you can open a new file browser window as root; either install "nautilus-gksu" or run the command "gksudo nautilus".

2. Linux software is best installed from the Synaptic Package Manager. That should be your first stop for new programs, and it's where you can install the "nautilus-gksu" package that I just told you about.

If possible, avoid anything that doesn't come either in a repository or from a reputable Ubuntu-specific website like [www.get-deb.net](www.get-deb.net). Forget about finding new software by downloading it from the developer's website, as it will be in source code form that is not as easy to install (but has other benefits that you might appreciate later).

---

### Post by stalkingwolf on 2008-11-22
a third option is crossoverlinux.  It runs many win-apps quite well.

---

### Post by mbsullivan on 2008-11-22
> a third option is crossoverlinux. It runs many win-apps quite well.

Crossover's targeted towards office applications and some (popular) games, so it may work. Also, if you want to run MS Office or Photoshop 7, this may be the way to go.

Cedega's target market is games, so it should run a larger breadth of games stably.

Wine's more consistently updated than either, so a new version of Wine's always what I'd try first.

Mike

---

### Post by MunkyJunky on 2008-11-22
I highly recommend trying WINE for games. I'm a Ubuntu gamer, and I used to use WINE, but I got myself a free copy of Crossover Games & Crossover Linux (as well as the Mac versions, even though I don't own a Mac :) ) during CodeWeavers Lame Duck promotion. I must say, they are awesome, although I would recommend a higher-spec rig for decent gaming, but most new games require a decent spec anyway. Shouldn't really be a problem.

---

### Post by ugly_duckling492 on 2008-11-23
Thanks, everyone's helpful and supportive. I guess people might want to know why I might need to wipe windows.

I got to a Leadership and Entrepreneurship high school. One of it's highlights is the Junior Year Internship. My possible Internship would be with a company called Opensourcery.

[http://www.opensourcery.com/](http://www.opensourcery.com/)

I'm up for an interview in late December or early January and the CEO challenged me to wipe windows and go with a linux OS. I think I'll win Brownie Points if I do, and I'm ready for the change. If I get really good at the job, I'll know Linux inside out. Imagine what I could do then. I'm looking forward to it but now I start as a complete newbie and nothing more. I hope I don't say bye to my hard core PC gaming.

Just finished downloading Ubuntu and I'm gonna give it a go.

---

### Post by Paqman on 2008-11-23
> **ugly_duckling492 said:**
> the CEO challenged me to wipe windows and go with a linux OS.

Did you explain that you're a gamer? If so, wiping Windows is a baaaad idea. Linux does a lot of things well, gaming isn't one of them.

My advice:dual-boot. You may find some of your games run acceptably well through Wine, but most won't.

---

### Post by conradin on 2008-11-23
How do i post my own brand new thread in this forum?
My other question is that I have several networks I'm seeking to manage they are on various switches around the department. Some are windows clients, there are Macs, and some Linux boxes of various types. I need to be able to manage the content they are able to view via the internet, run an application (vb6.0 application) that interfaces instruments like spectrometers. I was considering a DNS server, but this looks like a lot of work that wouldn't give me the level of control I seek. I would ideally like to have a log generated when any system or instrument fails. A friend of mine suggested a VPN. Prior to this I was Using Windows Server 2003, which was largly insecure and difficult to configure in a practical way. What Sort of sever should I set up to achieve the level of control I need? All computer clusters currently are peer to peer.

---

### Post by oldos2er on 2008-11-23
If you want to run Windows software, use Windows. Most Win* games that require 3d hardware acceleration will not work (that's my understanding, at least). There are a very few exceptions, idsoftware games being one of them.

 You might want to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) .

 For help creating a dual boot system, read [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) , the links under 'Just beginning'.

---

