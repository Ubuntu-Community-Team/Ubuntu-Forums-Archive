---
title: "Ubuntu speed vs *others* (Arch)"
date: 2010-09-03
forum: Recurring Discussions
---

### Post by dek8 on 2010-09-03
Would there be any speed improvement with Arch Linux compared to a Ubuntu minimalist xfce installation? (in terms of system responsiveness)

I mean my system is pretty fast and i know Ubuntu is easier, since im new to linux, but i went on with a minimalist xfce4 ubuntu setup and it went pretty smooth, i really like the redmond raleigh UI and require nothing more than xfce has... im happy overall... but i just wonder if there will be any notable performance from going to Arch Linux. Always looking for that little extra speed and responsiveness. And hearing great things about Arch...

I went on with installing Arch in vbox and i cant properly meassure its speed in that i can see that it runs on about a third of the processes in overall and it seems a little bit faster... but is it worth it to change Os if im happy with Ubuntu? 

Any comments?

---

### Post by Elfy on 2010-09-03
Arch people will tell you yes, gentoo people will tell you no - use gentoo, and on and on it will go until it turns into another thread with 2 or 3 people arguing about the same things until it get's closed.

This has been discussed more than once - moved to recurring.

Best thing you can do is try - at the end of the day they are all OS's - use whatever suits you.

---

### Post by kahumba on 2010-09-03
No desktop distro has any speed advantage over another one that would be obvious to **a normal end user**. The only exception would be because of using newer app and library versions.
Otherwise - no distro has made any such breakthrough yet (no matter how much they may claim otherwise).
The difference could be huge in usability though, for instance _**to me**_ almost all Fedora releases are a lot more glitchy than the corresponding Ubuntu releases.

---

### Post by Legendary_Bibo on 2010-09-03
From what I understand Arch is a little bit more difficult to use, or set up or something. If you have a powerful computer then I don't think you'll even notice the difference. I only assume you do because you can run a virtual box of a linux distro which in my experiences are a tad on the really freaking slow side. I don't even know why you're funning XFCE when it's just like normal Ubuntu, but more light.

---

### Post by NightwishFan on 2010-09-03
I would think not. I can build a minimal Ubuntu that boots into a command line using 13mb of RAM. :)

As for 'responsiveness' I would talk to Con Kolivas about that one. Generally configure things to use more RAM and install a preemptive kernel with 1000hz.

---

### Post by Tibuda on 2010-09-03
> **forestpiskie said:**
> Arch people will tell you yes

No, I would say no. Arch is as fast as you make it, just like when you install ubuntu from the [minimal disk](http://www.psychocats.net/ubuntu/minimal).

---

### Post by dek8 on 2010-09-03
> **NightwishFan said:**
> I would think not. I can build a minimal Ubuntu that boots into a command line using 13mb of RAM. :)

As for 'responsiveness' I would talk to Con Kolivas about that one. Generally configure things to use more RAM and install a preemptive kernel with 1000hz.

thats basically what im looking for. back when i used windows basically the first thing i did was to free up overhead by killing processes and disable swap space, cleaning out unneeded stuff and defragmenting the drive with cleaning up the registry.

to me, system responsiveness means everything, i mean, windows 7 is pretty nice, but its starting to look like a joke for us who wants to get minor job done, and that its trying to hold support for every standard, its using a whole bunch of processes running at all time just to understand what you are doing on your computer, i started to get bored of looking at how i kept upgrading my system with higher and higher specs seeing minor performance issues never getting it anywhere near how i had system responsiveness back with XP, even 98... but im still basically doing the same things, only now it looks like a circus.

I then went with linux, i thought ubuntu would be my easiest way to get into it, and saw that i could install a minimal ubuntu with setting it up with only the applications and interface i want and i went on, i dont like kde either, gnome looks better but i saw up on all the dependencies its using and its running more processes than my whole system together.

