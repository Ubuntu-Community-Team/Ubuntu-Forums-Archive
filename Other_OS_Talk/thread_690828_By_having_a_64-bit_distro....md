---
title: "By having a 64-bit distro..."
date: 2008-02-07
forum: Other OS Talk
---

### Post by CM Xtasy on 2008-02-07
Will I be able to still use 32-bit programs or will they need to be ported to 64-bit?

---

### Post by gavintlgold on 2008-02-07
I would definitely not recommend using 64-bit. There are just so many programs that won't work with it. Since all programs must be packaged for 64-bit, many Ubuntu programs don't work at all, or there are problems. It's much harder in general to install stuff in a 64-bit environment.

There is a way to do a 32-bit chroot, but there isn't a noticeable speed increase with 64-bit, and if you can run in a 32-bit environment with your 64-bit CPU it's much easier.

The only thing about 64-bit is you can put much more RAM on your machine. If that's the case then there are quite a few programs, though proprietary apps (like flash support) are basically nonexistant for 64-bit.

Hope that helps. I used to use 64-bit but got sick of it and installed 32-bit.

EDIT: In the future 64-bit will be worth it, but for now 32-bit is still the standard, so there is less support for 32-bit. There's nothing wrong with the architecture or anything ;)

---

### Post by Alex_Fingers on 2008-02-07
You'll be able to use 32bit programs with a 64-bit operating system but they wont make use of the additional power of your computer.

However, it isn't an issue that I've had really... All the linux programs have 64bit versions of them. You should install all the stuff you need using the Synaptic Package Manager (or apt-get install from the command line) and that'll work it all out for you.

The only problems are with java and flash because these are proprietary software - ie. not open source. The solutions to these are many and well documented in the "x86 64bit users" category on ubuntuforums.

Good luck and dont bother installing anything but the 64bit version of Ubuntu on a 64bit machine !

---

### Post by oskar2000 on 2008-02-07
Well, most OSS programs have been ported, and there are howto's for the rest, but I agree, it's too much hassle for too little gain. I never noticed a speed increase with 64 bits, but I did get significantly more crashes. I would wait another 5 years or so :)

---

### Post by oskar2000 on 2008-02-07
> Good luck and dont bother installing anything but the 64bit version of Ubuntu on a 64bit machine !

???

Why! With the exception of only a few things like video and audio encoding, it isn't significantly faster, but it is much more of a hassle.
Is there a 64 bit Virtualbox? Wine? Flash? Java?
I would have to install a 32 bit Jack if I had a 64bit distro to communicate with the 32 bit vst's I use. It's just such a mess. I would definitely NOT recommend it.
That doesn't mean you can't go find out yourself.

---

### Post by Alex_Fingers on 2008-02-07
I really cannot relate to your experience - I installed ubuntu7.10 on my new amd64 machine once - solid as a rock faster than anything I've ever used !! I've never had any negative experience with it at all with anything except java and flash, problems which I solved in about 2 minutes...

Maybe your PC is 32bit ?

---

### Post by oskar2000 on 2008-02-07
You can look at the benchmarks, it is not significantly faster. I don't know what you do, but I need about 10 programs that I would have to run in 32 bit chroots,
It's been about a year since I tried it last, but things generally don't change that quickly.

---

### Post by waspinator on 2008-02-07
how does OS X make 64 and 32 bit applications work so well together? I wish windows and ubuntu could do the same

---

### Post by Zack McCool on 2008-02-07
I have been using the 64-Bit version of Gutsy since a few weeks after it's release.  I highly recommend it.

Almost all of the apps I use have already been ported and are in the repos.  Anything that is Open Source that hasn't been ported should be easy enough to compile.  

Even things that haven't been ported already have solutions in Gutsy.  Flash, for instance, has a package in the Repos.  It installs the wrapper and the 32 Bit plugin.  Works fine.

Is there a 64-Bit Virtualbox?  I don't know.  But there IS a 64-Bit VMWare Server, and it runs much better than the same software on a 32 Bit box.  

And my machine doesn't lock.  Ever.  Everything just runs.  I have had minor glitches, but haven't been able to narrow them down to being 64 Bit issues.  I had minor glitches at times on 32 Bit, as well.

---

