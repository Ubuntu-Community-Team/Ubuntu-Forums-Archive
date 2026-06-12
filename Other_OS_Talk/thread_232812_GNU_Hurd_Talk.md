---
title: "GNU Hurd Talk"
date: 2005-07-30
forum: Other OS Talk
---

### Post by Brunellus on 2005-07-30
We've been talking a lot about alternative versus replacement OSes for a while now, so I figure I'll ask about another alternative os--

So whatever happened to the GNU HURD project?  I'm aware of its existence, and I"ve read the website...but is that project actively being developed?  And what, if any, benefits will the HURD kernel have for users?

---

### Post by DJ_Max on 2005-07-30
The Debian GNU/Hurd is under development is under active development, so is the GNU Hurd project. But neither should be used in a production environment, in other words, don't use them if you want a stable system. 

From what I'm reading, Hurd is a replacement for the Unix kernel, unlike Linux which is based on some of the ideas. Hurd is more Unix-like then Linux, but no so much as BSD.

---

### Post by BWF89 on 2005-07-30
"In short: just say NO TO DRUGS, and maybe you won't end up like the Hurd people."
-**Linus Torvalds**

---

### Post by bgstratt on 2005-07-30
The idea behind Hurd is to build an os that is perfect, not just throw together something that works.  The big joke is that it may be perfect, but doesn't work.  It does work, but you probably won't find much on it, Hurd tends to be to GNU/linux as GNU/linux is to windows, not in terms of working, but just obscurity.  The ideas behind it are great, but the follow through that we are able to see leaves much to be desired.  You might remember the article on BSD where one of the devs is attributed the quote that linux is just a bunch of hacks and BSD is "better" or more correct, or something like that, I can't remember the exact line, but you get the same idea from the Hurd people, not gnu/linux bashing, but trying to get something that is perfect, not just a bunch of hacks, or something thrown together just to make a sale.

I guess the rest of that is just being trollish, but to answer your questions again, it is being actively developed, and it is supposed to bring us to a more perfect system, instead of a bunch of workarounds or hacks.  If you ask me though, who cares if it's a hack or a workaround, as long as it does the job like I want it to.  That's one of the basic premises of GNU/Linux, and the reason for Linux, to get the computer to do what you want it to do, not what someone else wants it to do.

---

### Post by poofyhairguy on 2005-07-30
Hurd is a microkernel design with years of work. Linux came along with its simplier monolithic kernel and created the GNU operating system and Hurd never recovered.

---

### Post by jdodson on 2005-07-31
I for one welcome our new HURD overlords.....

Wait, im not on Slashdot.... Ok.

;)  Anyways, HURD is cool, I think they should keep hacking on it, I will use it when it is ready.  However, I am not sure it will ever be as good as Linux, though it would not upset me if it were so, I would actually enjoy the added choice in the kernel arena.

---

### Post by NeoSNightmarE on 2005-07-31
The Linux kernel has worked good for me so far on this computer so I'll keep it. As for if I get another computer and it's released...I dunno about that. May try it out on there. But on the main computer I'm going to keep the Linux kernel.]

And that was funny jdodson. It's so true though about the /. comments and all that. It's pure comedy reading most of them. :grin:

---

### Post by ubuntu_demon on 2005-07-31
a bit of competition is always good. linux is the most userfriendly unix I know (except from OS X). Maybe in a couple of years there will be an Ubuntu Hurd :)

---

### Post by BWF89 on 2005-07-31
I was reading in an article a few months ago and it said that the HURD won't support hard drives partitioned above 3GB. And didn't RMS allready say that the HURD was basically dead?

Mabye in the future if alot more people are useing GNU/Linux & BSD operating systems interest in developing it will spark and we'll have 2 competeing kernals but I kinda doubt that since Linux kernal has become the norm.

---

### Post by detyabozhye on 2006-05-23
They say that the Hurd is being "actively" developed. Where can I get regular updates on this "activity"? Maybe we'll have a completely 100% perfect OS in 3006?

---

### Post by Lovechild on 2006-05-23
[QUOTE=BWF89]"In short: just say NO TO DRUGS, and maybe you won't end up like the Hurd people."
-**Linus Torvalds**[/QUOTE]

Linus Torvalds, one of the great communicators of the 21th century.

You shouldn't listen to much to him on these matters, Linus is known to be against microkernels for his own reasons.  It doesn't make him the keeper of the ultimate truth.

HURD does rather well considering that they have maybe 5 active developers at any given time and have been forced to switch the underlying microkernel a number of times to reach what they deem a good system. 

However HURD might be irrelevant as a Linux replacement the next decade because it's simply not supported by as many people as Linux is, nor developed for that matter.

If you want an off the shelf Open Source OS to replace Linux, OpenSolaris and the BSDs are quite acceptable choices today. HURD might take a little longer to get to the same level, but I have no doubt that it will eventually get there.

---

### Post by prizrak on 2006-05-23
The HURD project is pretty much dead. It is quite possibly the victim of what Torvalds said about microkernel OS's. The messaging system between the kernel and it's parts is way too complex to be useful and too bug prone. Microkernels work well in real time and embedded OS's where there is a limited number of devices to interact with and hardware is largely uniform. In a PC environment there is way too much stuff to pass around. Microkernel OS's also tend to be harder to develop.

---

### Post by RAV TUX on 2006-05-23
I burned the iso image of Debian Hurd K11, I couldn't get it to run but it may have been errors on my part. I have also been unsuccessful to get SUSE, Fedora, Scientific Linux  and Mepis to run. So this isn't exactly an exclusive negative against the Hurd. 

The default partitioning tool in the Hurd install is easier and more superior then any I have used.

---

### Post by detyabozhye on 2006-05-23
But do they have any logs, feeds, whatever so u can follow the developement anyway?

---

