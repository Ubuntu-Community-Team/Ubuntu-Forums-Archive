---
title: "why is 386 still the recommended version?"
date: 2011-11-05
forum: Recurring Discussions
---

### Post by cybergalvez on 2011-11-05
With most (ok I guess all) computers capable of running 64bit why is the recommended version of Ubuntu still the 386 version?

---

### Post by lisati on 2011-11-06
There are still a handful of us who still have machines that can only use a 32-bit OS.

---

### Post by Hatsune Miku on 2011-11-06
> **lisati said:**
> There are still a handful of us who still have machines that can only use a 32-bit OS.

...The last chip without x86_64 is a Pentium 3

How can you do any Computing with that anymore O.o


Also, You should start migrating to a x64 bit OS, You get a tiny speed boost and use all your processors features... You really should use x64, like always O.o.

---

### Post by lakerssuperman on 2011-11-06
The decision was just made at UDS for 64 bit to become the recommended version as of 12.04.

---

### Post by pqwoerituytrueiwoq on 2011-11-06
my guess is a couple propriety programs/plugs-ins are still in the 32bit age (adobe air)
adobe flash just got out of it 
that or they have not updated the page yet or to so people with old systems can use the iso

@[[COLOR=#d40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635")
i am one of them but i don't use that antique anymore (2-4 mb video/512Mhz CPU)
nor do i use my less old 2.7GHz P4 system

---

### Post by critin on 2011-11-06
I have four perfectly running desktops that are all 32 bits, and I'll use them forever, or until they quit--whichever comes first.  I guess I won't be able to use any newer ubuntus from now on.  Time to venture out of my comfort zone, there are some good ones out there.

---

### Post by lisati on 2011-11-06
> **Hatsune Miku said:**
> ...The last chip without x86_64 is a Pentium 3

How can you do any Computing with that anymore O.o


Also, You should start migrating to a x64 bit OS, You get a tiny speed boost and use all your processors features... You really should use x64, like always O.o.
The 32-bit-only machine in my collection is something like 10-12 years old and has a CLI-only installation of Ubuntu 6.06 on it. All the newer machines I have are 64-bit capable. I even have a couple of 8-bit machines gathering dust somewhere, but since they're Commodore 128s, they probably don't count in this discussion. :D

---

### Post by dcstar on 2011-11-06
> **cybergalvez said:**
> With most (ok I guess all) computers capable of running 64bit why is the recommended version of Ubuntu still the 386 version?

There has been a raging debate on this exact question in a bug report for a couple of years now, do a Google search and read the many arguments for yourself.

Personally my stance is that it is an outdated and misleading "recommendation" kept alive by a few people who used the initial 64-bit releases and cannot let go of their prejudices from all those years ago.

---

### Post by 3rdalbum on 2011-11-06
> **Hatsune Miku said:**
> ...The last chip without x86_64 is a Pentium 3

There are still Atom CPUs that are capable of running Ubuntu but do not support 64-bit x86 instructions. The Z5, Z6 and (now discontinued) N2 Atoms.

i386 was recommended because Ubuntu did not have multiarch support. Now it does, and it's been shown to work pretty well, so in 12.04 the 64-bit edition will be the recommended one.

---

### Post by MartyBuntu on 2011-11-06
> **Hatsune Miku said:**
> ...The last chip without x86_64 is a Pentium 3


Wrong.
Athlons...Atoms...Most Pentium 4's

> **Hatsune Miku said:**
> 
How can you do any Computing with that anymore O.o

That would depend on your idea of "computing".

---

### Post by Hatsune Miku on 2011-11-06
To Everyone, CALM DOWN LOL! The last chip without x64 was a Pentium 3, Please unclench ur fist >.>

---

### Post by mcduck on 2011-11-06
> **Hatsune Miku said:**
> ...The last chip without x86_64 is a Pentium 3

How can you do any Computing with that anymore O.o


Also, You should start migrating to a x64 bit OS, You get a tiny speed boost and use all your processors features... You really should use x64, like always O.o.

Not true. Like other s have mentioned, most Pentium 4s, Athlon XPs, Intel Atoms and even fairly new Core & Core Duo processors are all 32-bit only. And all those are lot more recent technology than the P3 you mentioned. Atoms are even still sold and actually quite common on many types of machines, to it only make sense to default to architecture that works on everything.

...not to forget that the benefits of 64-bit computing don't even apply to most of the tasks a basic user would ever do with their computers.

---

### Post by philinux on 2011-11-06
See post #4.

Found link. [http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html](http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html)

---

### Post by haqking on 2011-11-06
Because it will work on anything (within reason these days)

X64 wont necessarily work as alot of people are using 32 bit, where as 32 bit will work if you have x64.

You can bet when it switches to x64 as default people will download it and then complain because it wont work on the system and "why did canonical make x64 the default" blah blah LOL

---

### Post by cybergalvez on 2011-11-06
Wow I guess I get it that there is still some hardware out there that does not support 64bit, but doesn't it make more sense to make 64bit the default since thats the majority of the hardware and let folks know when they should be downloading 32bit? 

I guess thats what they'll do with the next version, switch to 64bit as the recommended version, but still make 32bit avail.

---

### Post by haqking on 2011-11-06
> **cybergalvez said:**
> Wow I guess I get it that there is still some hardware out there that does not support 64bit, but doesn't it make more sense to make 64bit the default since thats the majority of the hardware and let folks know when they should be downloading 32bit? 

I guess thats what they'll do with the next version, switch to 64bit as the recommended version, but still make 32bit avail.

If people dont know now to change it to x64 when they need or want it then how will they know to change it then ;-)

you either know what you want or need or you dont

people are people

---

### Post by uRock on 2011-11-06
Moved to Recurring.

---

### Post by aysiu on 2011-11-07
Here's an idea: doesn't the user agent identify not only the web browser but also the operating system? How about if the person visiting the ubuntu.com website is using Windows 64-bit or any recent Mac OS X, she gets redirected to the 64-bit Ubuntu .iso? And if the person is visiting using Windows 32-bit or an older Mac OS X, she gets redirected to the 32-bit Ubuntu .iso?

Yes, I know you can use User Agent Switcher to change how your browser identifies, but if you're savvy enough to be playing around with user agents, you're probably savvy enough to know whether you're using a 32-bit or 64-bit capable computer, no?

Personally, I'm a fan of the 32-bit, mainly because my Ubuntu computer is a netbook (my devices are Windows laptop at work, Mac laptop at home, Ubuntu netbook at home, Android phone, and iPad).

---

### Post by ubuntu27 on 2011-11-07
> **critin said:**
> I have four perfectly running desktops that are all 32 bits, and I'll use them forever, or until they quit--whichever comes first.  I guess I won't be able to use any newer ubuntus from now on.  Time to venture out of my comfort zone, there are some good ones out there.

Hi Critin. Ubuntu will keep offering 32-bit version. It is just that beginning from next version, Ubuntu 64-bit will be offered as the first (recommended option). In another worods, when one clicks on "Download", the default iso will be 64-bit.
However, you will be able to choose 32-bit if you go to alternate download page (or "extra options").


For additional information, you can read: [Expected Changes In Ubuntu 12.04 Precise Pangolin (UDS-P In Brief)]("http://www.webupd8.org/2011/11/expected-changes-in-ubuntu-1204-precise.html")

---

### Post by kurt18947 on 2011-11-07
> **Hatsune Miku said:**
> ...The last chip without x86_64 is a Pentium 3

How can you do any Computing with that anymore O.o


Also, You should start migrating to a x64 bit OS, You get a tiny speed boost and use all your processors features... You really should use x64, like always O.o.


from Wikipedia:
**Instruction set architecture**

 Atom implements the [x86]("http://en.wikipedia.org/wiki/X86") ([IA-32]("http://en.wikipedia.org/wiki/IA-32")) instruction set; [x86-64]("http://en.wikipedia.org/wiki/X86-64")  is so far only activated for the desktop Diamondville and desktop and  mobile Pineview cores. The Atom N2xx and Z5xx series Atom models cannot  run x86-64 code.

---

### Post by 3rdalbum on 2011-11-07
> **aysiu said:**
> Here's an idea: doesn't the user agent identify not only the web browser but also the operating system? How about if the person visiting the ubuntu.com website is using Windows 64-bit or any recent Mac OS X, she gets redirected to the 64-bit Ubuntu .iso? And if the person is visiting using Windows 32-bit or an older Mac OS X, she gets redirected to the 32-bit Ubuntu .iso?

Quite a clever idea, but with one flaw: Lots of Windows users still use 32-bit Windows on 64-bit CPUs, because 64-bit Windows has a reputation of incompatibility. Probably not a deserved reputation, but that doesn't really matter.

Your idea is very similar to what Wubi does - if you've got a 64-bit CPU it will download the 64-bit ISO. Unfortunately it causes a lot of people to post to Ubuntu Forums, worrying that Wubi is downloading the wrong ISO because they didn't know their CPU could handle 64-bit :-)

