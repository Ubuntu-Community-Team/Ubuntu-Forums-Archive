---
title: "I wish linux was a Coyotos-like kernel"
date: 2007-02-26
forum: Other OS Talk
---

### Post by Nils Olav on 2007-02-26
That would make kernel hacking fun.

---

### Post by mips on 2007-02-26
Could you elaborate a bit more as i have no idea what you are referring to ?

---

### Post by huwnet on 2007-02-26
[http://coyotos.org/](http://coyotos.org/) ?

---

### Post by Nils Olav on 2007-02-26
> **huwnet said:**
> [http://coyotos.org/](http://coyotos.org/) ?

yep, thats what I was talking about.

---

### Post by TechZilla on 2008-02-04
i like our kernel the way it is :P nice and monolithic :popcorn:

..... but coyotos is one of the canidates for the GNU hurd.  i think it would be a great choice, and to finally have that damn kernel finished would be great.

---

### Post by Darkhack on 2008-02-05
This is very quickly going to turn into a monolithic versus microkernel debate.  It should probably be moved into Recurring Discussions.

I hate to be the first to fire the shot heard around the forum, but let me just say this.  There is a good reason why Windows, Mac, Linux, BSD, and Solaris all use monolithic kernels.  QNX is the only notable microkernel based OS I can think of that actually does all the wonderful things microkernel proponents push.  Of course QNX could just as easily have been written as a monolithic kernel and been just as stable.  It probably would have cost less in R&D too.

Yes, there are other microkernels but QNX is a complete operating system.  There aren't many operating systems built on Mach, Coyotos, or L4 that aren't just a big monolithic subsystem running on top (which doesn't count and don't give me that "hybrid" line which is just marketing).

---

### Post by SunnyRabbiera on 2008-02-06
Yeh but Minix is making some progress and thats a microkernel

---

### Post by xirtus on 2009-01-17
this threat is mislabeled, because it talks about changing the linux kernel.. this is a silly idea, leave linux alone... as in all alone... abandoned on an island... 

I think we should all be versed in the coming age of HURD... I mean I respect where we've come from through linux but we need to focus on where GNU is going.. Lets face it: we live on a monolithic plane in a multicore world and its Linus Torvald's fault...

Inevitably we will switch to HURD, the real question is when and how? are we goin to abandon Linux before or after the switch? Are we going to slowly ease into the HURD pool, slowly tiptoeing in from our linux system's like some did with Microsoft? or is this a full immersion, fresh start the rats in Secrets of NIMH?

I'd go ahead and say both, just like linux was, only thank baphomet that this time we've got the GNU libraries and all the crap we helped make in LiGNUx is GPL, so it won't be another microsoft

---

### Post by jrusso2 on 2009-01-17
> **xirtus said:**
> this threat is mislabeled, because it talks about changing the linux kernel.. this is a silly idea, leave linux alone... as in all alone... abandoned on an island... 

I think we should all be versed in the coming age of HURD... I mean I respect where we've come from through linux but we need to focus on where GNU is going.. Lets face it: we live on a monolithic plane in a multicore world and its Linus Torvald's fault...

Inevitably we will switch to HURD, the real question is when and how? are we goin to abandon Linux before or after the switch? Are we going to slowly ease into the HURD pool, slowly tiptoeing in from our linux system's like some did with Microsoft? or is this a full immersion, fresh start the rats in Secrets of NIMH?

I'd go ahead and say both, just like linux was, only thank baphomet that this time we've got the GNU libraries and all the crap we helped make in LiGNUx is GPL, so it won't be another microsoft


They have been working on the Hurd Kernel for 19 years and it still has a long way to go.  Where do you get the idea that we will end up on the Hurd kernel.  I don't think GNU has the programming talent to finish it or it would have been done years ago.

---

### Post by xirtus on 2009-01-17
> **jrusso2 said:**
> ...I don't think GNU has the programming talent to finish it or it would have been done years ago.


Well said, and don't you feel ashamed?

I don't mean *you*

I just mean us really.. I mean way to go us, jumping on the monolithic bandwagon, sacrificing freedom for openness... There is a difference mind you (-I don't trust sudo, reminds me of the queen... gimme root!) we should remind people, get students interested to use HURD as research projects, and throw some of ubuntu at it. I don't know why the universities haven't gone for HURD, but that would be a start..

Frankly I don't know what it will take to make multithreading multiplexing multicore multimicrokernel systems the dominant system, probably chips printed nano-layers at a time with crazy psudoscifi 3d holographic laser printing machines... but I'd like to be a realist and try to use what we have today and working toward the future one small step at a time.

Though two things are true:

one: when we get there, linux GPL libraries will flood in, opening the door to the new system infinitely faster than the growth of linux was.

two: when it works, it will work more effeciently than anything we've engineered to function thus far, and will for all intensive purposes, render at least all non-classified OS; including linux, obsolete.

---

### Post by DeadSuperHero on 2009-01-17
Hear, hear, xirtus! Well said!

---

### Post by Grant A. on 2009-01-17
Microkernels are only good for embedded devices, that's about it. Look, even the creator of MINIX has started gearing his Microkernel towards embedded devices.

All kernels have their ups and downs, but I truly think hybrid kernels are the way to go. Look at Mac OS X and Windows, they are both hybrid and the most successful operating systems ever to be released.

---

### Post by Frak on 2009-01-17
> **xirtus said:**
> one: when we get there, linux GPL libraries will flood in, opening the door to the new system infinitely faster than the growth of linux was.

two: when it works, it will work more effeciently than anything we've engineered to function thus far, and will for all intensive purposes, render at least all non-classified OS; including linux, obsolete.

That would have been true 15+ years ago. Though, today, the difference in speed would be negligible, let alone negative due to it's (mature) infancy. Our hardware is so advanced today, compared to then, that such a small process (or cluster thereof) runs within the same hypothetical performance bracket.

---

### Post by DeadSuperHero on 2009-01-17
> **Grant A. said:**
> Microkernels are only good for embedded devices, that's about it. Look, even the creator of MINIX has started gearing his Microkernel towards embedded devices.

All kernels have their ups and downs, but I truly think hybrid kernels are the way to go. Look at Mac OS X and Windows, they are both hybrid and the most successful operating systems ever to be released.

True, but I also think marketing would be a contributing factor to their successes. With backing of a major corporation and a paid workforce, Microsoft and Apple are able to have a better turnout rate for their products in comparison to Free Software projects.

However, I think that with enough research and experimentation, you could really go far with microkernel experimentation. Heck, look at QNX or AmigaOS.

In any case, I think it ultimately depends on the development method. With enough planning and enough dedicated workers, I think a microkernel could do just as well, or even better than a hybrid kernel someday.

That's the beauty of experimentation. Take airplanes, for example. A hundred years ago, anyone that suggested using flight as a means of travel would be laughed out of the patent office. Although you can always argue the semantics of something, it takes real experimentation to prove others wrong. Such is the beauty of science, and it's part of the reason why I like the FOSS development model more.

---

### Post by Grant A. on 2009-01-17
> **Mr. Psychopath said:**
> True, but I also think marketing would be a contributing factor to their successes. With backing of a major corporation and a paid workforce, Microsoft and Apple are able to have a better turnout rate for their products in comparison to Free Software projects.


Linux is supported by major corporations too... with a paid workforce... IBM employs 60% of the kernel devs...

> 
Heck, look at QNX or AmigaOS.


Both nearing End-of-Life

---

### Post by DeadSuperHero on 2009-01-17
> **Grant A. said:**
> 
Both nearing End-of-Life

Only due to the fact that they're proprietary, and their own companies simply didn't have the funds, advertising, or means to really go on. One need only look at the pathetic excuse of a company that Amiga has become. It's a darned shame.

In any case, you missed my point, I think. I was aiming at the quality of those Microkernel-based OS'es, not how well they've sold.

---

### Post by Grant A. on 2009-01-17
> **Mr. Psychopath said:**
> Only due to the fact that they're proprietary, and their own companies simply didn't have the funds, advertising, or means to really go on. One need only look at the pathetic excuse of a company that Amiga has become. It's a darned shame.

In any case, you missed my point, I think. I was aiming at the quality of those Microkernel-based OS'es, not how well they've sold.

Well, market-share is usually linked to how well a product sells, and the quality of it.

---

### Post by DeadSuperHero on 2009-01-17
> **Grant A. said:**
> Well, market-share is usually linked to how well a product sells, and the quality of it.
I disagree on that last bit. Look at Windows, it's preinstalled on virtually everything. While it does most things for the average joe, I personally think it's crapware. Still, people buy it out of sheer convenience of it being there because people don't bother putting an effort into improving the situation much.

---

### Post by MaxIBoy on 2009-01-17
In this era of multi-cored processors, one might think that microkernels would provide a major benefit.

WRONG!

In fact, the kernel uses a very small portion of the total CPU cycles. Optimizing the kernel itself for SMP isn't going to help. The performance benefit is so marginal that you'd only feel the difference on a very old processor, and when is the last time you saw a dual-core i486? 


BUT:
Modularity is important, too. And the ability to effectively *manage* multiple processors is also important. Even if the kernel only uses a single core, it has to be able to schedule parallel tasks. And the ability to swap out drivers would be nice.




I'm not going to draw any conclusions, but I'd like to point out Plan 9 from Bell Labs. (Correct me if I'm wrong, I'm not sure if I understand this fully.) It's a hybrid kernel, but it's truly distributed-- you could use a graphics card from one computer, a processor from a second computer, a sound card from a third computer, a keyboard from a fourth computer, and a mouse from a fifth computer, all running a single copy of the OS and united through a communications protocol called 9P. Everything is modular. Device drivers run as processes called "servers," each of which has its own set of permissions. Everything is a file (whereas, in Linux, everything is a file, except when it isn't.) Everything is abstracted (the window manager provides a virtual screen, keyboard, and mouse to every program, and every program thinks it's running "full-screen.") 

Plan 9 does a good job of managing tons of different assets in parallel, without being a full microkernel. Just something to think about.

---

### Post by xirtus on 2009-01-18
I understand why in the traditional method of interpolating data under a monolithic architecture results can be less notifiable but comparing translated results would be equivelent to comparing 32bit runtimes on a 64bit machine; it's just apples and oranges... A new system means new rules and a new way of doing things, it could be startlingly more efficient.

hybrid kernels can be extraordinary. Does anyone know about the new open-source BEOS project Haiku? From what I've seen they use a hybrid kernel and get a lot of improved results. Because of the way the programs are loading under the hybrid structure, side effects include two to three second boot times (just like in good old BEOS) and (once reconfigured to be read and able to run) program boot times are 7-12 times faster. Similarly the Darwin OS under MACOS employs a hybrid BSD kernel, -Darwin was NEXTSTEP, BEOS' contemporary)

---

### Post by smartboyathome on 2009-01-18
I've actually used Haiku on my old computer. It flew, with the only memory hog being Firefox (of corse, since it can't run in 100mb ram ;)).

---

### Post by xirtus on 2009-01-19
This is the most exciting this I've seen all year, and it's already the 19th...
[http://multixden.blogspot.com/2006/02/gnu-world-gnustep-on-hurd.html"]GNUSTEP with HURD]("gnustep on HURD")

Now I'm not going to preach linux, but there isn't a fancy button about HURD so I think it's cool to say HURD is LORD! gosh we should have an acronym LORD, but I can't think of anything besides "Linux Occultists Raising Demons" 
...maybe let it go...

Wouldn't Haiku and HURD make interesting bedfellows?

---

### Post by mips on 2009-01-19
> **Mr. Psychopath said:**
> One need only look at the pathetic excuse of a company that Amiga has become. It's a darned shame.


+1 Amen to that brother!   I wish they would open source the OS and put the trademarks into some form of foundation.

Btw, did you guys now the Amiga kernel, Exec, was a microkernel and a pretty efficient one at that as well.

---

### Post by cammin on 2009-01-19
> **mips said:**
> Btw, did you guys now the Amiga kernel, Exec, was a microkernel and a pretty efficient one at that as well.

That's why it was first mentioned in this topic.

---