### Post by Virogenesis on 2006-05-23
[http://en.wikipedia.org/wiki/GNU_Hurd](http://en.wikipedia.org/wiki/GNU_Hurd) has a bit about it and what have you incase anyone wants to know anymore.

---

### Post by Rhapsody on 2006-05-24
I do like the indirect recursive acronym of HURD (where HURD stands for HIRD of Unix-Replacing Daemons, and HIRD stands for HURD of Interfaces Representing Depth) but I think the complexity of trying to actually remember all that speaks for the whole system. It'd be nice if some sort of stable version emerged some day, but it's classic vapourware at the moment. Sounds great, but when can we actually use it?

---

### Post by RAV TUX on 2006-08-09
currently installing GNU Hurd, I was wondering if any of my fellow Ubuntu users have had experience with the Hurd? Specifically: Debian K11 GNU Hurd.

Rich, have you tried it?

---

### Post by hizaguchi on 2006-08-09
I messed around with installing it a while back, but the documentation is kinda sparse and scattered around the internet, and different guides conflict with each other quite a bit.  Considering all of this, and the fact that the OS is so unfinished that wireless networking (a must for my laptop) is not yet finished, my attention span wore thin after the 2nd attempt to get it to boot.

It's a cool idea, and I'm all about supporting Gnu, but it's not ready for my needs yet.

---

### Post by RAV TUX on 2006-08-09
> **hizaguchi said:**
> I messed around with installing it a while back, but the documentation is kinda sparse and scattered around the internet, and different guides conflict with each other quite a bit.  Considering all of this, and the fact that the OS is so unfinished that wireless networking (a must for my laptop) is not yet finished, my attention span wore thin after the 2nd attempt to get it to boot.

It's a cool idea, and I'm all about supporting Gnu, but it's not ready for my needs yet.

I haven't done enough drugs to appreciate GNU Hurd.

---

### Post by TravisNewman on 2006-08-10
I've had it up and running once. It's a pain. Really not worth the trouble honestly. I hope it gets better, but the Linux, Solaris, and BSD kernels are already enough to suffice for me.

---

### Post by fluffnik on 2006-08-13
Plan9 is as strange as I've got.

There's a live CD and the best ever mascot too.  :)

---

### Post by Shay Stephens on 2006-08-30
That name alone tells me the project won't get anywhere.  Complexity for complexities sake is death to progress.  It's just showing off.

> **Rhapsody said:**
> HURD (where HURD stands for HIRD of Unix-Replacing Daemons, and HIRD stands for HURD of Interfaces Representing Depth)

---

### Post by jdong on 2006-08-30
> **ubuntu_demon said:**
> linux is the most userfriendly unix I know (except from OS X).
Oh boy, that's what I thought too, but I had to work for a while in OSX's command line via ssh... and that was not user friendly by any means :-/


Linux has the most user friendly CLI that I know

---

### Post by ubuntu_demon on 2006-08-31
> **jdong said:**
> Oh boy, that's what I thought too, but I had to work for a while in OSX's command line via ssh... and that was not user friendly by any means :-/


You are responding on a comment from "July 31st, 2005" :)

I think Ubuntu is rapidly gaining on OS X regarding usability. IMHO for a lot of use cases Ubuntu is as easy/userfriendly as OS X already. In some ways Ubuntu is even easier than OS X because Ubuntu uses central software repositories for software (which has lots of software which is not written by Canonical/Ubuntu developers)

> **jdong said:**
> 
Linux has the most user friendly CLI that I know

same here (although it's not that I have tons of expierence using other CLI's)

---

### Post by jdong on 2006-08-31
lol, I like to dig things up like this..... but yeah, I absolutely agree that Ubuntu is quickly becoming one of the most usable OS'es. I'm gonna give Edgy knot2 a try today. Hope to be impressed :)

---

### Post by ubuntu_demon on 2006-08-31
> **jdong said:**
> lol, I like to dig things up like this..... but yeah, I absolutely agree that Ubuntu is quickly becoming one of the most usable OS'es. I'm gonna give Edgy knot2 a try today. Hope to be impressed :)
Cool I didn't know Edgy Eft Knot 2 was released :-D

But I don't see a download link here :
[http://www.ubuntu.com/testing/knot2](http://www.ubuntu.com/testing/knot2)

---

### Post by bruce89 on 2006-08-31
> **ubuntu_demon said:**
> Cool I didn't know Edgy Eft Knot 2 was released :-D

But I don't see a download link here :
[http://www.ubuntu.com/testing/knot2](http://www.ubuntu.com/testing/knot2)

It's not release yet, but it is scheduled for today.  There was a large D-Bus transition yesterday mind you.

---

### Post by jdong on 2006-08-31
> **bruce89 said:**
> It's not release yet, but it is scheduled for today.  There was a large D-Bus transition yesterday mind you.


You mean it's **knot** released yet, right?

(sorry, couldn't resist)

---

### Post by Brunellus on 2006-08-31
wow.  my HURD thread is back from the dead.

I should say that having done a bit of reading up on the subject, I think I can see why the HURD should be the wave of the future.  But it just seems so irrelevant

---

### Post by Shay Stephens on 2006-08-31
> **Brunellus said:**
> wow.  my HURD thread is back from the dead.

I should say that having done a bit of reading up on the subject, I think I can see why the HURD should be the wave of the future.  But it just seems so irrelevant

I was doing some research on the mythical hurd to see when it would be available.  I found out that it was already available.  The I started looking to see if anyone was using it.  And that is when I ran across your thread :-)

After having slept on it, there is a chance that hurd is ahead of it's time, and will only see it's time in the sun later on down the line.  What if, due to shortcuts taken early on and the like, linux hits a brick wall and can't make any more forward progress (like windows is experiencing now).  Then, perhaps, hurd might be able to offer something.  Just some wild speculation ;-)

---

### Post by ubuntu_demon on 2006-08-31
> **bruce89 said:**
> It's not release yet, but it is scheduled for today.  There was a large D-Bus transition yesterday mind you.
Thanks for the information. I'm a bit busy these times that's why I didn't know.

---

### Post by jdong on 2006-08-31
Riddell has already approved today's daily kubuntu CD's as knot2, so kubuntu's basically set for a knot2 release.

---

### Post by az on 2006-08-31
> **Shay Stephens said:**
> After having slept on it, there is a chance that hurd is ahead of it's time, and will only see it's time in the sun later on down the line.  

Ever since Linux was a twinkle in Linus' eye, that argument has been brought up.

Hurd is a microkernel.  Big deal.  So is Minix (Minix3 is now licenced in a more free way - perhaps that will make it a better contender?) the Mac OS kernel and I beleive so is the windows kernel (not the win 98 or milleneum, but the modern NT one).  I dunno what kind of kernel all of the BSDs are.

I think that is all irrelevant.  The important part is the communities around each project.  If Hurd is to become popular, it's because it serves a need that the other alternatives does not provide.  The technical merrits of each one is pretty much irrelevant once it reaches a certain level of functinality.

It's nice to know there are alternatives that are ready and waiting.  However, I doubt they will "take off" unless something changes in the linux community in a fundemental way.

For example, if Linus one day decides that the licencing should change or something that turns core linux developers and users off.

---

### Post by Shay Stephens on 2006-08-31
> **azz said:**
> Ever since Linux was a twinkle in Linus' eye, that argument has been brought up.

I hear ya.  I guess I am reaching to find a use for it ;-)

---

### Post by az on 2006-08-31
> **Shay Stephens said:**
> I hear ya.  I guess I am reaching to find a use for it ;-)

