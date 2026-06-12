---
title: "HURD kernel"
date: 2008-05-05
forum: Other OS Talk
---

### Post by kvk on 2008-05-05
A post born of my own programming ignorance. 

Why was the development of the HURD kernel such a major hurdle (um..okay, pun intended...) for Stallman, given his programming brilliance and the fact that Torvalds put the Linux kernel together in relatively short order? Was this due to Stallman wanting to write the entire thing himself, while Torvalds opened it up to everyone else?

Or am I completely off-base here?

Thanks! :)

---

### Post by SunnyRabbiera on 2008-05-05
Well Stallman is not alone on HURD, but as it stands there is no real interest in it.
HURD is actually practically from scratch, remember Linus built Linux knowing pre existing code.
Sure HURD is another unix like OS but it is built from the ground up, plus Linus had a lot of help.

---

### Post by p_quarles on 2008-05-05
Moved to Other OS Talk.

Stallman himself hasn't been an active part of HURD development for a while, if I remember correctly. He's been spending most of his time on activism for a number of years.

Without looking it up, my understanding is that HURD is a more technically difficult project than Linux. This, combined with the fact that the Linux kernel exists, works, and has reached maturity, makes it a more attractive project on which to work. The interest in HURD is more limited.

To exacerbate all that, hardware technology has advanced more quickly than HURD development, so in some respects HURD has effectively gone backwards, making it even less of an attractive project for potential developers.

---

### Post by p_quarles on 2008-05-05
Moved to Other OS Talk.

Stallman himself hasn't been an active part of HURD development for a while, if I remember correctly. He's been spending most of his time on activism for a number of years.

Without looking it up, my understanding is that HURD is a more technically difficult project than Linux. This, combined with the fact that the Linux kernel exists, works, and has reached maturity, makes it a more attractive project on which to work. The interest in HURD is more limited.

To exacerbate all that, hardware technology has advanced more quickly than HURD development, so in some respects HURD has effectively gone backwards, making it even less of an attractive project for potential developers.

---

### Post by Tatty on 2008-05-05
I am certainly no expert on kernels, but i was researching this a while ago and it appears that hurd is being designed as a microkernel as opposed to linux and the windows kernel which are written as monolithic kernels.

Microkernels are apparently notoriously much more difficult to write than monolithic kernels (see the wikipedia link below).  I assume this is probably a big reason as to the length of time hurd is taking.

But once again I stress I am certainly no expert so do not take my word for it, just dropping in my findings :)

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29#Kernel-wide_design_approaches](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29#Kernel-wide_design_approaches)

---

### Post by jrusso2 on 2008-05-07
> **Tatty said:**
> I am certainly no expert on kernels, but i was researching this a while ago and it appears that hurd is being designed as a microkernel as opposed to linux and the windows kernel which are written as monolithic kernels.

Microkernels are apparently notoriously much more difficult to write than monolithic kernels (see the wikipedia link below).  I assume this is probably a big reason as to the length of time hurd is taking.

But once again I stress I am certainly no expert so do not take my word for it, just dropping in my findings :)

