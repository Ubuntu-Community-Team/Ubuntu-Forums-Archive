---
title: "why dont they make a os that can run everything?"
date: 2008-10-17
forum: Other OS Talk
---

### Post by reinaldistic on 2008-10-17
sure linux can run linux and microsoft, but some micosoft stuff looses it's designed "beauty" and a lot of people have a need for mac type of programs so a universal translator os would be genious

better yet wine could be improved to allow the "beauty" of microsoft programs to stay and maybe add to wine the ability to understand mac programs, or maybe just another program but if linux were to play mac programs i think in a few years both microsoft and mac would go out of bussines

---

### Post by cardinals_fan on 2008-10-17
Why don't we have Santa Claus and the Tooth Fairy?

---

### Post by reinaldistic on 2008-10-17
why not? it would save money to parents

---

### Post by Bucky Ball on 2008-10-17
Why don't you focus on software and hardware manufacturers rather than the OS? They are the source of this conundrum.

---

### Post by Heinzelotto on 2008-10-17
The architectures of all those OSes you mentioned are too different of each other to make such a thing possible. For example, if you want to create a simple window (as a programmer) in OS X, Windows and X11 (Linux), the routines you have to call to accomplish this task are very different and OS-dependent.
An OS that could handle every single speciality of all those OSes would burst at the seams, let alone the speed penalty that would be caused by the more complicated and therefore harder to optimize source-code.

---

### Post by cardinals_fan on 2008-10-17
> **reinaldistic said:**
> why not? it would save money to parents
Just like the Tooth Fairy, this idea is a fantasy.  Such an operating system is so close to impossibility that the point is moot.  You CAN have virtual machines for multiple systems.  That's as close as you'll get.

---

### Post by MaxIBoy on 2008-10-17
Just like a supersonic submarine that runs on junk mail and bills, it's possible in theory but impossible in practice. 

Even putting WINE in the kernel code will make the OS more monolithic, resulting in slow startup times, increased RAM usage even when the feature isn't being used, and increased instability.

---

### Post by Gashi on 2008-10-18
well windows is easier to emulate than OS X
the reason for this is not anywhere near my knowledge of the subject 
but as far as kernel integration of WINE: 
why not build it into the kernel as an option like Xen?

---

### Post by Bucky Ball on 2008-10-18
> **Gashi said:**
> well windows is easier to emulate than OS X
the reason for this is not anywhere near my knowledge of the subject 
but as far as kernel integration of WINE: 
why not build it into the kernel as an option like Xen?

Because WINE can make some machines snail-like, even when it is not in use. :)

---

### Post by kendallben on 2008-10-18
Stupid Question

---

### Post by Shippou on 2008-10-18
This may help:

Unraveling the Utopian System that Runs All Software Imaginable Myth
[http://www.roughlydrafted.com/0506.utopian1.html](http://www.roughlydrafted.com/0506.utopian1.html)

For more up-to-date articles, follow my post here:
[http://ubuntuforums.org/showthread.php?t=864729](http://ubuntuforums.org/showthread.php?t=864729)

---

### Post by Buffalo Soldier on 2008-10-18
"he who defends everywhere, defends no where" I think it goes something like that.. Sun Tzu quote. Basically if you try to built a software/tool that caters for everyone, you will fail everyone... too much compromises.

---

### Post by Rhubarb on 2008-10-18
Wine may support OSX apps someday, see here:
[http://www.winehq.org/?issue=353](http://www.winehq.org/?issue=353)
>  **Quartz**

Ken Thomases has been point on the Quartz driver. There are several major roadblocks, the first and foremost of which being: where to start? Apple has a number of APIs to access its graphical framework. The one they promote the most, Cocoa, is an objective C interface. Alexandre has made it priority to keep Wine pure c and thus that is not a great option. There is also Carbon which is pure-C which Apple still supports. Apple has however announced that they have no plans of ever porting Carbon to 64-bit which may be a problem for Wine going forward. Once this investigation is complete Ken plans to sit down with Alexandre and get some serious design done. 

---

### Post by kaldor on 2008-10-18
What is with all of the insulting comments to the poster? Just explain why, no need to be a prick about it.

The fact is that this is just not possible. One system will never be able to run every type of file. That is like trying to insert an Xbox360 disc into a Gamecube and hoping that it will run fine... it just cannot happen.

---

### Post by Battie on 2008-10-18
> **kendallben said:**
> Stupid Question

No, not really.  What is obvious to you as a result of your set of knowledge may not be obvious to someone else with a different set.

I am often asked surprising questions about computers from people who really don't know what's going on under the hood.  I think the real test is how readily they grasp a good answer.

---

### Post by richg on 2008-10-18
Because, perfection does not exist.

Rich

---

### Post by andras artois on 2008-10-18
didn't you ever think as a kid that a ps2/xbox/gamecube game player would be the best thing ever? and you always wondered why no one had done it? that's because while you could do it it would be incredably laggy. for it to run without crashing or making mistakes it would have to be processed fully to check what system it was and then it would have to be played through the suitable architecure. in turn this would slow it down MASSIVELY considering each indivdual piece of information would have to go through this while being played or just a really really big start time.

Until people come up with a decent compromisation of it all, with a decent SDK then it will never happen. The compromisation will most liekly never happen because other people see too much money making in making there own OS with their own programs (ish) that are widely used etc.

---

### Post by MaxIBoy on 2008-10-18
> **Gashi said:**
> well windows is easier to emulate than OS X
the reason for this is not anywhere near my knowledge of the subject
Actually, OS X would probably be far easier (and it's not an emulator, it's a runtime. WINE = Wine Is Not an Emulator) 

The reason there's no Linux compatibility layer for OS X is that there aren't enough Mac-only programs for it to be worthwhile. I think that's pretty funny, but it's the truth.

---

### Post by chucky chuckaluck on 2008-10-18
'running everything' is not the goal. owning you, is.

---

### Post by Whiffle on 2008-10-18
There aren't enough resources of Pure Awesome in the entire World* to create such a fantastically amazing piece of software.









*Chuck Norris not included.  Mr. Rogers in a blood stained sweater, either.

---

### Post by sethvath on 2008-10-18
Why cant my toaster make juice, wash laundry, cook and print money?

Someobody should make that.

---

### Post by Rhubarb on 2008-10-19
> **sethvath said:**
> Why cant my toaster make juice, wash laundry, cook and print money?

Close but not quite: [http://www.embeddedarm.com/software/arm-netbsd-toaster.php](http://www.embeddedarm.com/software/arm-netbsd-toaster.php)
A little off topic I guess.

---