---

### Post by aysiu on 2011-11-07
> **3rdalbum said:**
> Quite a clever idea, but with one flaw: Lots of Windows users still use 32-bit Windows on 64-bit CPUs, because 64-bit Windows has a reputation of incompatibility. Probably not a deserved reputation, but that doesn't really matter.

Your idea is very similar to what Wubi does - if you've got a 64-bit CPU it will download the 64-bit ISO. Unfortunately it causes a lot of people to post to Ubuntu Forums, worrying that Wubi is downloading the wrong ISO because they didn't know their CPU could handle 64-bit :-)
Point taken, but then there's nothing lost. Right now it defaults to 32-bit anyway, right?

---

### Post by doorknob60 on 2011-11-07
> **Hatsune Miku said:**
> ...The last chip without x86_64 is a Pentium 3


No. Most Pentium 4's and some of the older Intel Atom chips don't support it. I have a Pentium 4 machine that is still quite usable for simple tasks, and is only 32 bit. Also two laptops, both still usable for simple browsing, etc. (A Pentium 4-era thing, and an AMD Sempron). However, I do agree that 64 bit should be the default now.

---

### Post by haqking on 2011-11-07
Does a drop down box for choice warrant a thread really ?

You click once and choose.

If it defaulted to x64 some people couldnt install it (as demonstrated in some threads on here) where people downloaded wrong version and they didnt have the hardware.

By defaulting to 32 at least it will work on both, alot of people dont know the difference between the 2, those that do will know what to look for

---

### Post by Legendary_Bibo on 2011-11-08
It's because the multiarch support in Linux isn't quite there just yet.

I've come across several games and applications compiled only for 32 bit that won't run in a 64 bit Ubuntu. Skype, Firefox, Flash, Chrome, etc. The 32 bit builds will work for 64 bit systems.

---

### Post by v1ad on 2011-11-08
weird... all my athlon and atom chips run x64...

---

### Post by lisati on 2011-11-08
> **3rdalbum said:**
> Quite a clever idea, but with one flaw: Lots of Windows users still use 32-bit Windows on 64-bit CPUs, because 64-bit Windows has a reputation of incompatibility. Probably not a deserved reputation, but that doesn't really matter.

Your idea is very similar to what Wubi does - if you've got a 64-bit CPU it will download the 64-bit ISO. Unfortunately it causes a lot of people to post to Ubuntu Forums, worrying that Wubi is downloading the wrong ISO because they didn't know their CPU could handle 64-bit :-)

Something similar happened to me. I had my main "desktop" machine for something like 4 or 5 years before I realised that it was 64-bit capable. I only found out after playing around with some stuff I saw here on the forums.

---