Use it!  Use it!  I think it's great!  I think it would be better if more people used it (it would acutally boot!)  

It's just not a competition thing in the "under the hood" category.  Those advantages/dissadvantages are of little relevance.

---

### Post by prizrak on 2006-08-31
NT is a modified microkernel. Vista is even more of a microkernel than XP was. In reality from a technical standpoint a pure microkernel or a pure monolithic kernel both suck. Each has advantages and disadvantages, I believe the best approach is mixed. Vista seems to be taking it with allowing sound to run in userland (i.e. outside of the kernel) and some other stuff too. Basically it's a good thing to leave certain things out of the kernel and run them so that if the driver crashes the kernel doesn't, also makes a driver much easier to install as there is no need to reload the kernel. Other things are better off running in the kernel for speed sake. If you ask me the way we program is outdated it's still the same now as it was in the 70's nothing really new.

---

### Post by kinematic on 2006-08-31
> **poofyhairguy said:**
> Hurd is a microkernel design with years of work. Linux came along with its simplier monolithic kernel and created the GNU operating system and Hurd never recovered.

uhmmm....yeah like development of the gnu operating system started in the early 80's and it was a complete os minus a stable,mature kernel when the linux kernel came along in 1991(or was it 1990?).
the linux "project" did not create the gnu operating system.

---

### Post by SoundMachine on 2006-09-01
> **kinematic said:**
> uhmmm....yeah like development of the gnu operating system started in the early 80's and it was a complete os minus a stable,mature kernel when the linux kernel came along in 1991(or was it 1990?).
the linux "project" did not create the gnu operating system.

Well, you can't really call a set of programs without a kernel an OS, can you?

Therefore you could say that the Linux kernel did indeed create the GNU OS as it was not really and OS before then.

---

### Post by Rhapsody on 2006-09-01
> **SoundMachine said:**
> Well, you can't really call a set of programs without a kernel an OS, can you?

Therefore you could say that the Linux kernel did indeed create the GNU OS as it was not really and OS before then.
Yes, but Richard Stallman still insists that Linux should really be called GNU/Linux or 'A Linux-based GNU system' and that Hurd will eventually be at the heart of a 'proper' GNU OS. My initial thought is "Talk is cheap, show me the code", but who knows? It may work out. Some day.

---

### Post by SoundMachine on 2006-09-01
> **Rhapsody said:**
> Yes, but Richard Stallman still insists that Linux should really be called GNU/Linux or 'A Linux-based GNU system' and that Hurd will eventually be at the heart of a 'proper' GNU OS. My initial thought is "Talk is cheap, show me the code", but who knows? It may work out. Some day.

Richard Stallman has a serious God-complex he'll have to get rid of before admitting any problems with any of his ideas. 

The Hurd is the future, the very, very, VERY distant future. :D

Truth is, i'd love to see it become a serious competitor but the reason it never will is the one i stated above.

To realize how everything works with RMS, let me use a quote from him.

> We heard about Linux after its release. At that time, the question facing us was, ``Should we cancel the Hurd project and use Linux instead?'' 
 We heard that Linux was not at all portable (this may not be true today, but that's what we heard then). And we heard that Linux was architecturally on a par with the Unix kernel; our work was leading to something much more powerful. 
 Given the years of work we had already put into the Hurd, we decided to finish it rather than throw them away.

The years of work he is referring to is dreaming about one day maybe getting started, the truth is that in January '91 the work hadn't even really started yet as the following quote shows:

> CMU has available under the same terms as Mach a single-server partial Unix emulator named Poe; it is rather slow and provides minimal functionality. We would probably begin by extending Poe to provide full functionality. Later we hope to have a modular emulator divided into multiple processes.

So basically, the Hurd is just RMS clinging to the hope that one day he'll have an OS that he can call his very own and be in full control over.

---

### Post by Iandefor on 2006-09-01
Well, the Hurd certainly sounds nice. Its modular design should make it easy to maintain, although I've heard of performance hits from moving data between daemons.

It just seems irrelevant now, since the Linux kernel has gained a lot of traction in the marketplace already.

Just my two cents :).

---

### Post by Brunellus on 2006-09-01
in fairness to rms (peace be upon Him), the Linux kernel is impossible without the GNU tools used to build it.

---

### Post by SoundMachine on 2006-09-01
> **Brunellus said:**
> in fairness to rms (peace be upon Him), the Linux kernel is impossible without the GNU tools used to build it.

And the GNU OS is no OS without Linux, but this discussion was about the Hurd. ;)

I find it hilarious that you used PBUH after his name though. :D

---

### Post by ago on 2006-09-01
> **Brunellus said:**
> in fairness to rms (peace be upon Him), the Linux kernel is impossible without the GNU tools used to build it.


It is like saying that if I build a scolpture half the merit is of the hammer... And a particular hammer as opposed to hammers in general...

---

### Post by Brunellus on 2006-09-01
> **ago said:**
> It is like saying that if I build a scolpture half the merit is of the hammer... And a particular hammer as opposed to hammers in general...
No, it's like saying that one is not possible without the other, or to put it in your analogy, one cannot scuplt stone without hammers.

say what you will about rms--and let me be clear about this, I do NOT necessarily agree with him on all points at all times-- The GNU project was and remains indispensible to the Linux kernel.  Even if you don't want to be pedantic and insist that all Linux-kerneled OSes be called GNU/Linux, you have to appreciate that.

---

### Post by ago on 2006-09-01
> **Brunellus said:**
> No, it's like saying that one is not possible without the other, or to put it in your analogy, one cannot scuplt stone without hammers.

