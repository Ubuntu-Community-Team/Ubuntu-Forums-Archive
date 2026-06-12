---
title: "not present: cmov - AMD"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Glkanter on 2011-12-17
I tried to run Ubuntu 11.10 from the cd on an old Compaq Presario 1200 with an AMD chip. The boot failed immediately with:
```
This kernel requires the following features not present on the CPU:
cmov
Unable to boot - please use a kernel appropriate for your CPU.
```I remember reading about this anomaly from a previous experience.

Are there any other 'flavors' of Ubuntu that will run on this chip?

Thanks!

---

### Post by Glkanter on 2011-12-17
Lubuntu 11.10 has the same problem.

---

### Post by matt_symes on 2011-12-17
Hi

cmov is an assembler instruction that was introduced with the Pentium pro processor. Your PC does not have it. It is an optimised move instruction.

You need a distribution that has an old kernel. Ubuntu will not work with that current kernel.

You can 

1. try a different distribution such as puppy linux. (You need a i486 or i586 architecture if i remember correctly) (a 2.4 kernel variant will work i think).
2. Try to find a kernel that will work with Ubuntu (not sure if that is possible)
3. Compile your own kernel without the cmov instruction.

You will need to do some research.

Kind regards

---

### Post by Glkanter on 2011-12-17
Xubuntu gives the same message.

---

### Post by Glkanter on 2011-12-17
Thank for the response.

I'll search for 'puppy linux.'
I find #2 confusing.
#3 is out of the question for me.

Thanks!

---

### Post by matt_symes on 2011-12-17
Hi

From here

[http://bkhome.org/blog/?viewDetailed=02418](http://bkhome.org/blog/?viewDetailed=02418)

> Lucid from Ubuntu is compiled such that it will run on 486 computers.   Maverick and up needs a 686 coputer.  The main reason for the change was  to take advantage of the cmov instruction, Lucid will install and run  on processors that do not have the cmov instruction.  I use it when  repurposing old thin client boxes based on the the VIA c3 or C7 or the  geode(all without cmov support). 

Maybe try Lucid (Ubuntu 10.04). That is going to be supported until April 2013.

Kind regards

---

### Post by Glkanter on 2011-12-17
Thanks for the suggestions. I'm downloading Puppy and Lucid.

Wish me luck!

---

### Post by matt_symes on 2011-12-17
Hi

> **Glkanter said:**
> Thanks for the suggestions. I'm downloading Puppy and Lucid.

Wish me luck!

Good luck.

Please post back to say how it went.

Kind regards

---

### Post by Glkanter on 2011-12-17
Lucid Alternate (ubuntu-10.04.3-alternate-i386.iso) began the process, then failed with:

```
Killed
[  140.101932] Kernel Panic - not synching: Out of memory and no killable processes...
[  140.101950]
```On to Puppy!

---

### Post by georgemc on 2011-12-17
The assembler instruction "cmov" was introduced somewhere around the 686 introduction, not sure when exactly.

Even though the 32bit Ubuntu ISO download files have a "i386" in their name they are not I386 but I686+ compilations.  This I think just adds to the confusion.

You can compile or cross-compile a kernel that does not use this instruction and install it on an older system.  It does require some effort, resources, and time on your part.

However: its not just the kernel that can be compiled requiring the "cmov" instruction, the applications can be compiled that way too.

I tried "Puppy" on an old (really old) laptop and was able to boot and install it.

Cheers

George

---

### Post by Glkanter on 2011-12-17
This forum is just far and away the best I've ever encountered for any sort of tech help. I really appreciate everybody's help.

Yes, Puppy is installing, and there is a desktop with icons.

It seems like it's still installing or configuring or something. I can't tell exactly what's going on, but it sounds like the cd drive is running, and the mouse pad pointer has a horrible response.

I'll let it keep running for the time being...

---

### Post by Glkanter on 2011-12-18
Mission Failed.

To make a long story short, after 3 misleading, but ultimately aborted attempts to load Puppy, the darn thing still tries to boot to Windows ME.

Thanks for everyone's help. Failure was a likely outcome, and I know I spent the minimal amount of time reaching that conclusion with this machine.

---

### Post by durand on 2011-12-18
How much memory does that computer have? That could also be a limiting factor? You might need something even ligther than Puppy Linux like ConnochaetOS: [http://www.connochaetos.org/wiki/](http://www.connochaetos.org/wiki/)

---

### Post by matt_symes on 2011-12-18
Hi

Might i suggest dsl (damn small linux) as well. It has a 2.4.x version of the kernel.

[www.damnsmalllinux.org](www.damnsmalllinux.org)

It is not maintained so much anymore but it may work on your system and give that old hardware a new lease of life.

How much memory *doesn't* it have by the way ?

Kind regards

---

### Post by Glkanter on 2011-12-20
I'll give those two flavors a try, thanks!

It looks like 640K + 59k extended?

---

### Post by Glkanter on 2011-12-20
I couldn't figure out how to download the Damn Small Linux...

---

### Post by matt_symes on 2011-12-20
Hi

Hhhmmm. Look for a version of DOS (Free Dos).

Kind regards

---

### Post by Miljet on 2011-12-20
Click the link given above. About halfway down the page, click on Downloads. On the next page, click on the last entry under Current Full Mirror List. That would be "ftp://ftp.heanet.ie/mirrors/damnsmalllinux.org/". Click Current on the next page. And finally click on "dsl-4.4.10.iso" and select where you want it to download. And don't forget to copy the md5sum just below the iso download.

---

### Post by Glkanter on 2011-12-21
Hey! The ConnochaetOS installed without any problems!

But I can't get a network connection. I have a Xircom PC card plugged in. And a Trendnet usb wifi available, but not plugged in.

Any suggestions?

Thanks!!

Garry

---

