---
title: "Source VS Binary Distros"
date: 2005-08-06
forum: Programming Talk
---

### Post by Luggy on 2005-08-06
Soon some group members and I will be taking part in a major project requiring quiet a bit of programming (taking data from a sensor, crunching numbers, displaying the data all pretty like). 

Our group leader is a major Gentoo (source) fan and insists that using a source based distro is the way to go for major programming projects like this (mostly from being able to exaime the source code of other projects for hints on what to do) . From my expirence with (AMD64) Gentoo I found that I hate compiling everything (emerge sync && emerge -uD world != fun).

I for the new rigs we will be using I was planning on using a binary distro (perferably Kubuntu) but is there any major advantage of using a source based distro for major programming projects?

---

### Post by LordHunter317 on 2005-08-06
There isn't, and he should be physically beaten for perpetuating such retarded myths.

Moreoever, you can get the source code on **any** distribution for the overwhelming majority of the software.  Certainly the same amount you can on Gentoo.

---

### Post by macgyver2 on 2005-08-06
[QUOTE=LordHunter317]There isn't, and he should be physically beaten for perpetuating such retarded myths.[/QUOTE]

I would have to say you're 99.9% right but would have to disagree ever so slightly...

Luggy said that this is a project involving "crunching numbers" but didn't say the magnitude of the crunching.  Now for the modelling I usually do it doesn't matter much because it's not too intensive.  For the part of my research that is intensive I log into a very nice shiny new Sun Blade and just run it there.  But were I to be doing that part on my own machine as well I'd rather go with a streamlined system built from source and optimized for what I need.

So...I don't think that it's entirely a "retarded myth".  Luggy's project leader may be exaggerating the computational needs of the project...then again maybe he's not.

[QUOTE=LordHunter317]Moreoever, you can get the source code on **any** distribution for the overwhelming majority of the software.  Certainly the same amount you can on Gentoo.[/QUOTE]

Of course that's true.  Were I to want to use my computer for some sort of intensive computational work--say n-body modelling or gas dynamics or...well you get the picture--I could just use Ubuntu and grab all the source packages for what I need on my system and rebuild them all, compiling in what I need and leaving out anything I don't...but that would actually be far more of a hassle than just using a source based distribution (like Gentoo).

---

### Post by npaladin2000 on 2005-08-06
You know, I think the question to ask is will taking the time ot compile the distro result in enough performance to offset that time penalty?  Or would it take less time overall to do it in a well-optimized binary distro?

I've installed Gentoo a couple of times.  Managed to get all the way through, learned a LOT, but it's an INCREDIBLE pain in the you-know-where. I saw little performance gain, and what little there was wasn't worth spending 8 hours on a base install. ;)

Meet him halfway...install a binary distro, grab the distro's kernel sources and custom-compile yourself a kernel.  You'll get a large portion of the whole "source distro" advantage just doing that. 

Incidentally, every time I try to custom-compile the Ubuntu Linux kernel sources, it comes out screwey and performes horribly.  I must be missing something, but I'm not done yet ;)

---

### Post by Luggy on 2005-08-06
Awesome, thanks for the advice guys!

---

### Post by LordHunter317 on 2005-08-06
> **macgyver2]Luggy said that this is a project involving "crunching numbers" but didn't say the magnitude of the crunching.[/quote]So?  It doesn't matter one bit.  I actually have much harsher words, but I'm not allowed to say them.

>  But were I to be doing that part on my own machine as well I'd rather go with a streamlined system built from source and optimized for what I need.Building from source is the worse way to get performance optimizations.

If you're code is entirely CPU-bound within itself, the speed of the rest of the system is irrelevant.  Why?  Because the rest of the system *isn't being called*.  Whether printf() takes 30ms or 31ms doesn't matter if you never call it to begin with, or if you call it outside a performance critical section.

> So...I don't think that it's entirely a "retarded myth".Yeah, it is.  The gain you get from compiling everything yourself is almost nothing said:**
> Of course that's true.Then why do Sun, IBM, SGI and a host of other companies not hand compile your OS on their 100+ CPU mainframes?

Oh yeah, because the speedup isn't worth the headache.  Not to mention it generally won't improve performance one tiny bit.

[quote=npaladin2000]Meet him halfway...install a binary distro, grab the distro's kernel sources and custom-compile yourself a kernel. You'll get a large portion of the whole "source distro" advantage just doing that.[/quote]Even this is silly.  Ubuntu provides optimized kernels for every subarch of x86 that it's worthwhile to do so for.

---