Not "hammers", plural, but "that hammer", singular... GNU did not invent the hammer, it just made a hammer, singular... And for that they experct 50% of the credits for any scolpure built with it... I do not seem to recall that the person that made Michelangelo's hammer co-signed the David...

The only thing I credit them for, is the "GNU" part (i.e. GPL), that one is their baby and was a major feat and I will agree that all (F)OSS projects are its children, as for the "tool" part I am really grateful but they cannot claim any credit on works created using those tools.

---

### Post by .t. on 2006-09-01
The HURD is a great idea, indeed, and I would like to use it. However, as with Windows vs Linux, we have a problem with drivers. Personally, I never have with Linux, but I know some people have, and I am sure that I would with the HURD. This is my reluctance.

---

### Post by SoundMachine on 2006-09-01
> **.t. said:**
> The HURD is a great idea, indeed, and I would like to use it. However, as with Windows vs Linux, we have a problem with drivers. Personally, I never have with Linux, but I know some people have, and I am sure that I would with the HURD. This is my reluctance.

I doubt you'd find ANYONE who won't have a driver problem with hurd.

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> Not "hammers", plural, but "that hammer", singular... GNU did not invent the hammer, it just made a hammer, singular... And for that they experct 50% of the credits for any scolpure built with it... I do not seem to recall that the person that made Michelangelo's hammer co-signed the David...

The only thing I credit them for, is the "GNU" part (i.e. GPL), that one is their baby and was a major feat and I will agree that all (F)OSS projects are its children, as for the "tool" part I am really grateful but they cannot claim any credit on works created using those tools.

Jeebus man, do you EVER take the time to find out what you are talking about before you open your mouth?

[www.gnu.org](www.gnu.org) - educate yourself.

[http://directory.fsf.org/GNU/](http://directory.fsf.org/GNU/) - these packages are GNU packages, developed in the GNU project, sponsored by the FSF, se any packages there you use?

---

### Post by Brunellus on 2006-09-01
> **SoundMachine said:**
> I doubt you'd find ANYONE who won't have a driver problem with hurd.
the HURD is the kernel of the future....and always will be.

---

### Post by Iandefor on 2006-09-01
> **Brunellus said:**
> No, it's like saying that one is not possible without the other, or to put it in your analogy, one cannot scuplt stone without hammers.

say what you will about rms--and let me be clear about this, I do NOT necessarily agree with him on all points at all times-- The GNU project was and remains indispensible to the Linux kernel.  Even if you don't want to be pedantic and insist that all Linux-kerneled OSes be called GNU/Linux, you have to appreciate that. Is the Linux kernel uncompilable by anything other than gcc or something? Because that's really the only thing I could think of that would merit calling GNU indispensable to the Linux kernel.

---

### Post by .t. on 2006-09-01
Yes. You cannot compile Linux except using the GCC. Just try. I dare ya.

---

### Post by detyabozhye on 2006-09-01
> **Brunellus said:**
> the HURD is the kernel of the future....and always will be.

haha! good one. :D

---

### Post by detyabozhye on 2006-09-01
> **.t. said:**
> Yes. You cannot compile Linux except using the GCC. Just try. I dare ya.

With some modifications to the code, I bet you can.

---

### Post by SoundMachine on 2006-09-01
> **Iandefor said:**
> Is the Linux kernel uncompilable by anything other than gcc or something? Because that's really the only thing I could think of that would merit calling GNU indispensable to the Linux kernel.

Try it.

Try it with as many compilers as you want to.

There is no substitute for experience. ;)

GNU is not really indispensable to the Linux kernel, given a couple of years just working on getting all of it to another platform it would run perfectly.

OTOH, FreeBSD runs numerous GNU software just to provide functionality, Solaris is extremely boring and fairly useless without it too even though Sun people claim it's the spawn of the devil invading their territory.

GNU is a big project.

---

### Post by prizrak on 2006-09-01
I might be asking a stupid question but why would the kernel have to be compiled with GCC? As I understand it, the kernel is written in pure C so any C compiler should be able to compile it given the correct libraries. 

GNU is hardly necessary for Linux (the kernel) to function, look at embedded devices that run a highly customized Linux version I bet they don't have much (if any GNU) stuff on them yet work just fine. 

The point is that while Torvalds did use GNU stuff, it could have happened w/o GNU just fine. This kind of argument has been beaten to death though about GNU, MS, Apple, Linux and so on and so forth.

---

### Post by SoundMachine on 2006-09-01
> **prizrak said:**
> I might be asking a stupid question but why would the kernel have to be compiled with GCC? As I understand it, the kernel is written in pure C so any C compiler should be able to compile it given the correct libraries. 

GNU is hardly necessary for Linux (the kernel) to function, look at embedded devices that run a highly customized Linux version I bet they don't have much (if any GNU) stuff on them yet work just fine. 

The point is that while Torvalds did use GNU stuff, it could have happened w/o GNU just fine. This kind of argument has been beaten to death though about GNU, MS, Apple, Linux and so on and so forth.


Try it.

And btw, Embedded devices have used the GNU compiler to compile it.

And no, not really, there were no other projects that desperately needed a kernel with the size of the FSF's GNU project around at the time, chances are, if they would have chosen another kernel, Linux would be where the Hurd is today.

But RMS is a lazy bastard who has more dreams than ambition and Linus is the complete opposite, so they mix very well.

It's like that margerita you only have once and you never have one that is quite as perfectly mixed again. ;)

For fun, just because no one else will really bother to take the time, i'll use another compiler to try to build the code with and keep going after fatal which happens before the actual compiling begins on ANY compiler i have tried it on before.

---

### Post by .t. on 2006-09-01
I dunno. I am not a kernel hacker. However; I have tried to compile Linux 0.0.1 with GCC 4, and it did not go smoothly. This was because the GNU assembler functioned differently from others, and even later versions. The Linux makefiles would be in need of re-writing if a different toolchain was used.

---

### Post by SoundMachine on 2006-09-01
> **.t. said:**
> I dunno. I am not a kernel hacker. However; I have tried to compile Linux 0.0.1 with GCC 4, and it did not go smoothly. This was because the GNU assembler functioned differently from others, and even later versions. The Linux makefiles would be in need of re-writing if a different toolchain was used.