i understand the whole Arch and Gentoo thing, that people want just the set of applications installed with having the system clean and nice, im about in the same boat that i want all the stuff out of there so that i can have good respnsiveness on the tasks that im doing- Seeing that there is a latency on everything, even on a thing like notepad, i still think i can remember that notepad opened faster in win3.1 on a pentium75 than it does now on a ssd with 3.3Ghz quad core windows 7 setup. yet, theres really nothing extraordinary new out of all of that which is in the way to keep you "happier", so far im happier than ive ever been with just a plain redmond-raleigh xfce4 theme on a minimalist ubuntu setup than ive ever been with a computer, everything seems snappy, its nice and clean, no popups or annoyances, im safe, fast internet and good system specs...

---

### Post by dek8 on 2010-09-03
... so basically all the linux kernels are the same in the core utilization of the processing powers of your system? there is no real advantage of using another "kernel" opposed to another if system performance is what you are looking for?

im not talking about the overall speed of getting things done on your computer when i talk about speed, i simply mean in the final setup in having the system perform the fastest and most responsive in that what you execute.

...in having a clean path right to the systems core processing power... if anyone understands what i mean with that...

---

### Post by dek8 on 2010-09-03
> **Legendary_Bibo said:**
> I don't even know why you're funning XFCE when it's just like normal Ubuntu, but more light.

thats why i use xfce, it is light, it doesnt stand in the way by looking "good" with all its dependencies of gnome. for the other fact that i get bored of any theme that i work in, if its brown maybe one day i want blue, then i get bored of blue, and i keep changing it, i rather just get down to the redmond theme because its basic grey, it tells me its a computer and its clean. im not being frantic. i just like my computer to look like a computer and not like some fancy grandmothers bedroom.(lol)

---

### Post by NightwishFan on 2010-09-03
Download the alternate install cd of Ubuntu 10.04 for your architecture. At the boot splash there is an option to "Install Command Line System" under one of the f4 f5 f6 menus. (I forget which). Check that option and install with the Alternate CD as normal. It resembles the options of the normal installer.

When the machine is installed, ensure you have a wired connection, and run:
```
sudo apt-get update && sudo apt-get upgrade
```

When that finished, simply install what minimal packages you want. A good system based on fluxbox is:
```
sudo apt-get install xorg synaptic fluxbox firefox gdm
```

You can replace fluxbox with xfce4, icewm, lxde.. It is whatever you want. If you do not want a login screen, do not install gdm and just login in when you get to the console and run startx.

Also, if you choose the amd64 arch, you can install a preemptive kernel which is better for lower latency. You might have to hold shift while booting to get a menu to boot to the preempt kernel.
```
sudo apt-get install linux-preempt linux-headers-preempt
```

If you have any questions feel free to ask.

---

### Post by dek8 on 2010-09-03
> **NightwishFan said:**
> I would think not. I can build a minimal Ubuntu that boots into a command line using 13mb of RAM. :)

As for 'responsiveness' I would talk to Con Kolivas about that one. Generally configure things to use more RAM and install a preemptive kernel with 1000hz.

hey night, i found this [https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption](https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption), im kinda scared with it, but i have an easy way to reinstall my system so i will give it a shot. 
But doing things when i cant meassure the output or tell by any way its done or not, do you tweak your system for speed as well? 

Would be great if you got some links or tweaks to other things like this... this realtime preempt looks good tho, i dont think theres any better "things" than that to do to the system? is it like possible to install a system on it or does it all clean its self up after changing the kernel?

---

### Post by dek8 on 2010-09-03
> **NightwishFan said:**
> Download the alternate install cd of Ubuntu 10.04


thanks Night,

 Whats the difference between the minimalist and the alternate installations?

Now, if im going this way i basically dont understand of why just exactly ubuntu... i do have a 64bit processor, how does 64bit linux work?... in windows7 it runs the operating system on 64 and has support for 32bit applications, is it the same thing on linux or does everything run 64bit? even firefox? i dont like the idea of running 2 architectures side by side, i dont know man, i rather go with 32bit windows than 64, how is it with linux?

and about doing it the minimalist way. i dont think i actually understand why the distros are called what they are called apart from the setup they have on the standard cd? since im installing a command line system with the ubuntu cd... couldnt i do this as well with any other distro and later choose what i want to install and it basically becomes the same thing, or is it things that are on that cd that is setup "the ubuntu way"...?

---

