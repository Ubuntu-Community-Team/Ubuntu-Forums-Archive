---
title: "is it possible to install ubuntu like gentoo?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-30
ubuntu simply flies on my computer that has 2 gigs of RAM and a 2GHz Core2Duo processor.but,i want a still faster ubuntu,something like gentoo.but,i know that installing gentoo is a pain at least for users like me.i wanted to know if there are ways to install ubuntu in a similar way,i mean kernel recompiling and all that stuff needed to get gentoo installed and running?if yes,please guide me into it,as i am ready to bear all that for a better and faster ubuntu,since i know i shall also learn a lot in the process.

---

### Post by OrangeCrate on 2008-11-30
How about an Ubuntu minimal install, and then roll your own after that? Should be pretty quick I would think.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by oldos2er on 2008-11-30
Compiling is the same whether it's Ubuntu or Gentoo; all Ubuntu's source code is freely downloadable from its repositories. But I think it would be much easier to install Ubuntu from a LiveCD, and once you get it up and running, then try your hand at configuring and compiling a custom kernel.

---

### Post by stonecoldjha on 2008-11-30
how do i compile a custom kernel?

---

### Post by Gannon8 on 2008-11-30
There are many tutorials on compiling your own kernel on line, but the whole OS, I am not sure about where to get the source code ubuntu specifically...

If you are still asking stuff in the Absolute Beginner Talk forum then I would not attempt to compile something as major as a kernel, let alone a whole OS (I only hang around here to help others :) ). I doubt you would get a noticeable speed increase, so I recommend just leaving the kernel as it is.

---

### Post by ugm6hr on 2008-11-30
> **stonecoldjha said:**
> but,i know that installing gentoo is a pain at least for users like me.i wanted to know if there are ways to install ubuntu in a similar way

If it is a pain, why do you want to do it that way?

And if you're going to do it that way, why not just install Gentoo.

---

### Post by sdennie on 2008-11-30
You can do this with apt-build.  However, your hassle to benefit ratio will be quite poor.  It's going to be painful to rebuild your system from source and the performance benefit is not likely to be noticeable.

---

### Post by binbash on 2008-11-30
> **ugm6hr said:**
> If it is a pain, why do you want to do it that way?

And if you're going to do it that way, why not just install Gentoo.

Because gentoo is faster than (WAY to FAST :D ) ubuntu (or anyother distro except archlinux) , and it is really hard to setup.It takes a couple of days if you dont install gentoo before(of course reaching that speed takes days : ) ).

---

### Post by sdennie on 2008-11-30
> **binbash said:**
> Because gentoo is faster than (WAY to FAST :D ) ubuntu (or anyother distro except archlinux) , and it is really hard to setup.It takes a couple of days if you dont install gentoo before(of course reaching that speed takes days : ) ).

If gentoo is faster than Ubuntu, it likely doesn't have much to do with the compiler flags things are compiled with.  It probably has to do with what packages are installed, the versions of those packages and what *parts* of them are enabled.  Recompiling something from source does not make it automatically faster.  Recompiling from source and disabling much of the software *might* make it faster but, in a similar way to "not installing the software" would.

---

### Post by binbash on 2008-11-30
> **vor said:**
> If gentoo is faster than Ubuntu, it likely doesn't have much to do with the compiler flags things are compiled with.  It probably has to do with what packages are installed, the versions of those packages and what *parts* of them are enabled.  Recompiling something from source does not make it automatically faster.  Recompiling from source and disabling much of the software *might* make it faster but, in a similar way to "not installing the software" would.

Yes that is why it takes days, you are testing your make.conf(flags etc), what you need etc.You are totally right at that point.

@stonecoldjha

Kernel compiling will make your pc fast for sure(if you compile right), but if you don't know your software well or never see a kernel config menu, i suggest you install a linux (ubuntu of course) on a virtual machine and test some stuff there.

---

### Post by stonecoldjha on 2008-12-01
i am about to buy a new PC that would have a quad core processor,4 gigs of RAM ,1 TB of hard disk,and an nvidia 8800 ultra card.ubuntu would be lightning fast on it.won't it be?

---

### Post by stonecoldjha on 2008-12-01
also,why does ubuntu not recognise 4 gb of RAM on my friend's pc?

---

### Post by oldos2er on 2008-12-01
> **stonecoldjha said:**
> also,why does ubuntu not recognise 4 gb of RAM on my friend's pc?

 Because he's using the 32-bit version.

---

### Post by stonecoldjha on 2008-12-01
but i suppose that he has got a 32 bit architecture.
also,tell me if my ubuntu would be dramtically faster on my new box with 4 gigs of RAM,quad core procesor and nvidia 8800 ultra card?

---

### Post by oldos2er on 2008-12-01
> **stonecoldjha said:**
> but i suppose that he has got a 32 bit architecture.
also,tell me if my ubuntu would be dramtically faster on my new box with 4 gigs of RAM,quad core procesor and nvidia 8800 ultra card?

 Possibly. But if you're obsessed with speed, why not use a lighter distro like Arch, for example?

---

### Post by stonecoldjha on 2008-12-01
because i love ubuntu,and of course this community which has always bailed me out of all troubles i had with ubuntu.

---

### Post by scorp123 on 2008-12-01
> **stonecoldjha said:**
> how do i compile a custom kernel? if you have to ask *that* then you are probably way over your head and should not bother with this.