Yes, now look at the size of the codebase, it would take years even for the entire team of devs to get a stable port out that can be easily compiled on another compiler and even then, only on that compiler and the lock in starts all over again.

---

### Post by Iandefor on 2006-09-01
It seems I stand corrected.

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> Jeebus man, do you EVER take the time to find out what you are talking about before you open your mouth?

My friend, I am educated, and so happens that about half of the community shares my line of thought, including thousands and thousands of extremely smart and educated people. I like to call it "Linux". You are free of thinking otherwise, but if you think that the other half of the word that has a different opinion is non-educated you just show how limited you are...

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> Try it.

Today, because millions of lines have been written taregeting gcc. But the kernel could have been developed with any other compiler.

---

### Post by SoundMachine on 2006-09-01
> **Iandefor said:**
> It seems I stand corrected.

Not entirely, it's perfectly doable and you know the hardasses around FLOSS, someone will do just that one day. ;)

---

### Post by jpkotta on 2006-09-01
GNU is important, but I think the GPL is the most important thing.  That was Stallman's greatest contribution.  Without it, Linux kernel, GNU, and lots of other software would have been grabbed by (and probably ruined by) greedy companies.

---

### Post by ago on 2006-09-01
> **jpkotta said:**
> GNU is important, but I think the GPL is the most important thing.  That was Stallman's greatest contribution.  Without it, Linux kernel, GNU, and lots of other software would have been grabbed by (and probably ruined by) greedy companies.

Exactly... All the enphasys on the tools is way over the top, but nobody can object on the GPL contribution...

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> My friend, I am educated, and so happens that about half of the community shares my line of thought, including thousands and thousands of extremely smart and educated people. I like to call it "Linux". You are free of thinking otherwise, but if you think that the other half of the word that has a different opinion is non-educated you just show how limited you are...

I love how you just skipped past being proven wrong and went into the "linus-gnu/linux" discussion.

If you had actually taken the time to read my responses you would have seen that i have flamed NO ONE as much as RMS in this thread, and it's Linux, Linus is right, GNU/Linux is just silly.

But THAT is a name, you marginalizing GNU into something that any sane knowlegable person can CLEARLY SEE it is not by just looking at the links i provided is a whole nother issue.

It's not opinion, it's you spewing BS and me correcting you in pretty much every exchange we ever have.

Why not stop playing pretend for just ONCE and actually learn something so you can speak from a standpoint of knowledge and not from a standpoint of ignorance? Is it because it would take an admittance of being wrong?

You said that the ONLY real contribution of GNU was the GPL, i showed you a list of GNU developed apps, you could have excused yourself and saved face but instead you continue with this crap?

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> you marginalizing GNU into something that any sane knowlegable person can CLEARLY SEE it is not by just looking at the links i provided is a whole nother issue.

No I did not, do not invent things I did not say. I clearly stated (twice) that their contribution for GPL was a major feat. And I clearly stated that we are extremely thankful for their tools. I simply said that they cannot claim to co-sign work done with those tools. Which is another way of saying that I think it is inappropriate to call it gnu-linux just because it was compiled with their gcc and used their tools.

read the posts before replaying and insulting people.

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> Exactly... All the enphasys on the tools is way over the top, but nobody can object on the GPL contribution...

Jeesus christ man, don't try to freeride his post to get yourself out of your mess, you said "The only thing I credit them for, is the "GNU" part (i.e. GPL), that one is their baby and was a major feat and I will agree that all (F)OSS projects are its children, as for the "tool" part I am really grateful but they cannot claim any credit on works created using those tools."

So i guess Gnome, Gimp, Freetype, these are just programs that you don't find important?

Well considering this is the forum of a Gnome based distro, i find this very strange.

I think you made the comment out of ignorance.

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> it's you spewing BS and me correcting you in pretty much every exchange we ever have.

I really think you need a new pair of glasses...

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> Jeesus christ man, don't try to freeride his post to get yourself out of your mess

My friend I am not freeriding anybody I wrote well before:

"The only thing I credit them for, is the "GNU" part (i.e. GPL), that one is their baby and was a major feat and I will agree that all (F)OSS projects are its children, as for the "tool" part I am really grateful but they cannot claim any credit on works created using those tools."

If you do can't read it is your problem

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> Exactly... All the enphasys on the tools is way over the top, but nobody can object on the GPL contribution...
> **ago said:**
> No I did not, do not invent things I did not say. I clearly stated (twice) that their contribution for GPL was a major feat. And I clearly stated that we are extremely thankful for their tools. I simply said that they cannot claim to co-sign work done with those tools. Which is another way of saying that I think it is inappropriate to call it gnu-linux just because it was compiled with their gcc and used their tools.

read the posts before replaying and insulting people.

"The only thing I credit them for, is the "GNU" part (i.e. GPL)"

Is what you wrote, so Gnome and GIMP are not things you credit them for, obviously, even though both are part of the GNU Project.

It's obvious to everyone by now that you didn't have a clue what the GNU project is and which programs they have produced.

And quite frankly, you trying to wiggle your way out of this makes me want to puke, so i'll just leave you to endlessly rant on on more things you don't understand.

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> My friend I am not freeriding anybody I wrote well before:

"The only thing I credit them for, is the "GNU" part (i.e. GPL), that one is their baby and was a major feat and I will agree that all (F)OSS projects are its children, as for the "tool" part I am really grateful but they cannot claim any credit on works created using those tools."

If you do can't read it is your problem

You STILL don't understand that things like Gnome and the Gimp are part of the GNU project, not just licenced under GPL?

Because what you are saying is that you are grateful for the Licence and what it has enabled others to do but you don't want to give them any credits for ALL the programs they have produced. 

Either it is because you don't consider Gnome and Gimp to be important or it is because you didn't know, which is it?

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> Is what you wrote, so Gnome and GIMP are not things you credit them for, obviously, even though both are part of the GNU Project.

Obviously you cannot understand what you read. I said that I cannot credit them for DERIVED work (DERIVED work = work done using their tools). But I added that I am thankful for the tools themselves (i.e. I credit them for tools they have created not for derived work)

"**for the "tool" part I am really grateful** but they cannot claim any credit on works created using those tools."

Boy you really need glasses...

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> You STILL don't understand that things like Gnome and the Gimp are part of the GNU project, not just licenced under GPL?