### Post by Zack McCool on 2008-02-07
> **oskar2000 said:**
> You can look at the benchmarks, it is not significantly faster. I don't know what you do, but I need about 10 programs that I would have to run in 32 bit chroots,
It's been about a year since I tried it last, but things generally don't change that quickly.

In computers?  A year is a long time in the PC world...

---

### Post by Alex_Fingers on 2008-02-07
I think, although I am an enthusiast, NOT a geek, 64bit linux distributions do make 32bit and 64bit apps work together. If you look in the root directory of a 64bit linux installation, you'll see a directory called lib32 and another called lib64. This means that 32bit apps will work fine except they only use half the memory allocations (I wish I knew properly what that meant !)

---

### Post by CM Xtasy on 2008-02-07
Okay so it's not recommended to use a 64-bit distro even if you can use it.  Thank you all~

---

### Post by mivo on 2008-02-07
> **gavintlgold said:**
> I would definitely not recommend using 64-bit. There are just so many programs that won't work with it.

Could you name some programs that won't work? Besides needing an additional 32-bit browser for MPlayer and Flash (or just using it instead of a 64-bit browser), I have not encountered any issues with running a 64-bit distro. 32-bit programs, even commercial games, run fine if you install the 32-bit libs (there's a package for this). Skype works well, too.

I would say there is **no reason** not to run a 64-bit distro on a 64-bit system. 64-bit is not only about using 4 GB or more of RAM, but there are other advantages as well. Good article here: [http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1]("http://www.bit-tech.net/bits/2007/10/16/64-bit_more_than_just_the_ram/1")

---

### Post by mivo on 2008-02-07
> **CM Xtasy said:**
> Okay so it's not recommended to use a 64-bit distro even if you can use it.  Thank you all~

Yes, it IS recommend. You **should** use a 64-bit distro. For advantages and disadvantages, also read the threads in the 64-bit section. :)

---

### Post by fwojciec on 2008-02-07
64bit is the way of the future but for now I much prefer the stability of the current standard: 32bit.  I have used both 32bit and 64bit systems for a long time.  Use 64bit if you do a lot of multimedia conversion and such, or if you get the kick out of configuring your computer in non-standard ways; otherwise just use 32bit for now...

---

### Post by Alex_Fingers on 2008-02-07
What is a "32 bit chroot" and these 10 32bit apps you use ? 

I'm sure you've got a point - there may be some specialist reason why you can't use a 64bit OS but an experience I had a few years ago of putting SuSE 10.1 32bit on a 64bit machine. It was quite buggy so I downloaded the 64bit version and the difference was massive - much much faster, solid, hardly any bugs. All the software most people use, eg. gimp, or for me, audio stuff - you would'nt know you're using 64bit except that it seems much faster..

---

### Post by fwojciec on 2008-02-07
> **Alex_Fingers said:**
> I think, although I am an enthusiast, NOT a geek, 64bit linux distributions do make 32bit and 64bit apps work together. If you look in the root directory of a 64bit linux installation, you'll see a directory called lib32 and another called lib64. This means that 32bit apps will work fine except they only use half the memory allocations (I wish I knew properly what that meant !)

Which is precisely why I prefer 32bit systems -- no multi-lib mess, less things to break.

---

### Post by bwtranch on 2008-02-07
Well, the argument rages on. I can see both sides of it and you can call me a "fence sitter". I am speaking to you from my AMD 64 running Hardy. The knife in my pocket is made of steel, not bone and my truck now runs on bio-fuels. If we could get the Exxon's of the world to release the research on hydrogen fusion, we would have almost unlimited power. Do you see my point?

---

### Post by Alex_Fingers on 2008-02-07
...but I'm completely unaware of whether any software on my machine is 32bit or 64bit - everything works fine, no hassles or complications. I install pretty much everything through synaptic or apt and everything seems to sort itself out in the background. The only problems I had was with flash and java (for limewire etc.) which I solved pretty quick.. I'd give the new 64bit version a try !

---

### Post by Alex_Fingers on 2008-02-07
I'm really surprised how divisive the issue is based on my thoroughly positive experiences with 64bit linux !

I'm sure all these other people know what they're talking about so perhaps try both with a dual boot and see which is better (then let us know)

It would be a shame to waste all that computing power you have with a 32bit system...

---