### Post by macgyver2 on 2005-08-06
Hey, I don't know what else to say other than I've been shown a couple instances where optimizing your system (it's *always* a good idea in scientific computing to optimize your own code) does lead to noticable performance benefits.

Like I said, for the one project I'm working on now...if I was subjected to using my own machine for it I would use optimized source (the program requires real-time output to X).  The rest of my work...no difference on Ubuntu vs. Gentoo vs. Red Hat vs. Solaris 9.

Anyway, I just think total vehement denial of the possible benefits is too extreme because there *are* cases (yes, they're limited...but they're still there) where optimizing your system can help.  It depends as much on the circumstances of the project as anything else.

---

### Post by LordHunter317 on 2005-08-06
[QUOTE=macgyver2]Hey, I don't know what else to say other than I've been shown a couple instances where optimizing your system (it's *always* a good idea in scientific computing to optimize your own code) does lead to noticable performance benefits.[/quote]Provide specific cases then, preferably with provable numbers.  No one's ever been able to provide a valid case.

> Like I said, for the one project I'm working on now...if I was subjected to using my own machine for it I would use optimized source (the program requires real-time output to X).You can't get such a thing as true real-time output to X, so I know this isn't true.  Anyway, the X server is about as optimized as it can be, and further optimization via compiler is not going to really improve your performance any.  Protocol and X server architecture just doesn't allow for it, really.

The stuff the X server will be able to optimize are the low-level drawing routines and the like: which won't help you substantially if your output is OpenGL, and for 2D, you have tons of other overhead to shed that'd give you much more substantial improvements.

So unless you're making direct X toolkit calls, I don't buy it.

> Anyway, I just think total vehement denial of the possible benefits is too extreme because there *are* cases (yes, they're limited...but they're still there) where optimizing your system can help.They are tiny and the gains are tiny.  If they were so significant even for just a few cases, why don't operating system vendors support it?

The very fact no vendors do, and the fact many of those vendors sell systems designed for this kind of work, tells me that there isn't much merit to these claims.

---

### Post by macgyver2 on 2005-08-06
[QUOTE=LordHunter317]Provide specific cases then, preferably with provable numbers. No one's ever been able to provide a valid case.[/QUOTE]
Unfortunately I can't give details about what was done. But it was consistently faster. Sure, small gain, but faster. A few percentage points...a couple minutes or so for each run that took about an hour.

[QUOTE=LordHunter317]You can't get such a thing as true real-time output to X, so I know this isn't true.[/QUOTE]
Lemme rephrase, as this was probably my mistake in terminology. By real-time output to X I was referring to plots being drawn on the screen while the modelling code is still running. "Real-time"...as opposed to what I'd refer to as not real-time where the whole plot is displayed at once after all the crunching is done instead of being continuously updated, and "to X" means well, to X. I mean, how else can I phrase it...the output shows up on my screen in X.  What would be a better way to say that?

[QUOTE=LordHunter317]They are tiny and the gains are tiny. If they were so significant even for just a few cases, why don't operating system vendors support it?[/QUOTE]
Because for the few cases that warrant it, the users can just do it themselves. Woo, we could go on for awhile if we were to find everything everyone on these forums was doing with their systems that isn't "supported" by any vendors. Once again, this seems like a definition thing. There's a difference between support and support.

[QUOTE=LordHunter317]The very fact no vendors do, and the fact many of those vendors sell systems designed for this kind of work, tells me that there isn't much merit to these claims.[/QUOTE]
This brings to mind the saying, "lack of proof doesn't imply proof of lack."

Anyway, I guess we'll just have to agree to disagree, and hey, if you want to say I'm clinging to a retarded myth, go for it. Doesn't bother me.

But please, no more "physically beaten" stuff!

---

### Post by LordHunter317 on 2005-08-07
[QUOTE=macgyver2]Unfortunately I can't give details about what was done. But it was consistently faster. Sure, small gain, but faster. A few percentage points...a couple minutes or so for each run that took about an hour.[/quote]And what did you change?  It's doubtful the whole system need to be recompiled: the gains from having a correct kernel and a correct libc6 make all the difference in most cases, and the gains can be quite real for some applications.  But hey look: that's two small pieces of a whole operating system, and something Ubuntu provides OOB, even.

And even still, you have to prove the difference actually matters.  Using the fastest sort routine doesn't make a difference if a slower one can still sort all the data before the next batch comes in.  Being I/O bound to something slow (like most programs are) makes performance largely irrelevant in lots of cases.

> Lemme rephrase, as this was probably my mistake in terminology. By real-time output to X I was referring to plots being drawn on the screen while the modelling code is still running.And?  That's not performance sensitive by any means, quite likely.  Whether the user sees the data 100ms after it was modelled or 500ms after it was modelled matters quite little.

Moreover, the gain you'd get from recompiling X would be on the order of a few ms in most cases (like, 1-2) and wouldn't always happen: other factors can induce much larger latencies that you can do nothing about.  So why go through all that effort when it's likely if you need the performance, you can get it by editing your own code, and have it in all cases?

> What would be a better way to say that?The issue is, it's not a true real-time application.  True real-time means you have very short time periods in which a task must be completed: usually a few tens of ms, sometimes less.  And they require operating systems where latencies are fixed and guaranteed, like QNX.

You can have other things that are close to real-time, like video conferencing.  Losing A/V sync by more than 100ms or so is quite jaring to a human, that's about the limit of our perception.  But 100ms is still a huge window, certainly large enough not to require anything special on the part of *the whole system* to obtain reliably.

Your application is *psuedo* real-time.  Meaning, you're updating the display continuously, but it doesn't matter (within reason) how long it takes between when the data is done modeling and the graph is displayed.  If it takes a few extra ms, or even seconds, it doesn't matter. 

> Because for the few cases that warrant it, the users can just do it themselves.That's just it: no cases warrant it.  If they did, they be paying the vendors to do it.

You don't pay several *million* dollars for a HPC setup and then go and run software on it in a configuration your vendor isn't willing to support.

Which is my whole point: if companies where every single wasted cycle costs money aren't doing it, then why should you?  Obviously, the gains aren't worth the cost to them, so it's really doubtful they can be worth it to you.

That's the whole problem: what you suggest literally doesn't align itself with enterprise realities.  

> Woo, we could go on for awhile if we were to find everything everyone on these forums was doing with their systems that isn't "supported" by any vendors.What people here are doing are irrelevant.  They're not the ones doing tasks that are truely performance/time/money sensitive to even truly require those types of micro-optimizations.

>  Once again, this seems like a definition thing.No, it's a you refuse  to except your idea doesn't match reality thing.  Really.  Everyone who thinks it's worthwhile just hasn't played in the HPC arena much.

> This brings to mind the saying, "lack of proof doesn't imply proof of lack."What?  Yes, if you can provide no support for your argument, especially in the face of strong proof for the other side, it's hard to take your views seriously.

It's not like my points are without merit.  When SGI starts shipping Altixes where every invididual one has had all the software compiled on it personally, call me.  I know mine didn't.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=LordHunter317]Even this is silly.  Ubuntu provides optimized kernels for every subarch of x86 that it's worthwhile to do so for.[/QUOTE]

There's no Pentium M arch (VERY different from P4; I've been advocating this in Linux ever since the whole Centrino bit started) and the i686 kernel isn't working right with the ipw2200 drivers.  That reminds me, I have to boot into it and break it again so I can file a bug report...