### Post by cariboo on 2010-09-03
I would suggest you spend some time learning to use Ubuntu, before trying to build up a minimal installation. If you are running a 64-bit system, you aren't really going to see a lot of difference in speed. It might only be a few 10's of a second in some cases. In most cases speed is subjective, what may seem fast to one person, may seem dead slow to someone else.

The thing to keep in mind is that Windows and Linux work totally different. In Windows there many services installed by default, and most of them are running at logon. With Linux, you only install the services you need, for instance on all my desktop systems, the only extra services I install are ssh and NFS. I don't run a firewall on each computer, my router takes care of that. I have never run anti-malware software, as it isn't needed.

Typically my Home and office systems use about 900Mb ram, with buffered programs. I usually run a couple of terminals and chromium. 

On my server, typical ram usage is 285Mb with LAMP, Samba, NFS, SSH and Cups, the biggest saving in ram usage is no gui. This server can easily stream media to 6 different systems without even breathing hard, and still serve web pages with no hint of a slow down.

---

### Post by NightwishFan on 2010-09-03
You do not need a "real time" kernel. Real time means that you get full kernel level preemption for time critical operations. It will not improve performance (probably makes things slower) it is for something that will fail if it does not happen at an exact time, such as industrial welding and audio synthesis.

As for the minimal install I also agree you should get more familiar or ask some specific questions. It is not hard, however I think the default Ubuntu install will be quite sufficient. That is what I use.

Speed is relative, generally the largest downside is loading programs from the disk, and not the CPU/RAM. You only need enough ram and a faster disk.

I find Ubuntu to be quite snappy. Perhaps try the program preload as well. Lately it was configured to run with idle priority which makes it not make other tasks interrupted. All you have to do is install it and common used programs will be loaded into ram ahead of time.

The preempt kernel included for amd64 Ubuntu is good for latency with audio and it isn't slow like the RT kernel. The generic kernel is good enough.

---

### Post by dek8 on 2010-09-03
i did install the minimalist ubuntu, and i dont question speed for 32bit vs 64bit other than it supports more memory. And im wondering about if all stays 64bit compared to some applications not being 64bit, like for instance firefox, i dont believe mozilla have published a 64bit version on that, and i rather have the operating system run 32bit than having some 32bit applications running on a 64bit OS.

and what im asking is what is the difference between installing the minimalist and the alternate cd? when i installed the minimalist, it went through installing alot of things from the net, does the alternate work any different? i ended up with a command line and did the aptitude install xorg xfce synaptic... and im still logging in on command line, just cause i like to keep a login manager out of the system for keeping it clean.




im just reading up on ramdisk and ramback, this is basically what im looking for, i got an ssd though, and i got 4gb ram.

and i just tried the rt kernel, i believe it is slower... i can notice it, at first it seemed like the mouse was more responsive but after a while im getting lag on small things like writing this post...

---

### Post by Gone fishing on 2010-09-03
Mmm just installed FreeBSD with XFCE and I have to say it feels fast. However, as a Desktop OS, Well you may gain a few seconds here and there but expect to spend more time Googling and and using Vi and compiling ports isn't quick.

Speed costs how fast do you want to go!

---

### Post by dE_logics on 2010-09-04
Ubuntu is known to be the slowest probably cause - 

1) The package maintainers most probably use -Os
2) There's some sorta bug in every package!... this one might be too!
3) Too many packages preinstalled (partially correct, 1200 is not that many and it's Ubuntu's philosophy to split a single package into 3 or 4. e.g gimp, gimp-data, gimp-doc, openoffice-base, openoffice-writer etc... etc... etc...)
4) There's no one to tell them what's wrong cause the majority  of the community thinks - 
 4.1) It doesn't matter how many packages you install.
 4.2) It doesn't matter with what options the sources have been compiled.
 4.3) It doesn't matter what gcc parameters the sources have been compiled with.

All that matters is that it's Ubuntu and if it's Ubuntu it's best in everything... speed, security, reliability etc..

---

### Post by dE_logics on 2010-09-04
Serious advice -- Install Sabayon minimal with a self configured and tweaked Zen kernel.

Need faster? Use Gentoo but it takes a lot of time and effort.

---