### Post by CM Xtasy on 2008-02-07
> **Alex_Fingers said:**
> I'm really surprised how divisive the issue is based on my thoroughly positive experiences with 64bit linux !

I'm sure all these other people know what they're talking about so perhaps try both with a dual boot and see which is better (then let us know)

It would be a shame to waste all that computing power you have with a 32bit system...

Well it's only a Core2Duo @ 1.66ghz.  I have terrible graphics (Intel 950GMA).  Which would be overall better (faster, more supported, more stable), E17 or XFCE?

---

### Post by bwtranch on 2008-02-07
Re #20 Yeah, it's true. Trouble is 32-bit just made too much money and became "too popular". They are going to milk this thing as far as they can. Like Flash, I went to their website the other day and they just did a 64-bit for windows and one will be out for Linux "sometime this year". Arrogance, that's all it is. I don't really care about flash anyway. It's more of an annoyance than a help, with those irritating ads. I usually keep it turned off unless there is something I want to see. And you can run the 32-bit version on your 64 if you want to. Personally, I don't really like adobe anyway and I use gnash. Adobe can have their mud, they're almost as bad as M$.

---

### Post by Alex_Fingers on 2008-02-07
Sorry - I've never heard of E17 or XFCE ! I use Ubuntu 7.10 / Gnome and life is sweet !

---

### Post by fwojciec on 2008-02-07
> **Alex_Fingers said:**
> I'm really surprised how divisive the issue is based on my thoroughly positive experiences with 64bit linux !

I'm sure all these other people know what they're talking about so perhaps try both with a dual boot and see which is better (then let us know)

It would be a shame to waste all that computing power you have with a 32bit system...

I had 32bit and 64bit Arch Linux installed in parallel on my computer for a couple of months -- both systems were sharing the same /home dir so they had identical configurations.  64bit version wasn't any faster than the 32bit version, or I couldn't tell the difference, 64bit version used more memory compared to the 32bit version to run the same applications.  Both versions were stable.  64bit version required slightly more maintenance.  I ended up removing the 64bit version and sticking with 32bit for now -- until I'm able to run a pure 64bit system (I still need 64bit versions of skype, flash, and acrobat reader).

It's not that 64bit systems are bad, it's that they don't really do anything noticeably better than 32bit systems at this stage -- unless, as I said earlier, you work with multimedia, 3d rendering and such.  Meanwhile, at this stage, 32bit systems are still much better supported so it makes sense to prefer them for general use, IMO.

---

### Post by bwtranch on 2008-02-07
Re #24

Your right. There is really no speed difference for everyday stuff, like browsing, email etc. But, in a scientific application like some serious number crunching, it is way faster. Floating point calculations are increased (theoretically, by a factor of 16!).

---

### Post by Alex_Fingers on 2008-02-07
..or if you're into 3d gaming (which I'm not) or all that compiz 3d desktop pointlessness (which I shouldn't be !) or audio processing (which I am) or high-res graphics manipulation (which I am) - whatever's best for you really, but I've never really had any issues what with my system being 64bit - I think things are improving..

---

### Post by bwtranch on 2008-02-07
Continuing on this line...does anybody know about server issues?

---

### Post by fwojciec on 2008-02-07
> **bwtranch said:**
> Re #24

Your right. There is really no speed difference for everyday stuff, like browsing, email etc. But, in a scientific application like some serious number crunching, it is way faster. Floating point calculations are increased (theoretically, by a factor of 16!).

You too are right, of course :D  Though people who need computers for specialist applications usually know if 64bit is going to be beneficial for their needs.

---

### Post by bwtranch on 2008-02-07
Re #26 Yeah Alex I play a 3D game called Scorched 3D. It has some awesome graphics and really bends your brain around sometimes. The 64 deals with it great, my other machine does it's best, it's 32, but that fan really cranks all the time. But the 64 always stays as "cool as a cucumber" HA!:)

---

### Post by bwtranch on 2008-02-07
So fwojciec, I have been hearing a lot about Arch today. Should I try it? I use Gentoo and I was wondering about any differences? Someone was saying that it's not for beginners. Gentoo really isn't either. I think I'm kinda past the noob stage anyway. Oh yeah, just to stay on topic, do they have a 64-bit version.:)

---

### Post by oskar2000 on 2008-02-07
> **CM Xtasy said:**
> Well it's only a Core2Duo @ 1.66ghz.  I have terrible graphics (Intel 950GMA).  Which would be overall better (faster, more supported, more stable), E17 or XFCE?

Can't really be compared. XFCE is a complete DE, and E17 is just a fancy window manager. E17 is much younger, so I'd expect it to be less stable, but I don't know. XFCE should be very stable, and is probably the better option if you don't really know why you want one or the other.

---

### Post by fwojciec on 2008-02-07
> **bwtranch said:**
> So fwojciec, I have been hearing a lot about Arch today. Should I try it? I use Gentoo and I was wondering about any differences? Someone was saying that it's not for beginners. Gentoo really isn't either. I think I'm kinda past the noob stage anyway. Oh yeah, just to stay on topic, do they have a 64-bit version.:)

As far as general philosophy is concerned, Arch is rather like Gentoo: all power to the user but with binaries so compiling is not necessary (though possible, of course); the overarching design principle is KISS.  The 64 bit version of Arch is designed as pure 64bit, which is unusual since these days most distros come with some sort of multilib environment installed by default -- in Arch you have to add 32bit libs yourself based on what you need and it's not officially supported.  Check out the new "Arch" sub-section of "Other OS Talk" for more info...  I'll be happy to confess my undying love for Arch in greater detail if you ask your questions there ;)

