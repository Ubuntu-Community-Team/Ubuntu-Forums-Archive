---
title: "32bit or 64bit"
date: 2011-11-16
forum: Recurring Discussions
---

### Post by argoz17 on 2011-11-16
So what are the disadvantages and advantages to using a 64 bit Ubuntu OS over using a 32 bit?

---

### Post by 3Miro on 2011-11-16
Just search the forum, the topic has been beaten to death. Some proprietary drivers (i.e. some printers) don't work on 64-bit and 64-bit takes a bit more RAM. On the other hand, 64-bit is a bit faster, especially if you are running CPU intensive tasks on a system with at least 4GB of RAM.

If I have at least 3GB of RAM and I don't have driver problems, then I would just go for 64-bit.

---

### Post by drawkcab on 2011-11-17
Nowadays it's tough to argue against x64 as most of the kinks have been ironed out, most notably flash performance.

---

### Post by wolfen69 on 2011-11-17
3...2...1...recurring.

Btw, I say 64bit if you have the horsepower. The next ubuntu release default is going to be 64. It is becoming the standard.

---

### Post by beew on 2011-11-17
It is not just whether the hardware supports it, how about your software, especially if you have things from outside the repos, possibly something you paid for?  e.g Matlab 32 bit doesn't run on 64 bit machines.

---

### Post by |{urse on 2011-11-17
I'd say 32bit if you dont want extra bugs, at the sacrifice of some 64bit native apps running faster/better. If you have an app that needs to be 64bit then a 64bit os makes total sense.

---

### Post by FuturePilot on 2011-11-17
> **wolfen69 said:**
> 3...2...1...recurring.

Btw, I say 64bit if you have the horsepower. The next ubuntu release default is going to be 64. It is becoming the standard.

Source?

---

### Post by tartalo on 2011-11-17
> **FuturePilot said:**
> Source?

[http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html](http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html)

---

### Post by 3Miro on 2011-11-17
> **beew said:**
> It is not just whether the hardware supports it, how about your software, especially if you have things from outside the repos, possibly something you paid for?  e.g Matlab 32 bit doesn't run on 64 bit machines.

32-bit software generally runs on a 64-bit systems. Matlab has a 64-bit version (which I would recommend due to the speed boost).

Are you sure 32-bit Matlab doesn't run on 64-bit systems. Maybe you only needed couple of 32-bit compatibility libraries from the Software Center.

---