---

### Post by scorp123 on 2008-12-01
> **stonecoldjha said:**
> i know that installing gentoo is a pain at least for users like me Compiling everything yourself won't make it any easier. That's precisely why Ubuntu has a package manager, so users can download pre-compiled packages and don't have to bother with compiling everything themselves.

If you compile things yourself and especially if you plan on doing this to your entire Linux installation then you should know what you are doing. You'd be better served if you sticked to Gentoo if you insist on compiling. Or why not even "Linux from Scratch"? :D

---

### Post by kk0sse54 on 2008-12-01
I would recommend doing a minimal install and then build your system from there. If you want something source based and like hours of compiling use Gentoo (really it's a great distro :)). For compiling your own kernel you might want to check out these links 

**Master Kernel Thread**
[http://ubuntuforums.org/showthread.php?t=311158&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=compiling+kernel)

**HowTo: Installing and using KernelCheck**
[http://ubuntuforums.org/showthread.php?t=618563&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=618563&highlight=compiling+kernel)

**HOWTO: Kernel Compilation for Newbies**
[http://ubuntuforums.org/showthread.php?t=56835&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=56835&highlight=compiling+kernel)

---

### Post by stonecoldjha on 2008-12-01
now i am getting the notion that the trouble is not worth taking.i am about to buy a more powerful pc,that i expect would run ubuntu fast enough,i mean would it not with 4 GB RAM ,an nvidia 8800 ultra,and quad core processor.
i can do all that stuff provided i notice significant performance gains.

---

### Post by OrangeCrate on 2008-12-01
And, after 19 posts in this thread, the last suggestion turned out to be the same as the first one. Funny.

@stonecoldjha

Your solution is probably the best one for you. Be sure to load the 64 bit version to take advantage of the 4 GB of RAM, if that's what you decide to do.

Good luck.

---

### Post by scorp123 on 2008-12-02
> **stonecoldjha said:**
>  i can do all that stuff provided i notice significant performance gains. Would you even know how to measure those performance gains ... or lack of performance? Do you even know how to benchmark a UNIX-like system? Probably not. So why bother with this then? Don't get me wrong. But your entire talk about performance gains is like a blind man talking about color. You simply lack the experience to be in a position where you could possibly make valid statements about "lack of performance" in Ubuntu. Again ... don't get me wrong. There are ways by which one could *easily* get slightly more speed out of Ubuntu, e.g. by removing unneeded components and turning off unneeded boot services that might make the boot process slower than it should. Selecting the right file system during the installation helps too, e.g. I use XFS so I don't have to waste time with those slow filesystem checks Ext2 and Ext3 make from time to time.

As for the performance on a Quad-Core system:

On any reasonably modern system any difference in performance that you'd gain by compiling things yourself versus using the binaries you'd get from the Ubuntu package manager would be totally negligible and hard to measure, e.g. you'd have to give those numbers you'd measure a certain tolerance for error (e.g. 10% error rate), and when you take that into account it becomes totally irrelevant if e.g. Firefox took 2 seconds to start or 2.1 seconds (the 0.1 second difference would be within the error tolerance, so this "performance gain" result counts for nothing). And to be fair you'd have to compile your Gentoo binaries with the same options and libs as in Ubuntu, e.g. GTK+ support, Pulse audio support libs, OSS audio support, ESD audio support, and so on.

Gentoo gains a lot of performance because it is possible to compile applications without certain components, making them appear faster. It's like driving around with an empty truck. It's obvious that an empty truck or only slightly loaded truck (= Gentoo binary) is way faster than a truck loaded with goods (= Ubuntu and all the many features its binaries come compiled with). Load up both trucks (= Gentoo + Ubuntu) with the same stuff (= same libraries and same options) and you will see that the difference is way way harder to tell.

Also: The downside to Gentoo's way of doing things is that as soon as you insert a component that you left away earlier you might end up having to recompile tons of stuff again or things won't play nicely together.

It's a hassle not worth taking in my humble opinion. I consider myself being a "Pro" user ... but honestly: I know better ways to spend my (valuable!) time than to compile binaries all day and night. Same goes for my machines both at work and at home: If they compile day and night they produce nothing but hot air ... I sure know better ways to put them to use than that!

Nothing against Gentoo ... I admire the possibility to tweak every aspect it gives to its (geek- ?) users... who obviously should know what they do. But Ubuntu's motto is "Linux for human beings" and I think most people are better served with that.

BTW: on my new HP m9480 Pavilion (Intel Q9400 2.66 GHz quad-core CPU, 8 GB RAM, 2 x 640 GB disks, Nvidia 9800GT) Ubuntu is fast as hell compared to Vista Ultimate ... and I haven't yet tweaked anything. I so far didn't feel the need. On the contrary. I have turned on every possible bit of eye candy ....  I have yet to see a performance problem here.

Vista on the other hand is a sad story. With Vista my new quad-core PC feels like an early slow Pentium-4 system, it's downright ridiculous. At least now I know which partition I will have to wipe when I want to try out another Linux distribution .... :D

---

### Post by kelvin spratt on 2008-12-02
All this talk of speed If you want a fast distro that half way between Unbuntu and Gentoo use Arch, Its fast lightning fast and you can compile or use the package manager, it installs as a base only system you decide what you want or do not want simple.

---