OP: Sorry for this brief OT :D

---

### Post by Bungo Pony on 2008-02-08
I'm currenly running 32bit and was considering going 64. I do a lot of audio and some video work, but most of the software I use for those tasks is 32-bit Windows software running in Wine. I'm guessing running 64 bit is of no use to me.

---

### Post by smartboyathome on 2008-02-08
> **CM Xtasy said:**
> Well it's only a Core2Duo @ 1.66ghz.  I have terrible graphics (Intel 950GMA).  Which would be overall better (faster, more supported, more stable), E17 or XFCE?

I would recommend E17 if you don't mind some bugs. It is lighter than XFCE (from what I have seen, which is about a month or two of work), and it is more organized with better themes and such imo.

---

### Post by chrisccoulson on 2008-02-08
I really can't think of any reason not to run the 64-bit version. I've ran nothing but 64-bit since Breezy, and while it is true that it may have been a bit of pain back then - that definately is not the case now.

In Gutsy, installing Flash in 64-bit Firefox from the repositories is a piece of cake, as it installs and configures nspluginwrapper automatically. The only applications I use that have no 64-bit port are a small number of proprietary apps, such as Googleearth, Acrobat Reader and Skype. All of those can be installed from the Medibuntu repository and work fine.

Other 32-bit applications will run, as long as you have the 32-bit dependencies.

The only thing really lacking in 64-bit now is a 64-bit Java browser plugin (although I don't miss not having it) - everything else just works.

> **gavintlgold said:**
> I would definitely not recommend using 64-bit. There are just so many programs that won't work with it. Since all programs must be packaged for 64-bit, many Ubuntu programs don't work at all, or there are problems. It's much harder in general to install stuff in a 64-bit environment.

There is a way to do a 32-bit chroot, but there isn't a noticeable speed increase with 64-bit, and if you can run in a 32-bit environment with your 64-bit CPU it's much easier.

The only thing about 64-bit is you can put much more RAM on your machine. If that's the case then there are quite a few programs, though proprietary apps (like flash support) are basically nonexistant for 64-bit.

Hope that helps. I used to use 64-bit but got sick of it and installed 32-bit.

Replies like this are totally misleading, as most of what you say just isn't true anymore. It might have been like that 18 months ago, but it isn't now.

---

### Post by RAV TUX on 2008-02-09
I recommend [64-bit OzOs.]("http://cafelinux.org/OzOs/")

;)

---

### Post by Rhubarb on 2008-02-09
Virtualbox does run in 64bit fine no problems at all:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Please note it will only run 32bit OSes.