### Post by oldos2er on 2011-11-17
Old, but most of it is still relevant: [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by BrokenKingpin on 2011-11-17
> **|{urse said:**
> I'd say 32bit if you dont want extra bugs 
???? I have been running a 64 bit Linux OS for years without any issues specific to the 64 bit version.

---

### Post by beew on 2011-11-17
> **3Miro said:**
> 32-bit software generally runs on a 64-bit systems. Matlab has a 64-bit version (which I would recommend due to the speed boost).

Are you sure 32-bit Matlab doesn't run on 64-bit systems. Maybe you only needed couple of 32-bit compatibility libraries from the Software Center.

Yes, I am sure, read it from Mathwork's FAQ. Now there may still be work around but why the anxiety (a work around may not exist) or the hassles (if the work around is very complicated)

I know that Matlab has 64 bit, but what if you already have a 32 bit liscense? I don't know if you can get a free upgrade to 64 bit, and even if you can for matlab that is not the point, the same scenario applies to other softwares and since we don't know what people use I think I should just bring this up, instead giving blanket endorsement to 64 bit just based on hardware consideration and speed,--the gain in speed can be quite marginal depending on what you do.

Of course if all you ever need is Ubuntu's offer in terms of software then I agree 64 bit is fine, this seems to be the assumption that many people go by when they recommend 64 bit. ( but then there is also the issue of hardware drivers, like someone mentioned before)

---

### Post by |{urse on 2011-11-17
> **BrokenKingpin said:**
> ???? I have been running a 64 bit Linux OS for years without any issues specific to the 64 bit version.

Awesome! There are still more bugs.

---

### Post by timsdeepsky on 2011-11-17
I have run 64 bit for a couple years and have no more problems with it then i did with 32....But i also run 2 frame grabbers each collecting 30 frames a second and multiple other programs at the same time....I have noticed 64 bit performing better with this system that has 8 gigs of ram and quad core Amd,,than it did with 32....Cheers....

---

### Post by oldos2er on 2011-11-17
> **|{urse said:**
> Awesome! There are still more bugs.

Cite?

---

### Post by wolfen69 on 2011-11-17
> **|{urse said:**
> I'd say 32bit if you dont want extra bugs

There are no "extra bugs" as you call it. If you ask me, 64bit seems to work better overall if anything. I've installed the 64bit version on many computers with no bugginess. There is a reason why canonical is making 64 the default. It's been ready for primetime for a while now.

---

### Post by |{urse on 2011-11-18
I'm only speaking from personal experience, I've experienced more headaches with 64bit than 32bit, and I was more referring to 64bit on windows. The only real 64bit problems I've ever had with linux was fedora core's adobe flash a couple years ago.

---

### Post by 3Miro on 2011-11-18
> **beew said:**
> Yes, I am sure, read it from Mathwork's FAQ. Now there may still be work around but why the anxiety (a work around may not exist) or the hassles (if the work around is very complicated)

I know that Matlab has 64 bit, but what if you already have a 32 bit liscense? I don't know if you can get a free upgrade to 64 bit, and even if you can for matlab that is not the point, the same scenario applies to other softwares and since we don't know what people use I think I should just bring this up, instead giving blanket endorsement to 64 bit just based on hardware consideration and speed,--the gain in speed can be quite marginal depending on what you do.

Of course if all you ever need is Ubuntu's offer in terms of software then I agree 64 bit is fine, this seems to be the assumption that many people go by when they recommend 64 bit. ( but then there is also the issue of hardware drivers, like someone mentioned before)

It is not a work-around, AMD64 is backwards compatible with ix86. At most, your OS would need some compatibility libraries that can be added via synaptic with the meta package ia32-libs.

---

### Post by BrokenKingpin on 2011-11-18
> **|{urse said:**
> I was more referring to 64bit on windows.
You realize this is a Linux forum right, and that the question was specific to Ubuntu?

---

### Post by wolfen69 on 2011-11-19
> **BrokenKingpin said:**
> You realize this is a Linux forum right, and that the question was specific to Ubuntu?

Oh well. I'm amazed people still question 64bit computing.

---

### Post by |{urse on 2011-11-20
Dear whoever reads this,
Yes I know this is ubuntu forums, I was commenting on 64bit computing (which was met with disagreement, which is fine) 64bit computing is great, and in my scope of experience, (which may or may not pale to your own) I have had more odd issues than with 32 bit. It was a bad choice of words to say "I'd say 32bit if you dont want extra bugs" as I truly don't know that for sure, upon rereading it's pretty egotistical for me to act as if definitely know anything for sure. mea culpa, sorry for that. in general right now on windows and years ago on linux there seemed to be (again, personal experience) more issues with 64bit compatibility with non-64bit programs and the ever-present lack of 64bit versions of this or that software or driver.  ](*,) (Thats what I think in regard to 32bit v 64bit on ubuntu forums). 

Dictated, but not read.
|{urse

---

### Post by 3rdalbum on 2011-11-23
> **argoz17 said:**
> So what are the disadvantages and advantages to using a 64 bit Ubuntu OS over using a 32 bit?

The main advantage to 64-bit Ubuntu that nobody has mentioned yet in this thread:

You can tell your Windows-using friends that you have had no compatibility problems with 64-bit Ubuntu. Their jaws will drop, figuratively speaking.

64-bit Windows is generally quite okay, but Windows people still think of it as some exotic niche for hypergeeks who can write 'rundll.exe' commands with their eyes closed and who don't actually run any programs except what they've written themselves.

You can also tell lesser computer enthusiasts that you are running 64-bit and they'll think "Wow, that must be twice as fast as my 32-bit".

---

### Post by 3rdalbum on 2011-11-23
> **|{urse said:**
> Awesome! There are still more bugs.

How so? It's the same source code, just compiled for longer numbers in some places, and native mathematical operations for 64-bit numbers (rather than the multi-hop method that's used in 32-bit mode for 64-bit numbers).

Ubuntu also compiles the 64-bit edition with more CPU optimizations, because the lowest 64-bit CPU supports a lot more optimization than the lowest 32-bit CPU. This shouldn't introduce bugs either - the optimization features are in the CPU and regularly used by application programs already.

But it's still the same source code, and the 64-bit mode of the CPU basically does the same thing in the same way as the 32-bit mode. It's not like these are totally different types of CPU, it's the same CPU on the same die. There really cannot be much of a difference between a 32-bit OS and its 64-bit counterpart.

Now, if you look at Ubuntu on x86 and Ubuntu on ARM, there you'll probably notice more bugs on ARM. But ARM is a totally different instruction set and totally different architecture.

---

### Post by philinux on 2011-11-23
> **beew said:**
> It is not just whether the hardware supports it, how about your software, especially if you have things from outside the repos, possibly something you paid for?  e.g Matlab 32 bit doesn't run on 64 bit machines.

Would the new multiarch approach solve that now?

---

