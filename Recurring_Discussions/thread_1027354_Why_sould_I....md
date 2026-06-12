---
title: "Why sould I..."
date: 2009-01-01
forum: Recurring Discussions
---

### Post by mark on 2009-01-01
I've determined through live boot CDs that I can run 64-bit Linux on my laptop (Dell 1525n, Intel T5550 Core 2 Duo CPU).  My question is (and I searched for similars) why?  What's the advantage of a 64-bit OS when everything I need seems to run fine in 32?  This is not flame-bait, I sincerely would like the latest thinking on this...

Regards,

Mark

---

### Post by mikewhatever on 2009-01-01
Here is a good read. [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

To summarize, you shouldn't, nor should you not.

---

### Post by 73ckn797 on 2009-01-01
> **mark said:**
> I've determined through live boot CDs that I can run 64-bit Linux on my laptop (Dell 1525n, Intel T5550 Core 2 Duo CPU).  My question is (and I searched for similars) why?  What's the advantage of a 64-bit OS when everything I need seems to run fine in 32?  This is not flame-bait, I sincerely would like the latest thinking on this...

Regards,

Mark

The only real difference that I have found is that the 64bit recognizes 3.9Gib of 4Gib memory. The 32bit only recognized 3.3Gib. I do not have high demanding apps. I probably could have left things alone but since I have a 64bit motherboard I wanted to use it. Probably not much of a reason but it is what it is.

---

### Post by scorp123 on 2009-01-01
> **mark said:**
>  What's the advantage of a 64-bit OS when everything I need seems to run fine in 32?   Same problem here. There are a few commercial Linux applications that I have to use, and they only work on 32-bit Linux, I can't make them to work on 64-bit Linux. So what I do is that I use 32-bit Ubuntu but with the PAE-enabled "linux-server" kernel (which is default on "Ubuntu Server"), so with the PAE I at least get to use all of my 8 GB RAM (individual processes are still limited to 4 GB max. per process ... but I can live with that). With PAE enabled a 32-bit OS could address up to 64 GB RAM. There apparently is a minor performance hit though if you use PAE, but so far I didn't notice anything special. So if compatibility matters more than performance then I'd say go for 32-bit + PAE. If you are sure that everything that matters to you is available and perfectly working on 64-bit too, go for 64-bit then.

---

### Post by Half-Left on 2009-01-01
> **scorp123 said:**
> Same problem here. There are a few commercial Linux applications that I have to use, and they only work on 32-bit Linux, I can't make them to work on 64-bit Linux. So what I do is that I use 32-bit Ubuntu but with the PAE-enabled "linux-server" kernel (which is default on "Ubuntu Server"), so with the PAE I at least get to use all of my 8 GB RAM (individual processes are still limited to 4 GB max. per process ... but I can live with that). With PAE enabled a 32-bit OS could address up to 64 GB RAM. There apparently is a minor performance hit though if you use PAE, but so far I didn't notice anything special. So if compatibility matters more than performance then I'd say go for 32-bit + PAE. If you are sure that everything that matters to you is available and perfectly working on 64-bit too, go for 64-bit then.

It's not a minor performance hit, it's a big overhead to run, 64bit is superior at addressing memory, thankfully kernel devs put in a memory split to less than 4Gb users so they dont need to enable PAE.

---

### Post by scorp123 on 2009-01-02
> **Half-Left said:**
> It's not a minor performance hit, it's a big overhead to run  Define "big overhead" please? You should get a max. performance hit of about 10% which isn't much (maybe up to 15% in rare extreme cases), and you are only going to see and experience that if you do memory-intensive stuff. E.g. having a full-blown Oracle database with large memory tables run on a PAE-enabled system .... yes, that's not such a cool idea. The performance will suck. But in normal everyday desktop usage? Nope, you shouldn't see any serious performance problems. At least I am not seeing any :)  But then again I have not much of a choice as I absolutely need to run certain commercial apps and they only really work on 32-bit Linux. Trust me, I'd prefer to have native 64-bit versions of this stuff ... but right now I can't have that, so I have to use "Plan B" here.

---

### Post by Half-Left on 2009-01-03
Go look up overhead, overhead can wipe out all the low latency on your desktop so all of them milliseconds your desktop feeling snappy are gone, thats what overhead does.

Dont confuse it with speed and ask for benchmarks. Yes a low latency does is very imported to everyday users, i.e clicking anything, The overhead of PAE can wipe this out.

---

### Post by scorp123 on 2009-01-04
> **Half-Left said:**
> so all of them milliseconds your desktop feeling snappy are gone I am unable to reproduce that here. I can even run VirtualBox and 3D shooters such as Nexuiz at the same time (therefore pretty much filling up my RAM) and yet my desktop feels *snappy enough*. The only real difference I can see is that it feels *even snappier* when I boot into my 64-bit partition.

But that "big overhead" talk and "snappy feeling is gone" is FUD. PAE isn't perfect yes, it's a workaround yes, and it does slow the system down **a bit**. But it sure doesn't cause the system to crawl as you describe it :D

---

### Post by Half-Left on 2009-01-04
> **scorp123 said:**
> I am unable to reproduce that here. I can even run VirtualBox and 3D shooters such as Nexuiz at the same time (therefore pretty much filling up my RAM) and yet my desktop feels *snappy enough*. The only real difference I can see is that it feels *even snappier* when I boot into my 64-bit partition.

But that "big overhead" talk and "snappy feeling is gone" is FUD. PAE isn't perfect yes, it's a workaround yes, and it does slow the system down **a bit**. But it sure doesn't cause the system to crawl as you describe it :D

This is WHAT overhead is, doesn't mean you can feel it because something may make up for that overhead. What I'm saying is that if it was not such a big deal then kernel devs wouldn't have put memory split in. No one wants unneeded overhead, low latency is good, it affects sound and responsiveness, you dont feel it because you have alots of ram, the over head will be there if you enable it on a system with 4Gb or less. PAE changes the way memory gets mapped inuring a overhead on systems with less than 4Gb.

I didn't say it would make your system crawl, I said if you read me right it gives a fair amount of overhead. Who in their right mind would want to run a PAE enabled kernel with 512mb-1Gb of ram?, answer noone and this is one reason why distros dont ship PAE enabled kernel by default.

---

### Post by scorp123 on 2009-01-04
> **Half-Left said:**
> Who in their right mind would want to run a PAE enabled kernel with 512mb-1Gb of ram?  Yes, I agree to that part. BUT: With memory less than 4 GB it's no big deal because your 32-bit standard kernel should be able to handle that. So it's unlikely that you would make use of PAE system calls even if it was turned on. Ubuntu Server ships with PAE enabled by default and I don't see people complaining about it ;)

> **Half-Left said:**
>  this is one reason why distros dont ship PAE enabled kernel by default. [LIST]
[*]RHEL 5.2
[*]CentOS 5.2
[*]Ubuntu Server
[*]OpenSUSE
[*]SLES
[/LIST] ... these distros either ship with PAE already turned on (e.g. Ubuntu Server) or they have a kernel package aside from their default kernel that has PAE turned on ;)

---