Did I ever claim otherwise? Learn to read!

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> Obviously you cannot understand what you read. I said that I cannot credit them for DERIVED work (DERIVED work = work done using their tools). But I added that I am thankful for the tools themselves (i.e. I credit them for tools they have created not for derived work)

"**for the "tool" part I am really grateful** but they cannot claim any credit on works created using those tools."

Boy you really need glasses...

Let me explain this as simple as i can, these are part of the GNU Project, these are GNU applications, not because they were made using their tools but because they are part of the GNU Project.

Do you get it, it's not about someone else using their developed tools to produce something, these are GNU Project applications.

---

### Post by SoundMachine on 2006-09-01
> **ago said:**
> Did I ever claim otherwise? Learn to read!


I give up. You stated that you are only grateful for the GPL part and the tools, not for the applications built in the GNU Project and you keep being thickheaded enough to see my point.

I'll ignore your sorry *** from now on. bye.

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> Let me explain this as simple as i can, these are part of the GNU Project, these are GNU applications, not because they were made using their tools but because they are part of the GNU Project.

Did I ever claim otherwise? Learn to read!

---

### Post by ago on 2006-09-01
> **SoundMachine said:**
> IYou stated that you are only grateful for the GPL part and the tools, not for the applications built in the GNU Project

I did not mention it because, we where talking about the Linux kernel. And the reletiontip between the linux kernel and GNU has to do with 2 things: GPL and tools. It has absolutely nothing to do with gimp. So gimp in that contest was completely OT. 

If I had mentioned ANYWHERE that I did not credit them for the gimp & co, you would be right. But I didn't. And you cannot infer things from sentences people have not said (particularly if what they did not mention was OT).

---

### Post by .t. on 2006-09-01
Please don't troll. Let it stop here, be mature; or this thread is in the gaol.

---

### Post by detyabozhye on 2006-09-01
> **SoundMachine said:**
> Jeesus christ man, don't try to freeride his post to get yourself out of your mess, you said "The only thing I credit them for, is the "GNU" part (i.e. GPL), that one is their baby and was a major feat and I will agree that all (F)OSS projects are its children, as for the "tool" part I am really grateful but they cannot claim any credit on works created using those tools."

So i guess Gnome, Gimp, Freetype, these are just programs that you don't find important?

Well considering this is the forum of a Gnome based distro, i find this very strange.

I think you made the comment out of ignorance.

Easy on using that name as a curse word. Some people, including me, are offended by that.

---

### Post by SoundMachine on 2006-09-01
> **detyabozhye said:**
> Easy on using that name as a curse word. Some people, including me, are offended by that.

I did not use it as a curse word, if i had i would have apologized to the one that i had offenced by using it as a curse word against, your religion is your personal belief, keep it that way and you'll live a much happier life.

---

### Post by RAV TUX on 2006-09-01
Two things:

1. this thread will be moved to the other OS forum

2. lets please keep the bickering down, PM each other instead of posting here.

---

### Post by detyabozhye on 2006-09-01
> **SoundMachine said:**
> I did not use it as a curse word, if i had i would have apologized to the one that i had offenced by using it as a curse word against, your religion is your personal belief, keep it that way and you'll live a much happier life.

Sorry, I can't, I'm an Evangilical Christian Baptist, you know, one of those guys who can't keep quiet about it without becoming unhappy. :D But really, we should _try_ to keep the forum clean of anything inflametory, including that. That's why I don't say anything the muslim, budhist, shinto, whatever faith.

Some cuss words would make sense instead of the name in that sentance, like d*** for example. So you sort of did use it that way. And the forum terms of use or whatever don't allow that, far as I remember.

I'm not mad at you or anything, but I would really like to keep this forum clean and this thread unlocked.

---

### Post by SoundMachine on 2006-09-01
> **detyabozhye said:**
> Sorry, I can't, I'm an Evangilical Christian Baptist, you know, one of those guys who can't keep quiet about it without becoming unhappy. :D But really, we should _try_ to keep the forum clean of anything inflametory, including that. That's why I don't say anything the muslim, budhist, shinto, whatever faith.

Some cuss words would make sense instead of the name in that sentance, like d*** for example. So you sort of did use it that way. And the forum terms of use or whatever don't allow that, far as I remember.

I'm not mad at you or anything, but I would really like to keep this forum clean and this thread unlocked.


Well holy Jesus, Holy Spirit, God Moses and Mohammed.

Since when did you get to decide which words or names i can or cannot use on this forum?

---

### Post by az on 2006-09-01
Actually, I think this thread needs to be split.

Anyway.


1.  Yes, you can compile linux on another compiler.  ICC is the intel C Compiler which was developed by Intel to run some funky features in their duo-core processors before GCC became able to do it.  I am not an expert on the matter, I just know some benchmarks were done comparing the linux kernel compiled with GCC and ICC.


2. There are plenty of GNU OSes that run a differnt kernel than linux.  There are a few Debian ports to BSD, for example.  I beleive that the Solaris port of Ubuntu (Nexenta) is a GNU system.

GNU is the toolchain that makes up the foundation of the OS.  The GPL is a fundemantal part of the GNU OS and its' community.


So there!

---

### Post by SoundMachine on 2006-09-01
> **azz said:**
> Actually, I think this thread needs to be split.

Anyway.


1.  Yes, you can compile linux on another compiler.  ICC is the intel C Compiler which was developed by Intel to run some funky features in their duo-core processors before GCC became able to do it.  I am not an expert on the matter, I just know some benchmarks were done comparing the linux kernel compiled with GCC and ICC.

This has already been covered in this thread, even if the devs wanted to port it to another compiler it owuld take years.




> 2. There are plenty of GNU OSes that run a differnt kernel than linux.  There are a few Debian ports to BSD, for example.  I beleive that the Solaris port of Ubuntu (Nexenta) is a GNU system.

GNU is the toolchain that makes up the foundation of the OS.  The GPL is a fundemantal part of the GNU OS and its' community.


So there!

Have you ever tried any of the ports, it's like a frankenstein with a leg for a brain. it's not even in testing.


GNU is a lot more than that, GNU is also GIMP and GNOME and FreeType.

To simplify things for Ubuntuers, withouth GNU, no GUI, without Linux, no kernel.