[http://en.wikipedia.org/wiki/Kernel_%28computer_science%29#Kernel-wide_design_approaches](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29#Kernel-wide_design_approaches)

Apple's OS X uses the Mach kernel and it didn't take them over twenty years

---

### Post by SunnyRabbiera on 2008-05-07
> **jrusso2 said:**
> Apple's OS X uses the Mach kernel and it didn't take them over twenty years

Yeh but apple mostly based their work on BSD, HURD is almost from scratch

---

### Post by p_quarles on 2008-05-07
> **SunnyRabbiera said:**
> Yeh but apple mostly based their work on BSD, HURD is almost from scratch
Well, the Mach project was from scratch too, and has been in development for nearly as long as HURD. 

The BSD userland employed by OS X is more equivalent to the GNU userland employed by GNU/Linux distros. Neither provide the function of the actual kernel. 

Again, I think the main reason for the slow progress of HURD is the fact that there is already a GPL licensed, mature and stable kernel. The Mach kernel is appealing to a different business model (specifically, any model that isn't compatible with the GPL), so there was a need for it.

---

### Post by Dr. C on 2008-05-07
> **p_quarles said:**
> ...

Again, I think the main reason for the slow progress of HURD is the fact that there is already a GPL licensed, mature and stable kernel. The Mach kernel is appealing to a different business model (specifically, any model that isn't compatible with the GPL), so there was a need for it.

I agree why develop another Free kernel when there is Linux, Open Solaris and BSD? It really is no longer a priority for the FSF and for good reason. 

There are far more important priorities starting with Free 3d video drivers
[http://www.fsf.org/campaigns/priority.html]("http://www.fsf.org/campaigns/priority.html")

---

### Post by xirtus on 2009-01-17
because linux is aweful... just because its the best OS out there doesn't make it good... thats like winning against microsoft... so?

look at haiku its based on beos instead of using a linux kernel and it's something like 7-12 times faster... That doesn't mean a damn thing next to HURD

a brain isn't one organ, its really two made of many...

a microkernel will ineviabtly mean a lot of analog processes that the Monoliths have been relied on for and analog is always better, just more expensive...

Any guesses on how the government is doing? -with their secret, holographic 3d "conscious" kernel village?

---

### Post by xirtus on 2009-01-17
nb, the mach kernel in mac os is monolithic, its not really a HURD design, those chumps...

---

### Post by jrusso2 on 2009-01-17
> **xirtus said:**
> nb, the mach kernel in mac os is monolithic, its not really a HURD design, those chumps...

Its not Hurd but OS X AFAIK uses a Microkernel. Where is your source for saying it uses monolithic?  If that was true you would have to compile drivers for OS X?

---

### Post by saulgoode on 2009-01-17
> **jrusso2 said:**
> Its not Hurd but OS X AFAIK uses a Microkernel. Where is your source for saying it uses monolithic? 
OS X uses a hybrid derivative of Mach [called XNU]("http://en.wikipedia.org/wiki/XNU#Kernel_design"). It is neither strictly monolithic nor strictly microkernel.

> **jrusso2 said:**
> If that was true you would have to compile drivers for OS X?
Which is why [I/O Kit]("http://en.wikipedia.org/wiki/I/O_Kit") exists.

---

### Post by xirtus on 2009-01-17
thanks for getting there first, saul!


this has all been hashed out before by the dukes,

[I]"In short: just say NO TO DRUGS, and maybe you won't end up like the Hurd people."
-Linus Torvalds
[/I]


well I think if you want to look at functional microkernels you'd have to point to the MINIX system that was around before Linux. -I'm not saying it's beryl with the flashiest gui or anything, but people looking for instant gratification might need to start someplace else... Microkernel multiplexing is just the future.

awhile ago there was this clash of the titans see with the MINIX guy, a professer named Tanenbaum:

 *"Tanenbaum argued that since the x86 architecture would be outdone by other architecture designs in the future, he did not need to address the issue, noting &#8220;Of course 5 years from now that will be different, but 5 years from now everyone will be running free GNU on their 200 MIPS, 64M SPARCstation-5.&#8221; He stated that the Linux kernel would eventually fall out of taste as hardware would progress, due to it being so closely tied to the 386 architecture.[11] (See section &#8220;Erroneous predictions&#8221; for a detailed account of this claim.)"*


Then Linus admitted that microkernal systems are hyphier and theoretically more awesome.
[I]
>1. MICROKERNEL VS MONOLITHIC SYSTEM

True, linux is monolithic, and I agree that microkernels are nicer. With
a less argumentative subject, I'd probably have agreed with most of what
you said. From a theoretical (and aesthetical) standpoint linux looses.
If the GNU kernel had been ready last spring, I'd not have bothered to
even start my project: the fact is that it wasn't and still isn't. Linux
wins heavily on points of being available now.

>   MINIX is a microkernel-based system. [deleted, but not so that you
> miss the point ]  LINUX is a monolithic style system.

If this was the only criterion for the "goodness" of a kernel, you'd be
right.  What you don't mention is that minix doesn't do the micro-kernel
thing very well, and has problems with real multitasking (in the
kernel).  If I had made an OS that had problems with a multithreading
filesystem, I wouldn't be so fast to condemn others: in fact, I'd do my
damndest to make others forget about the fiasco.
[/I]


I think that really sums it up... Basically Linux is aweful, but an awefully lot better than the competition (for now) the question is what and when and how I guess.. I'm not being rhetorical lets work on it now! anyone have any ideas?

---

### Post by DeadSuperHero on 2009-01-17
I personally think the HURD developers just made a few mistakes along the way, but recent developments on their main site seem to point that they're making a lot of progress.

I'd also take a good look at HURD/Viengoos, which is a new HURD microkernel being written from scratch by Neil Walfield, who also did considerable amounts of work on L4.

I have some collected bits of info he sent me put on my hobby project blog, if anyone's interested. It can be located [here]("http://projectxoo.blogspot.com/2009/01/useful-info-on-viengoos-kernel.html").

---

### Post by 3rdalbum on 2009-01-19
GNU/HURD was designed as a true microkernel-based operating system, with a very complex design; in fact, it's still an ambitious design! That's why the HURD wasn't ready before Linux came along.

Mac OS X uses a hybrid kernel, as does Linux - some drivers and services run inside kernelspace, some run inside userspace. The reason why you don't need to compile drivers for Mac OS X is because they are all precompiled and the OS X kernel uses a stable ABI (Linux doesn't, for various good reasons).

---

### Post by gaffurabi on 2009-01-19
-as a noob and out of wonder-

if we ever get to use a stable (or mature if you would call it) version of HURD will it be 'awesome' because this microkernel does multitasking as never done before (since we have 64-bit duo and quadro cpu's today for mainstream computers)? will we be blown by its ultra speed and stability?

---

### Post by 3rdalbum on 2009-01-20
Stability: Yes, in theory. If one part of the "kernel" crashes, it can simply be restarted without affecting the rest of the system. That is, unless it's part of the actual real kernel.

Speed: Probably not. Microkernels are not generally faster than hybrid kernels, and are sometimes slower. Also, the kernel itself is not the heavy part of the operating system; Puppy Linux uses basically the same kernel as Ubuntu, but the two have vastly different system requirements.

---

### Post by rliegh on 2009-01-20
Hurd has switched kernels at least four times now (from ??? to GNUMach, from GNUMach to l4, now from L4 to Coyotos). 

Oh, and OSkit fits in there somewhere -probably under the GNUMach umbrella. If you count it as a seperate kernel than that's 5 kernels that they've tried to build the HURD on top of.

Then you also have the fact that the goals of GNU/HURD are abstract, and do not reflect any sort of real-world based need -so no one is going to rush to finish it.

We have UNIX (in the form of Solaris), BSD, Linux and Darwin -there's no particular niche that HURD fits that isn't already being filled.

Lastly, all of the interesting developments have moved from the kernel level to the network and application level: there's just not that much left to do on the operating system front -all of the interesting innovation and development will be on a higher, probably network application level.

tl;dr -HURD fills no need, and can't even decide on what kernel they're going to use -no one cares any longer and no one will.

---

### Post by jrusso2 on 2009-01-21
> **rliegh said:**
> Hurd has switched kernels at least four times now (from ??? to GNUMach, from GNUMach to l4, now from L4 to Coyotos). 

Oh, and OSkit fits in there somewhere -probably under the GNUMach umbrella. If you count it as a seperate kernel than that's 5 kernels that they've tried to build the HURD on top of.

Then you also have the fact that the goals of GNU/HURD are abstract, and do not reflect any sort of real-world based need -so no one is going to rush to finish it.

We have UNIX (in the form of Solaris), BSD, Linux and Darwin -there's no particular niche that HURD fits that isn't already being filled.

Lastly, all of the interesting developments have moved from the kernel level to the network and application level: there's just not that much left to do on the operating system front -all of the interesting innovation and development will be on a higher, probably network application level.

tl;dr -HURD fills no need, and can't even decide on what kernel they're going to use -no one cares any longer and no one will.

The void it would fill is for a GNU operating system which means GPL 3 kernel with no closed source anything the dream of RMS since the 80's

---

### Post by rliegh on 2009-01-21
> **jrusso2 said:**
> The void it would fill is for a GNU operating system which means GPL 3 kernel with no closed source anything the dream of RMS since the 80's

***Sooooooo***...it meets no **real-world need**; exactly as I said. 

Sorry -the world is desperately crying out for a large number of things (many of which are software related), but a gpl3-based kernel isn't one of them.

---

### Post by DeadSuperHero on 2009-01-21
> **rliegh said:**
> Hurd has switched kernels at least four times now (from ??? to GNUMach, from GNUMach to l4, now from L4 to Coyotos). 


Wrong. It started with GNU Mach, which is still going its own way, even though Mach is a flawed implementation. They considered L4 and Coyotos, but porting never really got far for Coyotos due to the fact that it's written in a new language known as BitC.

As for L4, they made considerable progress before realizing some horrific deficiency in it, and so Neal Walfield, engineer of HURD/L4, decided to start from scratch and correct the shortcomings in Viengoos.

Does it suit a "real world" need? For some people, definitely. But asking whether a Free Software GPLv3 kernel fills a need is tantamount to asking whether a GPLv2 linux kernel fills a need. Or a BSD kernel. Or a Solaris kernel. There are different pieces of software for different people with different preferences, there just doesn't happen to be a truly free, fully functional OS out there....yet! With all this dour, "realist" outlook on it, I'd be surprised if anything in the FOSS community would ever get done.

---

### Post by fistfullofroses on 2009-01-21
> **rliegh said:**
> ***Sooooooo***...it meets no **real-world need**; exactly as I said. 

Sorry -the world is desperately crying out for a large number of things (many of which are software related), but a gpl3-based kernel isn't one of them.

Umm... to be honest none of the stuff we use is "needed" there exists a more common *nix system (OS X), that has commercial support, and mainstream applications that are more compatible with major applications. There is also an operating in existence from this little upstart in Redmond that I hear has gotten a lot of support lately. So, is there a need for Linux? BSD? Solaris? V7? NO THERE IS NOT. Darwin from Apple is open source. Why use other *nixs? WE WANT TO. I am considering building a machine with an IDE HDD just so I can play with UNIX V7 some more. Come on! We are tinkerers. Hobbyists. Enthusiasts. One is never enough. For that matter, why did we create other operating systems at all, when UNIX was already there?

---

### Post by oswaldkelso on 2009-01-21
> **fistfullofroses said:**
> Umm... to be honest none of the stuff we use is "needed" there exists a more common *nix system (OS X), that has commercial support, and mainstream applications that are more compatible with major applications. There is also an operating in existence from this little upstart in Redmond that I hear has gotten a lot of support lately. 
What do OSX, and mainstream applications have to do with the GNU hurd kernel
> So, is there a need for Linux? BSD? Solaris? V7? NO THERE IS NOT. Darwin from Apple is open source. Why use other *nixs? WE WANT TO. I am considering building a machine with an IDE HDD just so I can play with UNIX V7 some more. Come on! We are tinkerers.Hobbyists. Enthusiasts. One is never enough
 Some users are Hobbyists and Enthusiasts. But others? like google, ibm and yahoo. hardly Hobbyists.
>  For that matter, why did we create other operating systems at all, when UNIX was already there?

"The name “GNU” is a recursive acronym for “GNU's Not Unix”; it is pronounced g-noo, as one syllable with no vowel sound between the g and the n."

[http://www.gnu.org/](http://www.gnu.org/)

---

### Post by cammin on 2009-01-21
Do you work for G'NU dot org or something?

---

### Post by fistfullofroses on 2009-01-21
> **oswaldkelso said:**
> What do OSX, and mainstream applications have to do with the GNU hurd kernel

 Some users are Hobbyists and Enthusiasts. But others? like google, ibm and yahoo. hardly Hobbyists.


"The name “GNU” is a recursive acronym for “GNU's Not Unix”; it is pronounced g-noo, as one syllable with no vowel sound between the g and the n."

[http://www.gnu.org/](http://www.gnu.org/)

My point is that the majority of computer users around the globe use OS X or Windows. All other operating systems are niche markets. An argument about usefulness is tailored to your specific needs, but in general most people will always default to OS X and/or Windows.

---

### Post by jrusso2 on 2009-01-21
> **rliegh said:**
> ***Sooooooo***...it meets no **real-world need**; exactly as I said. 

Sorry -the world is desperately crying out for a large number of things (many of which are software related), but a gpl3-based kernel isn't one of them.

You will have to talk to RMS about that I am not a free software fanatic.  But this would be his reasoning.

---

### Post by rliegh on 2009-01-22
> **fistfullofroses said:**
> Umm... to be honest none of the stuff we use is "needed" there exists a more common *nix system (OS X), that has commercial support, and mainstream applications that are more compatible with major applications. There is also an operating in existence from this little upstart in Redmond that I hear has gotten a lot of support lately. So, is there a need for Linux? BSD? Solaris? V7? NO THERE IS NOT. Darwin from Apple is open source. Why use other *nixs? WE WANT TO. I am considering building a machine with an IDE HDD just so I can play with UNIX V7 some more. Come on! We are tinkerers. Hobbyists. Enthusiasts. One is never enough. For that matter, why did we create other operating systems at all, when UNIX was already there?

There's not enough that is unique and interesting enough to draw mindshare to developing the HURD. 

If I was wrong you would have more than 10 people currently working on it. ;)

There isn't a serious amount of people who are tinkering with the HURD.

GNU/HURD is a hobby for *very few* people.

There's not only little enthusiasm for the HURD -it's actively considered a joke.

The reason for this is very simple -because there is nothing about it that is unique and interesting enough about it to make it worth anyone's time.

All of the OSes you listed have more to attracted people to them than simply the license. 

GNU/HURD --**only** has the license; and that's a priority for damned few people.
> **jrusso2 said:**
> You will have to talk to RMS about that I am not a free software fanatic.  But this would be his reasoning.

I lost respect for RMS after watching him spend a month trolling -yes, **trolling** the OpenBSD mailing list with the claim that because the ports infrastructure **suggests** non-free software that it meant that OpenBSD itself was non-free.

I have great respect for GNU software and the work they did in the 80's and 90's -but RMS himself has seriously lost the plot.

---

### Post by oswaldkelso on 2009-01-22
> **rliegh said:**
> 

GNU/HURD --**only** has the license; and that's a priority for damned few people.


I lost respect for RMS after watching him spend a month trolling -yes, **trolling** the OpenBSD mailing list with the claim that because the ports infrastructure **suggests** non-free software that it meant that OpenBSD itself was non-free.

I have great respect for GNU software and the work they did in the 80's and 90's -but RMS himself has seriously lost the plot.

Even if GNU/HURD only had the license, no matter how few people. Well I guess they think it reason enough for them. 

To be fair to RMS is this not the same or similar reason Debian, Fedora, Ubuntu etc are not in the free distro list? I don't think the **point** of the argument was BSD specific. Just they link to non free? 

[http://www.gnu.org/links/links.html#FreeGNULinuxDistributions](http://www.gnu.org/links/links.html#FreeGNULinuxDistributions)

---

### Post by Frak on 2009-01-22
I like the theoretic that HURD would be faster than the Linux kernel because of the multiple parts that consist of it. Even though, today, there would be no noticable improvements (maybe 20 years ago), it still seems to be a more stable structure.

---

### Post by oswaldkelso on 2009-01-23
> **Frak said:**
> I like the theoretic that HURD would be faster than the Linux kernel because of the multiple parts that consist of it. Even though, today, there would be no noticable improvements (maybe 20 years ago), it still seems to be a more stable structure.

I like the theory also, so I'm glad someone is still working on it.    
 
[http://code.google.com/soc/2008/hurd/about.html](http://code.google.com/soc/2008/hurd/about.html)
[http://www.nationmaster.com/encyclopedia/GNU-Hurd](http://www.nationmaster.com/encyclopedia/GNU-Hurd)
[http://en.wikipedia.org/wiki/File:OS-structure.svg](http://en.wikipedia.org/wiki/File:OS-structure.svg)

---