### Post by DemonBob on 2010-09-04
> **Gone fishing said:**
> Mmm just installed FreeBSD with XFCE and I have to say it feels fast. However, as a Desktop OS, Well you may gain a few seconds here and there but expect to spend more time Googling and and using Vi and compiling ports isn't quick.

Speed costs how fast do you want to go!

pkg_add -r :)

---

### Post by Gone fishing on 2010-09-04
> pkg_add -r

Absolutely:D 

But if you want **speed** you'd use ports and compile. Actually I'm very impressed with FreeBSD so far the configuration makes sense and setting up a software Raid a breeze. Just playing so far used packages for X, compiling ports for X and xfce didn't look like fun but used ports for other stuff not too bad.

However as my desktop OS I'd rather use Ubuntu anyone use PCBSD? Hows that for everyday useage?

---

### Post by cariboo on 2010-09-04
I have a system that boots 4 different distributions, Maverick, PCLinuxOS, Fedora and openSUSe. These are all default installation with all but openSUSE running gnome. Of the three I would say that PCLinuxOS feels the fastest of the three,then Maverick and finally Fedora with openSUSE/kde bringing up the rear.

This is a system I put together from discarded parts, Athlon 3200+, 1Gb Ram, Nvidia 8400GS, SATA DVDR/W and 160GB HDD and a PATA 30GB HDD for XP.

The one thing I have found is that the network speed in Fedora is just abysmal, that's one of my projects for next week to see why it doesn't perform the same as the rest of the OSs.

---

### Post by kevCast on 2010-09-04
> **dE_logics said:**
> Ubuntu is known to be the slowest probably cause - 

1) The package maintainers most probably use -Os
2) There's some sorta bug in every package!... this one might be too!
3) Too many packages preinstalled (partially correct, 1200 is not that many and it's Ubuntu's philosophy to split a single package into 3 or 4. e.g gimp, gimp-data, gimp-doc, openoffice-base, openoffice-writer etc... etc... etc...)
4) There's no one to tell them what's wrong cause the majority  of the community thinks - 
    4.1) It doesn't matter how many packages you install.
    4.2) It doesn't matter with what options the sources have been compiled.
    4.3) It doesn't matter what gcc parameters the sources have been compiled with.

All that matters is that it's Ubuntu and if it's Ubuntu it's best in everything... speed, security, reliability etc..

> **dE_logics said:**
> Serious advice -- Install Sabayon minimal with a self configured and tweaked Zen kernel.

Need faster? Use Gentoo but it takes a lot of time and effort.

What garbage.
```

1) Optimizations only go so far. The algorithm is what's important. Besides, generic optimizations means more stable code. But maybe you like reading core dumps.
2) There's a bug in all 25,000+ packages?
3) If you recall, Ubuntu is based on Debian.
4) There is definitely a huge amount of zealot behaviour for Ubuntu, however:
    4.1) I'm not sure what this means.
    4.2) Yes, you're right. It doesn't matter.
    4.3) You just restated 4.2 with different wording.

```

As far as your advice, the marginal benefit of -ZOMG-so-fast-code is eclipsed by the marginal cost of lost time. Combined with the lack of ease in setup and in maintenance makes Gentoo something only fit for a hobbyist's desktop.

And before you label my opinion has the rantings of a delusional Ubuntu fanboy, I want to let you know that I'm a Fedora user, and that Linux is Linux. However, the quality of implementation of said Linux is a different story. And Gentoo's story is one of severe headache, bordering on aneurysm.

---

### Post by NightwishFan on 2010-09-04
Relax. Though I mainly agree, please note that ALL software has bugs, including Windows, Debian, Fedora, whatever. The upside that I see from max optimizations is slim to none I concur, and I see no personal use for it. The 'speed' of Ubuntu is subject to differences of perspective and opinion. Throughput and latency, program launch time, all of them are governed by different bits of software and configuration.

From my experience, Canonical generally tends to favor something working over something being fast, which is correct as Ubuntu is a product. As for 'speed', I doubt you will notice a second difference from another distribution for say converting a video with ffmpeg. Perhaps a distro or configuration with reduced libraries may make programs launch faster, by a second or so.

Ubuntu pretty much runs like a greased gear for me.