A mod hit it fight a long time ago, i don't even know why we're still discussing it.

---

### Post by deanlinkous on 2006-09-02
GNU is the operating system. It is the stuff YOU use to operate the system afterall. It needs a kernel to operate and it can use a different kernel. Linux is one kernel that can be used. Does anyone use linux without GNU? Because of all that I would say that GNU has a place in the name so therfore we should call it GNU+linux or GNU/linux. RMS seems to be moving toward GNU+Linux now since it seems to convey the meaning a bit more. RMS has not said that linux is less of anything than hurd. If someone wanted to (try) and remove the GNU from linux then all is well and good and it could just be called linux. Still it is covered under the GPL so it would still be possible for someone to take it and add it back together. :)

Please remember that the FSF/RMS/GNU/GPL did not reach out and grab linux and use it but the other way around. 

And RMS is not over the hurd development.

Could the fuss over the GPLv3 be the thing that drives developers (that want v3) away from linux and to the hurd?

Now back to the hurd...

The hurd is not technically a microkernel or technically even a kernel. The hurd is a 'service' layer above a microkernel that would provide most services that a kernel normally provides. By modularizing it and keeping it abstracted it provides some amazing opportunity and features. ex: You could implement your own file system easily if you wish. 

Originally it started out building on the mach 'micro' kernel and way down the road it was realized that mach isn't quite as micro as it should be. A lot of the mach overhead was stuff that was wanted on the hurd level. Why this wasn't realized earlier...maybe the mach was the best we had at the time? So then the L4 kernel was considered and planned and.....dropped. We seen the coyotos and I think that has been decided on for the next run. Yet I do think they are currently still building on the mach kernel.  I personally think we can keep wishing for the perfect kernel or we can take mach and tweak it to do what we want. The mach was/is in development by various projects and some seem to have rung some performance out of it.

Probably the best mirror is this one...
[http://ftp.gnuab.org/pub/debian-cd/](http://ftp.gnuab.org/pub/debian-cd/)

As you can see a couple people still seem to bang on it...
[http://lists.gnu.org/archive/html/commit-hurd/](http://lists.gnu.org/archive/html/commit-hurd/)
Anyone going for a test drive? :)

RMS has said it isn't really usable at this point and is glad that another kernel is free and usable and that is what everyone should use. Good old linux...or should I say GNU+Linux!

---

### Post by _asc_ on 2006-09-04
Regarding the statement that HURD is the kernel of the future and it's time just hasn't come yet: 
Wouldn't HURD's architecture with its hurd of deamons be perfect for multicore CPU's?

---

### Post by 3rdalbum on 2006-09-04
Your typical Linux distro is seperated into many many different tasks anyway, so they already can run in different cores. Having the more basic servers as different tasks probably wouldn't give much of a speed increase really. Plus, the microkernel design still yields less performance than Linux's monolithic design.

---

### Post by deanlinkous on 2006-09-04
conjecture either way... :D

---

### Post by detyabozhye on 2006-09-04
Why don't we just make a "hybrid" kernel and get it over with. ;) (Y'all know Linus' opinion on that)

---

### Post by cptnapalm on 2006-09-16
I'm more than a little puzzled as to why FSF does not abanddon the HURD kernel.  I mean, they have been trying to get it working for what?  Twenty years?  If you read the mailing list when Linus first announced that he was working on a little for fun project, there were swipes taken at how much longer before the HURD kernel was done.  That was fifteen years ago.

What really baffles me is why the micro-kernel design is still touted as being easier to do this that and the other with, seeing as how absurdly difficult it seems to be to get one working on a sizable system.

I could see a mini-kernel design... larger core with loadable kernel modules... hey, wait a sec... :-\"

---

### Post by Rhapsody on 2006-09-16
> **cptnapalm said:**
> I'm more than a little puzzled as to why FSF does not abanddon the HURD kernel.  I mean, they have been trying to get it working for what?  Twenty years?  If you read the mailing list when Linus first announced that he was working on a little for fun project, there were swipes taken at how much longer before the HURD kernel was done.  That was fifteen years ago.
Development certainly has been slow.

Development on GNU Hurd was started in 1990. Today, the most recent stable release is 0.2.

Development on the Linux kernel was started in 1991. Today, the most recent stable version is 2.6.17.13.

You can certainly see a difference in activity.

---

### Post by detyabozhye on 2006-09-16
What's so great about micro-kernels anyway. They usually have worse performance than monolithic kernels and are harder to develop and maintain. Even Windows and Mac OS X don't use pure micro-kernels, their kernels implement some monolithic ideas, AFAIK.

---

### Post by 3rdalbum on 2006-09-17
> **detyabozhye said:**
> What's so great about micro-kernels anyway. They usually have worse performance than monolithic kernels and are harder to develop and maintain. Even Windows and Mac OS X don't use pure micro-kernels, their kernels implement some monolithic ideas, AFAIK.

Weren't they designed to give easy abstractions from hardware, among other things? The HURD isn't a kernel in itself, it's a system of servers sitting on top of a microkernel, so I've no idea why it's taking so long :-)

Worse performance? To my mind, definately; although there are still people arguing against that.

Micro-kernels promise greater stability than monolithic kernels, as drivers and other services run in user-space. Also, with micro-kernels, they are probably easier to maintain; most of the development work on the Linux kernel is on things that sit *above* a micro-kernel.

---

### Post by detyabozhye on 2006-09-17
> **3rdalbum said:**
> Micro-kernels promise greater stability than monolithic kernels, as drivers and other services run in user-space. Also, with micro-kernels, they are probably easier to maintain; most of the development work on the Linux kernel is on things that sit *above* a micro-kernel.

Possibly, but then again the Windows kernel is a micro-kernel and it isn't any more stable than the Linux kernel. I guess it just depends on how it's made.

---

### Post by Rhapsody on 2006-09-17
> **detyabozhye said:**
> Possibly, but then again the Windows kernel is a micro-kernel and it isn't any more stable than the Linux kernel. I guess it just depends on how it's made.
I wouldn't go so far as to call the Windows NT kernel a microkernel. The hybrid kernel they use is an attempt to have the advantages of both a monolithic kernel and microkernel, but has just been dismissed by some as advertising. Interestingly, Microsoft themselves have been known to call it a 'macrokernel', which would be pretty much as far from a microkernel as you could get.

---

### Post by detyabozhye on 2006-09-17
I know it isn't a pure micro-kernel, but AFAIK (maybe I'm wrong) the main design was a micro-kernel into which they hacked monolithic kernel ideas, dunno.