I run Ubuntu 7.10 here on 64bit, haven't had any problems at all.
Virtualbox runs fine
Sauerbraten (FPS game) runs fine, though I did compile it
Flash runs fine
Wine runs fine
and so does google earth.  (Just download the binary, and run it). [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

All the games I play run fine, Including UT2004 and Quake4 and Quake wars.  Anything else you need can be gotten from the repositories (which hold the same apps that 32bit holds).

I can't think of a reason to run a 32bit OS on a 64bit CPU.

---

### Post by Perfect Storm on 2008-02-09
64-bit is fine. I can do all the things I did in 32-bit in 64-bit +plus it's faster when I do heavy gimp stuff, blender, compiling, sound editing etc. 
Compiz fusion are more respondsive.

So there's really only advantages.
If there's an application that only runs 32-bit it is easy to get the right libs for that application with Getlibs (a Cappy invention, you can find his thread in our 64-bit forum). It's only in few rare occasions it's needed (old non-GPL games). The 32-bit and 64-bit libs are seperated so you won't run into trouble.

---

### Post by oskar2000 on 2008-02-09
> **Rhubarb said:**
> I can't think of a reason to run a 32bit OS on a 64bit CPU.
It wouldn't make sense for me, because I do audio editing on a daily basis, for that I need vst plugins which run in a win32 host on wine. To connect wine to jack, I would need a 32 bit jack audio server, which in return means that all the other programs I have connected to it would have to run in 32 bit chroots too. So...
In addition to that I never noticed a notable speed increase - but I did find that the packages were buggier in general (just personal experience, YMMV) - so there is really absolutely no reason for me to install a 64 bit OS.

---

### Post by cdtech on 2008-02-09
> **Alex_Fingers said:**
> I really cannot relate to your experience - I installed ubuntu7.10 on my new amd64 machine once - solid as a rock faster than anything I've ever used !! I've never had any negative experience with it at all with anything except java and flash, problems which I solved in about 2 minutes...

Maybe your PC is 32bit ?

I totaly agree. I'm also running 64 and wouldn't change it for the world. Backward compatibility for running 32-bit and most open-source software can easily be compiled for x86_64.

Gzip compression, ram speed, and kernel compilation performance are far better with 64. I can backup my entire system (compressed) much faster than 32 and less strain on my CPU. I can't find enough programs to run at one time to cause my system to lock up or lag. Multitasking is superior on my laptop now.

My 64 bit laptop is wonderfully fast at everything I’ve tried to do. If you do serious number crunching or serious multimedia work consider the 64 bit, if not then it's your choice.

I've had my share of problems installing Ubuntu 64 on my laptop but nothing a little reading and configuring couldn't repair. Staple programs such as wifi, sound and graphics where all straight forward to configure, using others post here at Ubuntuforums and common sense.

---

### Post by chrisccoulson on 2008-02-09
> **oskar2000 said:**
> It wouldn't make sense for me, because I do audio editing on a daily basis, for that I need vst plugins which run in a win32 host on wine. To connect wine to jack, I would need a 32 bit jack audio server, which in return means that all the other programs I have connected to it would have to run in 32 bit chroots too. So...
In addition to that I never noticed a notable speed increase - but I did find that the packages were buggier in general (just personal experience, YMMV) - so there is really absolutely no reason for me to install a 64 bit OS.

I'm not sure that is entirely true is it? You should just need the 32-bit libjack binaries extracted in to /usr/lib32. That is certainly how everything else works on a mixed 32-bit/64-bit system.

For example, I don't have to run a 32-bit ESD sound server and then run 32-bit versions of every other app in a chroot just because there is one 32-bit application I need to use. I have 32-bit versions of all the libraries in /usr/lib32 (and 64-bit libraries in /usr/lib) which allow me to run both 32-bit and 64-bit applications.

Forgive me if I am wrong, as I have no experience with Jack - but if works like everything else, then what you're saying is nonsense

---

### Post by oskar2000 on 2008-02-10
> **chrisccoulson said:**
> I'm not sure that is entirely true is it? You should just need the 32-bit libjack binaries extracted in to /usr/lib32. That is certainly how everything else works on a mixed 32-bit/64-bit system.
I don't claim I really understand this whole business. I took Dave Hayne's word for it. He is writing linux-audio articles for the linux journal.
Here's a link to the article:
[http://www.linuxjournal.com/node/1000216/](http://www.linuxjournal.com/node/1000216/)

You are right it works, but not very well apparently. I haven't tried it myself. I agree that it would be good to actually make use of 64 bit processors eventually, but it's not worth the trouble for me at this point. I have tried 64 bit distros every half year or so for the past 3 years. Never worked out for various reasons. I might try it again with Hardy. But without wineasio, it really isn't that interesting.

---