---

### Post by LordHunter317 on 2005-08-07
> **npaladin2000]There's no Pentium M arch (VERY different from P4 said:**
> Yes, a Pentium-M is closer architecturally to a P3.

However for both processors, the gains you get over running a 686 kernel are somewhat small.  Certainly, you get the majority of the gain by going to 686.

[quote]and the i686 kernel isn't working right with the ipw2200 drivers.Well, I've had stability issues of all sorts with all of Ubuntu's kernels.  I've even tried hunting them down (by comparing the patches to Debian, where I have no problems) and have been unsuccessful.

---

### Post by macgyver2 on 2005-08-07
Thanks for the clarification of what is "real-time" and what is "psuedo real-time".

As for everything else, I feel like it's useless for me to try to convince you anymore and I don't want it to turn into some flamewar. ](*,)

Now then, I'm going to continue living in my fantasy-land where I apparently see things that don't exist, and I'll be happy that they don't require your belief to work.

Oh, and what I meant with that saying...just because OS vendors might not support something OOB does not mean that that something is not possible.  But that makes me think of something else.  If none of this optimization stuff does anything, why have it in the first place?  Why support something useless?  If a system runs the same no matter if I use the base 386 compiled stuff or something that was compiled specifically for a Pentium IV...why is the option to compile specifically for that Pentium IV even available?

---

### Post by LordHunter317 on 2005-08-07
[QUOTE=macgyver2]As for everything else, I feel like it's useless for me to try to convince you anymore and I don't want it to turn into some flamewar. ](*,)[/quote]That's because **you have no proof**.    It's hard to convience someone when you just say, "XXX exists".  Provide an example, "well, it happened this one time and gave us some numbers, but I'm not going to tell you."

And guess what: everytime I've asked someone to provide proof, that's the response I've gotten.  No one has ever been able to shown provable, repeatable speed ups by doing whole, specific-system recompiling.  It's very much a placebo effect. 

And anyone who's spent any time profiling any code would know that.  Performance-critical sections are very small, and rarely are what you expect them to be.  And the solution is never: compile the application with different flags to make it go faster.  

>   But that makes me think of something else.  If none of this optimization stuff does anything, why have it in the first place?Because for **certain** applications, they do make a huge difference.

But for the applications you do, you can get optimized binary packages on just about any distribution.  A common example of applications that do matter are the ones that do heavy audio/video encode/decode.  And hey look, you can get optimized mplayer binares for just about every processor type of x86.

> If a system runs the same no matter if I use the base 386 compiled stuff or something that was compiled specifically for a Pentium IV...why is the option to compile specifically for that Pentium IV even available?Because the compiler has to compile all software, including the software where it makes sense to?

You can't deduce just because the compiler will let you specify CPU type for any code, that it's a good idea to do so.  The compiler has to support any file that's thrown at it, including those that will see gain, those that will see no gain, and those that won't even run under certain cpu flags.

---

### Post by az on 2005-08-07
This is getting repetitive.  Let's move on, please.

---

