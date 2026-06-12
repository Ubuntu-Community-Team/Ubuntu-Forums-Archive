---
title: "Which version of a distro is the right one?"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by unit4216 on 2011-09-10
Sorry about the wording of the title, I don't know how else to say it.

For example, for Gentoo, there are about 10 options:

alpha
amd64
arm
hppa
ia64
ppc/ppc64
s390/s390x
sh
sparc
x86

I know this is an ubuntu forum, but some other distros have this option.  I know amd64 is basically 64-bit, but I've heard 64-bit is usually not a good idea because support is limited/stuff is made for 32-bit, etc.  I googled some of the others, but I still don't quite know what they are.  In general, could someone give me a brief description of each of these/what type of system they are for?

Thanks a bunch.

---

### Post by haqking on 2011-09-10
> **unit4216 said:**
> Sorry about the wording of the title, I don't know how else to say it.

For example, for Gentoo, there are about 10 options:

alpha
amd64
arm
hppa
ia64
ppc/ppc64
s390/s390x
sh
sparc
x86

I know this is an ubuntu forum, but some other distros have this option.  I know amd64 is basically 64-bit, but I've heard 64-bit is usually not a good idea because support is limited/stuff is made for 32-bit, etc.  I googled some of the others, but I still don't quite know what they are.  In general, could someone give me a brief description of each of these/what type of system they are for?

Thanks a bunch.

It depends on your hardware.  To be honest for the most part nowadays if you have x64 bit hardware then run x64 bit software.

There can be a few idiosyncracies but then you can have issues in 32 bit.

So why not.

What is your hardware in terms of CPU ? and how much RAM ?

The above lists refer to the architecture of your CPU.

most end users have Intel or AMD and so x86 or AMD, and amd64 usually is what you need if running x64 bit on either Intel or AMD. which also refers to Intel that is x64 bit.

---

### Post by dave01945 on 2011-09-10
i'm no expert but most of them look like different cpu architectures amd64 and x86 and your most common for home computers amd64 is the 64bit version of x86 and x86 is 32bit and those two are very standard 

i'm sure ppc/ppc64 are both powerpc archtecture and the used to be used on mac but i think all new macs now use x86 

arm is a common archtecture but not for pc's it is used on portable devices like mobile phones and tablet pc's

as for the others i don't know much about them but if your using a standard pc you will want x86 for 32bit version and amd64 for 64bit version and a few years ago 64bit wasn't very supported but now most software will run well on 64bit and if not alot of 32bit software will work on a 64bit machine and with 64bit you have the option of using more than 4GB of ram as a general rule 32bit can not use more than 4GB

---

### Post by unit4216 on 2011-09-10
> **haqking said:**
> It depends on your hardware.  To be honest for the most part nowadays if you have x64 bit hardware then run x64 bit software.

There can be a few idiosyncracies but then you can have issues in 32 bit.

So why not.

What is your hardware in terms of CPU ? and how much RAM ?

The above lists refer to the architecture of your CPU.

most end users have Intel or AMD and so x86 or AMD, and amd64 usually is what you need if running x64 bit on either Intel or AMD. which also refers to Intel that is x64 bit.

Oh, good, that was my understanding of what it was referring to, I just wanted a little bit of clarification.  FYI, I'm running an i7 with 8 gigs of DDR2.  I thought there were more problems with running 64-bit, though, a lot more problems in terms of the amount of software that is made for 32-bit that hasn't been modified to run on 64-bit.  I can't believe I didn't figure out that x86 meant x86-32, in contrast to x86-64, though.  I am too dumb.

Thanks, though, really.

---

### Post by haqking on 2011-09-10
> **unit4216 said:**
> Oh, good, that was my understanding of what it was referring to, I just wanted a little bit of clarification.  FYI, I'm running an i7 with 8 gigs of DDR2.  I thought there were more problems with running 64-bit, though, a lot more problems in terms of the amount of software that is made for 32-bit that hasn't been modified to run on 64-bit.  I can't believe I didn't figure out that x86 meant x86-32, in contrast to x86-64, though.  I am too dumb.

Thanks, though, really.


 Too dumb ? no such thing as a dumb question, only a dumb answer ;-)

I7 is x64 if you want to run x64. and also has hyperthreading.

I personally wouldnt run x86 on it, you might have a few issues with a few things.  Best bet is to figure out what software you will need and run and check first but to be honest i would go with x64 where possible

---

### Post by fabricator4 on 2011-09-10
> **unit4216 said:**
> Oh, good, that was my understanding of what it was referring to, I just wanted a little bit of clarification.  FYI, I'm running an i7 with 8 gigs of DDR2.

As you've figured you'd definitely want the amd64 version.  The only other option that I can say will definitely work would be i86.

Don't be confused with the 'amd' and 'i' prefix as they denote the instruction set, not the manufacturer of the cpu.  Intel 64 bit CPU's use the AMD instruction set.

I think it was pretty cool of Intel to embrace the AMD instruction set rather than do a Microsoft and try to force something proprietory just for the sake of it.

> 
I thought there were more problems with running 64-bit, though, a lot more problems in terms of the amount of software that is made for 32-bit that hasn't been modified to run on 64-bit.

Canonical still seem to recommend the 32 bit releases over the 64 bit, but really you'll have very few if any additional problems.  The only time I'd recommend the 32 bit version for a 64 bit machine is if it has 2Gb or less of memory.  Apart from that the performance improvements far outweigh the possible negatives.

I have an older dual core machine that can only take 2Gb or RAM so I'm using the 32 bit release, but I should probably try the 64 bit release to see if it makes a difference on this old machine.

> 
  I can't believe I didn't figure out that x86 meant x86-32, in contrast to x86-64, though.  I am too dumb.

As said, there's no dumb questions, although it reminds me of my favourite tagline from the eighties: "ASCII silly question, get a silly ANSI".  :-)

Chris

---

### Post by haqking on 2011-09-10
> **fabricator4 said:**
> 

As said, there's no dumb questions, although it reminds me of my favourite tagline from the eighties: "ASCII silly question, get a silly ANSI".  :-)

Chris

Ahhh yes back when i used to teach various IT Certifications (please god dont send me back there) i used to say that all the time to my students, along with "the only difficult question is the one you dont know the answer too" and " there are 2 types of people in this world...blah blah you know the rest ;-)

---