---

### Post by dek8 on 2010-09-05
> **dE_logics said:**
> Ubuntu is known to be the slowest probably cause - 

1) The package maintainers most probably use -Os
2) There's some sorta bug in every package!... this one might be too!
3) Too many packages preinstalled (partially correct, 1200 is not that many and it's Ubuntu's philosophy to split a single package into 3 or 4. e.g gimp, gimp-data, gimp-doc, openoffice-base, openoffice-writer etc... etc... etc...)
4) There's no one to tell them what's wrong cause the majority  of the community thinks - 
 4.1) It doesn't matter how many packages you install.
 4.2) It doesn't matter with what options the sources have been compiled.
 4.3) It doesn't matter what gcc parameters the sources have been compiled with.

All that matters is that it's Ubuntu and if it's Ubuntu it's best in everything... speed, security, reliability etc..

I installed arch on virtualbox and it only downloaded like 2% of what the ubuntu minimalist installer did, i dont know anything about it but it seems to me that there is ALOT of things in ubuntu, i thought minimalist just mean having the core features of the operating system and then go on from there... this is why i started this thread in the first place, cant seem to find any easy to understand explanation for it... i look at it this way, for doing a complete ubuntu install, and then doing it minimalist xfce setup, the minimalist xfce is like 3 times faster ine execution than the standard ubuntu install, its like everything runs with more than enough processing powers in reserve making everything snappy and fresh all the time. thinking maybe ubuntu is bloated even with the minimalist. i dont know.

---

### Post by linux18 on 2010-09-05
@nightwishfan

can you share the .vdi of your minimal that boots in 13MB of ram it sounds very interesting.

---

### Post by dek8 on 2010-09-05
> **dE_logics said:**
> Serious advice -- Install Sabayon minimal with a self configured and tweaked Zen kernel.



what is the sabayon with a self configured and tweaked Zen kernel? lol
Do i get that from their homepage?
Is it this Sabayon_Linux_CoreCDX_5.3_x86.iso ? Zen?

---

### Post by MarcusW on 2010-09-05
> **cariboo907 said:**
> I have a system that boots 4 different distributions, Maverick, PCLinuxOS, Fedora and openSUSe. These are all default installation with all but openSUSE running gnome. Of the three I would say that PCLinuxOS feels the fastest of the three,then Maverick and finally Fedora with openSUSE/kde bringing up the rear.

This is a system I put together from discarded parts, Athlon 3200+, 1Gb Ram, Nvidia 8400GS, SATA DVDR/W and 160GB HDD and a PATA 30GB HDD for XP.

The one thing I have found is that the network speed in Fedora is just abysmal, that's one of my projects for next week to see why it doesn't perform the same as the rest of the OSs.

In my experience, where on the HDD the Linux-based OS is installed affects the performance greatly. So note that the OS that's installed on the beginning of the HDD has an advantage over the others.

---

### Post by perspectoff on 2010-09-05
> **dek8 said:**
> ... so basically all the linux kernels are the same in the core utilization of the processing powers of your system? there is no real advantage of using another "kernel" opposed to another if system performance is what you are looking for?

im not talking about the overall speed of getting things done on your computer when i talk about speed, i simply mean in the final setup in having the system perform the fastest and most responsive in that what you execute.

...in having a clean path right to the systems core processing power... if anyone understands what i mean with that...

Ubuntu, Fedora, Arch, and Gentoo are not kernels. 

They use the same Linux kernel (for the most part). You are confusing the Linux kernel (which is still supervised by Linux Torvalds himself) with the OS.

Also, an OS, for almost every user, is only the beginning. The applications are what we end up using, and it is the ease of obtaining, installing, and using applications that makes an OS useful. 

It is this last quality that makes Ubuntu appealing -- they have standardized the pipeline.

Yes, one OS might have a few milliseconds advantage over another -- so what? 

What eats up a user's time is customizing the system, and obtaining, installing, and using applications. 

If you're not a real user, but just a tinkerer who loves tinkering, then you will be happiest installing them all -- comparing, measuring, and tweaking performance. In that case, no one's advice makes any difference.

