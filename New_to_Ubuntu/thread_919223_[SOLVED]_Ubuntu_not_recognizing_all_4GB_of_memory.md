---
title: "[SOLVED] Ubuntu not recognizing all 4GB of memory"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-13
Hi, all:

I"m running 32-bit Kubuntu 8.04, KDE4.1.1, and have (1) Intel Core 2 Duo 2.83GHz, (2) 4GB RAM.

Ubuntu is recognizing only 3.2GB of ram; how do I get it to use all 4GB?  I've seen this issue addressed in other threads on this forum, but they're all in reference to 64-bit systems.

---

### Post by akiratheoni on 2008-09-13
That's because 32-bit OSes can only support 3GB of RAM or less. If you want it to see all 4GB of RAM, you need to run a 64-bit operating system.

---

### Post by tarahmarie on 2008-09-13
Oh, BALLZ.  Do you think that the upgrade to Intrepid will change this?

---

### Post by gali98 on 2008-09-13
No it will not. This issue is do to hardware and the limitations of 32bit.
But you can just install 64 bit. There is very little that does not run on 64bit.
I have not found anything yet.
Kory

---

### Post by akiratheoni on 2008-09-13
I believe you would have to do a complete re-install of Ubuntu. The 3GB limit is a limit of the 32-bit architecture; no matter if you were running 32-bit Windows, Red Hat, OpenSUSE, Mac OSX, what name you, it could only recognize 3GB of RAM.

If you haven't created a separate /home partition, you might want to consider doing so right now:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Follow that tutorial. That way you can install 64-bit Hardy Heron and not lose your preferences (you will still need to re-install the programs, but your preferences for those programs will not be lost).

---

### Post by jemate18 on 2008-09-13
> **tarahmarie said:**
> Oh, BALLZ.  Do you think that the upgrade to Intrepid will change this?

I have almost the same specs as yours with 4GB RAM running 32-bit Ubuntu Hardy..

Only 3.2GB of RAM is detected. THis is because the limitation of the 32-BIT architecture.. I tried the 64-BIT version and it did got all 4GB, problem is 64-bit version took a lot of problems for me so i switch back to 32.

In Intrepid? If you choose the 64-bit, then it will recognize all 4GB, but 32-will only have 3.2GB at the most

---

### Post by gali98 on 2008-09-13
a lot of problems on 64bit is running 32bit programs.
Using the getlibs script, I have solved every problem I have run into...

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Kory

---

### Post by tarahmarie on 2008-09-13
For now, it sounds to me like it's more trouble than it's worth going to a 64-bit system.  I know I"ll need to eventually,, but I think I'd rather wait until a few more of the bugs are worked out.  I've already got enough stuff that doesn't work exactly as I'd like it to.  Plus, that's what swap memorys for, right ;-)

---

### Post by starcannon on 2008-09-13
I've installed 64bit on a separate partition last week to see how things have progressed. Its not too bad these days, granted not quite as out of the box as 32bit, but nearly. Really the only issues I'm facing are some softwares that I want to run aren't currently available precompiled for 64bit; however, if I weren't lazy, it is something I could manage by compiling them myself.

GL and nothing wrong with 32bit, indeed I keep it on a separate partition as my safety net.

---

### Post by jimmy the saint on 2008-09-13
It would be interesting to know the Motherboard chipset.  An often overlooked fact in RAM/32bit/64bit discussions is the fact that some motherboards are not capable of giving the OS access to all 4Gigs.  I, for example, have a Gigabyte MoBo which advertises 4Gig capability, but due to the 945 chipset, is incapable of actually allowing the OS to use it all.  Most newer boards do not suffer this issue though.

---

### Post by bodhi.zazen on 2008-09-13
> **akiratheoni said:**
> That's because 32-bit OSes can only support 3GB of RAM or less. If you want it to see all 4GB of RAM, you need to run a 64-bit operating system.

> **gali98 said:**
> No it will not. This issue is do to hardware and the limitations of 32bit.
But you can just install 64 bit. There is very little that does not run on 64bit.
I have not found anything yet.
Kory

> **jemate18 said:**
> I have almost the same specs as yours with 4GB RAM running 32-bit Ubuntu Hardy..

Only 3.2GB of RAM is detected. THis is because the limitation of the 32-BIT architecture.. I tried the 64-BIT version and it did got all 4GB, problem is 64-bit version took a lot of problems for me so i switch back to 32.

In Intrepid? If you choose the 64-bit, then it will recognize all 4GB, but 32-will only have 3.2GB at the most

None of that information is true. 32 bit arch will support up to **64 Gb** of ram.

It is called PAE

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

If you do know know, please do not give out mis information.

The server and openvz kernels come with PAE enabled, otherwise you need to re-complie your desktop (generic) kernel. Search these forums, there are several how-to's on how to enable PAE.

---

### Post by starcannon on 2008-09-13
> **bodhi.zazen said:**
> None of that information is true. 32 bit arch will support up to **64 Gb** of ram.

It is called PAE

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

If you do know know, please do not give out mis information.

The server and openvz kernels come with PAE enabled, otherwise you need to re-complie your desktop (generic) kernel. Search these forums, there are several how-to's on how to enable PAE.
True enough, though not common knowledge, so the "if you do (not) know, please do not give out mis information" bit is kinda a gray area. I am only just now aware that we can go over 3 gb because of your post. Not because I didn't know, but because it was what I had previously been lead to believe(that sounds contradictory but I hope its understandable). In other words, I don't think any mis-information was given out of known ignorance nor on purpose, currently its just that the PAE enabled kernels are not common knowledge, and I have never seen them given as an installer choice on the standard 32bit edition of Ubuntu.

---

### Post by cmat on 2008-09-13
If Ubuntu supported the "bigmem" kernel you could utilize up to 64 GBs of RAM on a 32-bit system. I think Debian has this.

---

