---
title: "32 or 64 bit"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by padrejeff on 2008-08-17
I am about to install 8.04 on my IBM T41 laptop. It is running  Pentium M Centrino.

How do I know if I should install the 32 bit or 64 bit CD (I have both)??

Thanks,

Jeff

---

### Post by DGortze380 on 2008-08-17
assuming your processor is actually 64bit (I'm finding mixed information on that subject) it's up to you. research each, IIRC you have to use 32-bit flash but everything else should be ok. Take a look around, as I have not run 64bit Ubuntu myself yet.

---

### Post by zzHanks on 2008-08-17
I think this computer is not capable of running the 64-bit version, but I'm not sure

---

### Post by mevets on 2008-08-17
I'd say just go with 32 bit unless you have a particular reason to go 64. Like say you have 4+ GB of ram and you want to be able to use all of it or you need all the performance you can get.

---

### Post by nicedude on 2008-08-17
32bit is the way to go, its best for program compatibility and I have ran both on my AMD laptop and could tell no difference under any normal things I do ( watching videos & surfing etc) .

---

### Post by zamadatix on 2008-08-17
im running ubuntu 64 right now it was a pain to get 32 bit firefox but you wont noticed many differences the only program i know of in the ubuntu add remove that doesnt work is one of the nes emulators (you can just use the other ones). and if you have a valid reason as said like more than 4gb ram or any of the other benefits use it otherwise not really much different.

---

### Post by carlinuxlearner on 2008-08-17
It makes a difference when doing number crunching things like encoding, rendering, and editing. And it was a breeze getting firefox (flash and all that junk) working on my install.

If all you do is browse the web, write e-mails, do a little photo editing, you won't be seeing much of a difference.

C@RL

---

### Post by zzHanks on 2008-08-17
> **carlinuxlearner said:**
> ...And it was a breeze getting firefox (flash and all that junk) working on my install.
That's the reason why I'm using my 32-bit laptop now.

How did you get it to work in the end? I tried many HowTo's, re-installed many times. The weird thing is that sometimes it worked and sometimes not.

---

### Post by padrejeff on 2008-08-17
> **carlinuxlearner said:**
> It makes a difference when doing number crunching things like encoding, rendering, and editing. And it was a breeze getting firefox (flash and all that junk) working on my install.

If all you do is browse the web, write e-mails, do a little photo editing, you won't be seeing much of a difference.

C@RL

So, 32 bit is what you are saying I ought use? I'm in the latter category with a bit of spreadsheet work, but not huge number crunching. Is there a problem getting Firefox to work in 32bit?

J

---

### Post by mevets on 2008-08-17
In 32bit its just seamless.

---

### Post by carlinuxlearner on 2008-08-17
@ padrejeff

*"Is there a problem getting Firefox to work in 32bit?"*
No, problems sometimes arise when you try to install 32bit FireFox, on a 64bit install (so you can use flash).

C@RL

---

### Post by carlinuxlearner on 2008-08-17
@ zzHanks

*"How did you get it to work in the end?"*

I found a tutorial on these forums, for installing flash on a 64bit install, followed the instructions, and it worked first try.

C@RL

(I wish I knew what thread it was, but I have no idea where I found it on here (the tutorial))

---

### Post by zzHanks on 2008-08-18
[quote=padrejeff] Is there a problem getting Firefox to work in 32bit?

J[/quote]

In my case Firefox/Flash was a nightmare in 64-bit.

So I would install the 32-bit version.

---

### Post by hyper_ch on 2008-08-18
There's no real reason to stick with 32bit anymore. Firefox runs fine. Flash runs also fine, same goes for java... all can be installed quite confortably from the repos.

---

### Post by Vivaldi Gloria on 2008-08-18
> **hyper_ch said:**
> There's no real reason to stick with 32bit anymore. Firefox runs fine. Flash runs also fine, same goes for java... all can be installed quite confortably from the repos.

+1

I was going to say the same thing. Actually for some reason flash crashes less in 64 bit hardy.

---

### Post by mikewhatever on 2008-08-18
> **hyper_ch said:**
> There's no real reason to stick with 32bit anymore. Firefox runs fine. Flash runs also fine, same goes for java... all can be installed quite confortably from the repos.

There is also no real reason not to, unless you have 4+ GB of RAM or tend to edit videos, compile from source, etc. It's true that 64 bits Ubuntu works fine and things are easy to install, but that nspluginwrapper thing turned out a heavy and resource hungry beast during my own foray into Ubuntu 64. It used over 100 MB of RAM and about 50 % CPU, and was slow.

For OP, you should check the sticky called [Advantages and Disadvantages of 64bit]("http://ubuntuforums.org/showthread.php?t=765428").

---

### Post by tuxxy on 2008-08-18
> **mikewhatever said:**
> There is also no real reason not to, unless you have 4+ GB of RAM or tend to edit videos, compile from source, etc. It's true that 64 bits Ubuntu works fine and things are easy to install, but that nspluginwrapper thing turned out a heavy and resource hungry beast during my own foray into Ubuntu 64. It used over 100 MB of RAM and about 50 % CPU, and was slow.


You dont need 4+ GB of RAM to run 64bit, it just has the capability to do so, unlike 32bit.

Yes 64bit is much faster for video editing, compiling from source, image manipulation etc however you failed to add that **any** 64bit application will outperform the equivelant 32bit app not just multimedia apps.

The nspluginwrappper may of crashed and this caused the overuse of your systems resources as this is not usual activity for it.  Whewn it does this again pull up your processes and check how many instances of nsplugin you have running.

> **hyper_ch said:**
> There's no real reason to stick with 32bit anymore. Firefox runs fine. Flash runs also fine, same goes for java... all can be installed quite confortably from the repos.

+1

---

### Post by Midahed on 2008-08-18
I've used both, but I went back to 32-bit in my latest re-install because I didn't need the additional number-crunching power of 64-bit.

Take a look at another recent thread on the same subject:-

[http://ubuntuforums.org/showthread.php?t=872437](http://ubuntuforums.org/showthread.php?t=872437)

If you have a 64-bit machine you can choose to install a 32-bit or a 64-bit OS.  You don't have that choice if your PC is 32-bit.

---

### Post by tuxxy on 2008-08-18
If you are reffering to this post of yours,

> I used to run 7.04 Feisty 64-bit as my first venture into the world of Linux, but I've just finished re-installing my system from scratch, using 8.04 Hardy 32-bit.

I bought a 64-bit motherboard and processor because.... well, because it was there to be bought. 

I didn't need the processing power of the 64-bit environment and, to be honest, I don't use the sort of apps that would benefit from 64-bit crunch-power.

Although I got most things working OK under 64-bit, it was sometimes a bit of a struggle.

I haven't noticed any speed degradation in moving back to 32-bit. Most important of all, things just work. There's no need to constantly wonder if x or y will work in a 64-bit environment.

For me, 64-bit was too 'bleeding edge'.

If you need the processing power, then go for it. But if you want a problem-free PC, I'd stick with 32-bit for the moment.

I'm still using the same 64-bit kit, so I could return to the fold in the future but, for now, I'm taking the easy way out.

Sorry if that's heresy on this section of the forum.

This point isnt valid as you are comparing a 32bit hardy install to a 64bit feisty, I am sure that your soundcard will be supported in 64bit hardy, have you tried?

Also I have installed 64bit Hardy on numerous complete new linux users systems, without a hiccup.

---

### Post by Midahed on 2008-08-18
> **tuxxy said:**
> If you are referring to this post of yours,

[http://ubuntuforums.org/showpost.php?p=5502274&postcount=12](http://ubuntuforums.org/showpost.php?p=5502274&postcount=12)

This point isn't valid as you are comparing a 32bit hardy install to a 64bit feisty, I am sure that your soundcard will be supported in 64bit hardy, have you tried?

Also I have installed 64bit Hardy on numerous complete new linux users systems, without a hiccup.
No, I haven't tried Hardy 64-bit.  Actually I referred the OP to the whole thread, not my post in particular, in order that opinions from both sides of the argument could be considered.

Yes, the point was made in that thread that my 64-bit experience was based on a 7.04 Feisty installation, and I accept that the world of 64-bit support has no doubt improved a lot since then.  However, I made the choice to go back to 32-bit because I had found the 64-bit Feisty environment 'too bleeding edge' and wanted an easy life.  More importantly, though, I just _didn't need_ the crunch power of 64-bit, so there was _no_ point in risking the possibility of any difficulties with the 64-bit environment when I knew that 32-bit would do the job I wanted just fine.

I have noticed absolutely NO performance difference for my usage of my PC under 32-bit compared to what 64-bit gave me.

_If_ the OP has no need for the power of a 64-bit system, there is a valid argument for sticking with the more commonly used 32-bit version of the OS.  Only the OP can make that decision.

---

### Post by EzEatNCSU on 2008-08-18
Well, I use 32-bit Ubuntu 8.04 cause I can't even get the liveCD for the 64-bit one to start (though I have an AMD Turion64 X2 processor that should work...) I may be doing some number crunching and stuff in the future (rising computer science major), so I'd like to know if there's a reason why I should try to figure it out and get it working, or just stay with the 32-bit (which works just fine as usual ;))

---

### Post by mikewhatever on 2008-08-18
> **tuxxy said:**
> You dont need 4+ GB of RAM to run 64bit, it just has the capability to do so, unlike 32bit.

No you don't, but since 64 bit applications use more RAM and you'd probably need nspluginwrapprer, more RAM is advisable.


> Yes 64bit is much faster for video editing, compiling from source, image manipulation etc however you failed to add that **any** 64bit application will outperform the equivelant 32bit app not just multimedia apps.

Are you sure? There are lots of myths on the subject. The performance gain is not that great, and not worth the trouble, at least in my experience. Here is a third party comparison:
[http://www.phoronix.com/scan.php?page=article&item=998&num=1](http://www.phoronix.com/scan.php?page=article&item=998&num=1)

[quuote]The nspluginwrappper may of crashed and this caused the overuse of your systems resources as this is not usual activity for it.  Whewn it does this again pull up your processes and check how many instances of nsplugin you have running.[/quote]

Well, is it supposed to crash every time you use flash? If it does what you describe, still less reason to use it.

---

### Post by Joeb454 on 2008-08-18
> **mikewhatever said:**
> No you don't, but since 64 bit applications use more RAM and you'd probably need nspluginwrapprer, more RAM is advisable.
.............................
Well, is it supposed to crash every time you use flash? If it does what you describe, still less reason to use it.

1) Not true, I've never noticed any increase in RAM usage between a 32 bit or 64 bit install on the same system.

2) nspluginwrapper works just fine for me, Flash support for Linux however, doesn't. Though it's enough for what I need to do

---

### Post by mikewhatever on 2008-08-18
> **Joeb454 said:**
> 1) Not true, I've never noticed any increase in RAM usage between a 32 bit or 64 bit install on the same system.

It is according to Wikipedia: [http://en.wikipedia.org/wiki/64_bits](http://en.wikipedia.org/wiki/64_bits)

> The main disadvantage of 64-bit architectures is that relative to 32-bit architectures the same data occupies more space in memory (due to swollen pointers and possibly other types and alignment padding). This increases the memory requirements of a given process and can have implications for efficient processor cache utilization. Maintaining a partial 32-bit model is one way to handle this and is in general reasonably effective. In fact, the highly performance-oriented z/OS operating system takes this approach currently, requiring program code to reside in any number of 32-bit address spaces while data objects can (optionally) reside in 64-bit regions.

> 2) nspluginwrapper works just fine for me, Flash support for Linux however, doesn't. Though it's enough for what I need to do

Happy for you. These kind of discussions tend to become endless, so I'm going to leave it at that. By the way, shouldn't it be moved to a recurring section?

---

### Post by skymera on 2008-08-18
ok i had the same questions.

Running an Intel processor with EMT64 technology so i can install  64BIT OS.

But hearing stories i thought not. 

But i installed DEbian a few months ago and gave 64BIT a go.

I've had no program compatibility issues, everything has run smooth. I feel it's slightly more responsive, quicker and installs, extracts programs much more efficiently.

Go for it! :):):)

---

### Post by philinux on 2008-08-18
Been running 64 bit for 4 months now. Not a single problem.

Flash. Java and firefox.

---

### Post by markbuntu on 2008-08-18
64 bit works better for me, the rt kernel just won't work on my 32 bit install so  ubuntustudio is not working very well for me on that install. I have both on separate hard drives and switch between them regularly. 

There are big differences in the performance and stability of my sound applications that run through jackd. 64 bit uses more ram but far less cpu for similar tasks.

---