But if you want to get things done, go with he OS with the best online support, the most number of users who can give that support, and the best integrated package delivery system.

Hands down, that currently is Ubuntu (or my personal favorite, Kubuntu).

---

### Post by perspectoff on 2010-09-05
> **dek8 said:**
> I installed arch on virtualbox and it only downloaded like 2% of what the ubuntu minimalist installer did, i dont know anything about it but it seems to me that there is ALOT of things in ubuntu, i thought minimalist just mean having the core features of the operating system and then go on from there... this is why i started this thread in the first place, cant seem to find any easy to understand explanation for it... i look at it this way, for doing a complete ubuntu install, and then doing it minimalist xfce setup, the minimalist xfce is like 3 times faster ine execution than the standard ubuntu install, its like everything runs with more than enough processing powers in reserve making everything snappy and fresh all the time. thinking maybe ubuntu is bloated even with the minimalist. i dont know.

I laugh myself silly anytime I see someone arguing about performance in virtual machines.

If you were really concerned about performance, you wouldn't be running a virtual machine.

---

### Post by NightwishFan on 2010-09-05
I used to have a screenshot of the VM, I will do it again sometime.

---

### Post by cj.surrusco on 2010-09-05
> **cariboo907 said:**
> 
On my server, typical ram usage is 285Mb with LAMP, Samba, NFS, SSH and Cups, the biggest saving in ram usage is no gui. This server can easily stream media to 6 different systems without even breathing hard, and still serve web pages with no hint of a slow down.

I also have a home sever set up with similar programs set up (SSH, FTP, LAMP). I always read that not having a GUI would speed up my server, but I decided to try it anyway and found that it barely makes a difference (for my system at least, which is just an old Dell Desktop). 

I mostly use SSH command line to control the server but I have the VNC GUI (gnome) for those tasks that are much easier with a GUI. I always have a tightvnc server running and it never uses more than 1% CPU when there aren't any clients connected, and even when clients are connected, it uses about 1% at idle and about 6-8% when browsing around with the GUI. 

I found that to be a very insignificant difference, so that's why I always have the VNC running. The CPU is a Pentium 4 2.8 ghz, by the way.

---

### Post by dek8 on 2010-09-05
> **perspectoff said:**
> Ubuntu, Fedora, Arch, and Gentoo are not kernels. 

They use the same Linux kernel (for the most part). You are confusing the Linux kernel (which is still supervised by Linux Torvalds himself) with the OS.

Also, an OS, for almost every user, is only the beginning. The applications are what we end up using, and it is the ease of obtaining, installing, and using applications that makes an OS useful. 

It is this last quality that makes Ubuntu appealing -- they have standardized the pipeline.

Yes, one OS might have a few milliseconds advantage over another -- so what? 

What eats up a user's time is customizing the system, and obtaining, installing, and using applications. 

If you're not a real user, but just a tinkerer who loves tinkering, then you will be happiest installing them all -- comparing, measuring, and tweaking performance. In that case, no one's advice makes any difference.

But if you want to get things done, go with he OS with the best online support, the most number of users who can give that support, and the best integrated package delivery system.

Hands down, that currently is Ubuntu (or my personal favorite, Kubuntu).

When did i say that the distros are different kernels? I asked about the performance of the different kernels. taking in to account that possibly? an older or newer kernel version is better suited for speed... Linux Torvalds lol

---

### Post by dek8 on 2010-09-05
> **perspectoff said:**
> I laugh myself silly anytime I see someone arguing about performance in virtual machines.

If you were really concerned about performance, you wouldn't be running a virtual machine.

you are weird man, try reading it before you just come up with a comment, i never compared speed in virtualbox. I said that arch downloaded less than ubuntu for an install.

---

### Post by cariboo on 2010-09-05
> **MarcusW said:**
> In my experience, where on the HDD the Linux-based OS is installed affects the performance greatly. So note that the OS that's installed on the beginning of the HDD has an advantage over the others.

In my case oppenSUSE is installed on the first partition, then Maverick, then PCLinuxOS and finally Fedora. As far as I'm concerned, there shouldn't be a noticeable difference from partition to partion, there will be a difference, but enough that I would actually get a feeling the one OS is slower than the other.

---