---

### Post by Rhapsody on 2006-09-17
> **detyabozhye said:**
> I know it isn't a pure micro-kernel, but AFAIK (maybe I'm wrong) the main design was a micro-kernel into which they hacked monolithic kernel ideas, dunno.
It's difficult to tell exactly what they did, given the closed source development model. I'd think it was the other way around though. Get a monolithic kernel, shoehorn some servers into it, and call it a new type of kernel.

---

### Post by Brunellus on 2006-09-17
> **Rhapsody said:**
> I wouldn't go so far as to call the Windows NT kernel a microkernel. The hybrid kernel they use is an attempt to have the advantages of both a monolithic kernel and microkernel, but has just been dismissed by some as advertising. Interestingly, Microsoft themselves have been known to call it a 'macrokernel', which would be pretty much as far from a microkernel as you could get.
well, the Windows NT kernel's internals are covered by a nondisclosure agreement, right?  so who's to say what kind of kernel it really is?

---

### Post by 3rdalbum on 2006-09-18
One thing I think is weird is that whenever you insert or remove a kernel module on Windows, the desktop icons flicker. It disturbs me to think that maybe the kernel is the bit that controls the drawing of the desktop!

I've always thought that the reason why Linux was more stable than the Windows kernel was because driver developers know exactly what's inside the Linux kernel, and can debug "from both sides". Whereas, with the Windows kernel, its exact operation is a mystery to driver developers.

---

### Post by RAV TUX on 2007-03-09
> **panickedthumb said:**
> I've had it up and running once. It's a pain. Really not worth the trouble honestly. I hope it gets better, but the Linux, Solaris, and BSD kernels are already enough to suffice for me.interesting

---

### Post by cbreaker on 2007-11-28
I thought I might pipe in here a little bit:

- As Free/Open Source software drivers continue to become more common, Hurd will benefit.   Linux isn't a bad thing for GNU Hurd, it's a good thing.    It will make it MUCH easier for Hurd to mature into a viable operating kernel once it gets there.

- Micro Kernels CAN be ported to embedded hardware, and quite easily.  iPhone, or iPod Touch anyone?   MacOS X uses a Micro Kernel, and it works just fine on embedded devices.

- Just because Linus says that he doesn't like Micro Kernels, doesn't mean they are bad.   There's some very significant advantages to a Micro Kernel.    For one, it's much, much more modular.   Consider the Windows NT kernel.   It's a Micro Kernel, and look at that.   You don't need to replace it every time you update a driver, and you don't need new updated drivers every time the kernel is updated.

I believe in Micro Kernels.   I think Linux is a great feat of engineering, and it's a very good kernel, but I want something better.   Maybe Hurd will be it.

---

### Post by cbreaker on 2007-11-28
> **3rdalbum said:**
> One thing I think is weird is that whenever you insert or remove a kernel module on Windows, the desktop icons flicker. 

Don't be a Linux shill.  You're not doing anyone a favor.  That happens because Explorer is asked to redraw the icons for certain events, ensuring that the desktop list of icons is accurate.

> **3rdalbum said:**
> I've always thought that the reason why Linux was more stable than the Windows kernel was because driver developers know exactly what's inside the Linux kernel, and can debug "from both sides". Whereas, with the Windows kernel, its exact operation is a mystery to driver developers.

Not exactly.   Windows uses a Micro Kernel.   The interfaces to the kernel with each Windows release is more or less static.   Driver developers use these API's to make system calls and interface with the system.   Driver developers for Windows don't need to know the source code for the Kernel to write a proper driver. 

Linux does indeed benefit from being open source, and driver developers can utilize that advantage to make a stable driver.   It doesn't automatically make Linux more stable.    Lots of things contribute to stability.

---

### Post by dsiembab on 2008-05-16
This is a very interesting thread.

---

### Post by lakersforce on 2008-11-16
If anyone here has ever managed to get the mach up and run? I have run into some problems when booting.

This is my harddisk controllers:

> 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)


I've made a partition of about 2 gigs. Under linux the device is /dev/sda4.

When I start it at grub with
```
grub>kernel (hd0,3)/boot/gnumach.gz root=device:sd0s4 -s
(...more modules loaded...)
boot

```

..I am told by the kernel that no such device (root=device:sd0s4) exists.

The [GNU/Hurd Hardware Compability Guide]("http://www.nongnu.org/thug/gnumach_hardware.html") does not mention any intel controllers (but yet I find it hard to believe that no such support exists). I was wondering if anyone can (de)confirm this?

(or just more generally speaking; help me out!!)

---

### Post by DeadSuperHero on 2008-11-17
My biggest beef with HURD right now is the confusing direction they are taking. 

They've got the option of going with L4, coding a variation of Coyotos, or doing a new one called Viengoos.

I really want to love the HURD, but it's got a ways to go. However, it will be interesting to see how applicable taking packages from, say gNewSense and porting them to HURD will be.

I'm currently doing HURD experiments of my own on my personal project, called Xoo. (eXtendible Operating Organism), so you guys can read up on some of my own progress and designs for the user side of a GNU/HURD derivative. ([http://projectxoo.blogspot.com/](http://projectxoo.blogspot.com/))

I'm most interested in seeing a GPL v3 Operating System that fully makes use of only Free Software. One of these days...

---

### Post by detyabozhye on 2008-11-18
I've heard (and believe it to be true) that Microkernels are much slower than fat kernels when it comes to things such as filesystems. And AFAIK, there's not a lot that can be done to remedy that, since the filesystem is in userspace with a microkernel (something like that, I don't remember the details anymore), but the question I have is: would it be possible to make a microkernel perform as well as a monolithic kernel with modifications to hardware? Possibly a new CDU design?

---

### Post by jdong on 2008-11-18
Well yes the modular design of the microkernel requires a lot more IPC where before shared memory access would have sufficed. But, personally, I think correctness is more important than speed, particularly if you look at the number of nasty full-kernel-compromise vulnerabilities in Linux that come from really stupid places like Samba or NFS drivers. IMO we can take the performance penalty of microkernel design -- that's not the big issue.

---

