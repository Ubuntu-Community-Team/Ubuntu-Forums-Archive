---
title: "64bit and 32 bit- why?"
date: 2012-08-03
forum: Recurring Discussions
---

### Post by abduljones on 2012-08-03
Could someone who knows, as opposed to someone with a guess, educated or otherwise, explain why there are 64 bit and 32 bit OSs and when you would use each one. I don't have a problem with anything per se, but it came up in a conversation and I can't find an answer that doesn't assume a level of knowledge I haven't got (I'm only up to chapter 5 of Mr Shott's very interesting book). I've never thought to use a 64bit as I was told they were unstable, which prompted the question, then why would you...?

---

### Post by FatFrog on 2012-08-03
As the number of bits (32/64) increases there are two main benefits.

Firtsly, More bits means that data can be processed in larger chunks more accurately. Additionally, more bits means your system can address a larger number of locations in physical memory.

Hope this helps!

---

### Post by Dylan1473 on 2012-08-03
If you have a 64 bit processor you should use a 64 bit operating system. A couple years ago it might have been true that they were too unstable but I've been running 64 bit for quite some time with no problems, along with many others.

A 64 bit system *may* provide a small speed increase (so small as to not really be noticeable, though), but the primary benefit is that it allows for the use of more memory. If your total RAM (both standard memory and graphical memory, I believe) is at or exceeds 4GB you need a 64 bit system to make use of all of it.

Additionally, most modern systems (at least Laptop/Desktop/Server) are now made to use the 64 bit architecture. 64 bit was once much less common (which was probably the larger part of the reason it was unstable) but this is no longer true. If 64 bit is not actually more common now (and I'm not actually sure) I expect it will be before too long.

---

### Post by cogier on 2012-08-03
Here you will find a detailed explanation. [http://www.techsupportalert.com/content/32-bit-and-64-bit-explained.htm]("http://www.techsupportalert.com/content/32-bit-and-64-bit-explained.htm")

---

### Post by QIII on 2012-08-03
Use a 64 bit OS.

Countdown to move to recurring discussions begins now...

---

### Post by oldos2er on 2012-08-03
> **abduljones said:**
>  I've never thought to use a 64bit as I was told they were unstable, which prompted the question, then why would you...?

Moved to Recurring.

I use 64-bit software in order to take full advantage of my hardware. Never experienced unstability that could be attributed solely to bitness. For the most part in Linux, the same code is compiled for use on various architectures.

---

### Post by 3rdalbum on 2012-08-04
> **abduljones said:**
> I've never thought to use a 64bit as I was told they were unstable

You were probably told this by Windows users, whose only yardstick was Windows XP 64-bit.

To be fair, Windows XP 64-bit wasn't unstable as far as I know - it's just that most programs at the time were 32-bit and not guaranteed to work reliably on a 64-bit operating system.

Linux really has no problems with 64-bit OSes or programs. It runs well on eleven wildly different CPU architectures - why wouldn't it run well on the world's most common CPU architecture with a couple of 64-bit extensions?

---

### Post by thatguruguy on 2012-08-04
> **Dylan1473 said:**
> 

A 64 bit system *may* provide a small speed increase (so small as to not really be noticeable, though)

Unless, like me, you do a significant amount of video transcoding, or run other programs that can benefit from multi-threading. In which case the performance increase can be significant.

---

### Post by codingman on 2012-08-04
64-bit is also slightly faster in my opinion, and can get more out of my physical ram, also overclocks components better.

Just a long shot at explaining an in-depth thing in computers.

---

### Post by vexorian on 2012-08-04
64 bit ubuntu used to have app compatibility problems in the past (imagine no flash, and worse WINE). Nowadays it seems that things are all right.

In my opinion, if you have less than 4GB of RAM you should use 32 bits. If you have more 4GB you MUST use 64 bits. If you have exactly 4GB, then you can go either way.

---

### Post by ranger1021994 on 2012-08-04
64 is the future and 32 is the past
It will take some time for people to shift but shift is inevitable

64bit : primarily useful if you have more RAM installed ie. >4GB

32bit apps can run mostly without any problems on Windows while Ubuntu provides both 32 and 64 bit applications and packages

I personally recommend 64bit.

---

### Post by oldos2er on 2012-08-04
> **vexorian said:**
> In my opinion, if you have less than 4GB of RAM you should use 32 bits. If you have more 4GB you MUST use 64 bits. If you have exactly 4GB, then you can go either way.

64-bit Ubuntu runs extremely well with 2GB RAM. Tasks such as video encoding are measurably faster than they are on 32-bit (speaking from experience).

---

### Post by vexorian on 2012-08-04
> **oldos2er said:**
> 64-bit Ubuntu runs extremely well with 2GB RAM. Tasks such as video encoding are measurably faster than they are on 32-bit (speaking from experience).
It is not speed that worries me, but memory. With 32 bits, I already have trouble not using all my RAM in 2GB. If I had at least other 2GB I would try 64 bits.

Between firefox and Java my setup is already using more than 1.0GB, if I add virtual box to the mix, that's buh bye to my memory.

---

### Post by Paqman on 2012-08-04
32-bit is the legacy standard, but some hardware is still limited to being 32-bit only.

64-bit is the new standard, and is supported by almost all modern hardware. Linux has excellent 64-bit support, so there's no real reason to use a 32-bit OS on 64-bit hardware.

---

### Post by Paqman on 2012-08-04
> **vexorian said:**
> 
In my opinion, if you have less than 4GB of RAM you should use 32 bits. **If you have more 4GB you MUST use 64 bits**. If you have exactly 4GB, then you can go either way.

That's not quite correct.

32-bit Ubuntu can use more than 4GB of RAM, but it does it by using a system called PAE that is a bit of a kludge. Very few systems have both >4GB RAM and a 32-bit only CPU, but I guess they do exist and so PAE is a useful tool to have in the box.

I wouldn't bother using 32-bit on a <4GB RAM system with a 64-bit CPU unless it was very short on RAM. You'd have to get down to about 1GB or less for it to make sense installing 32-bit just for RAM purposes, as the 64-bit version will use slightly more RAM to do the same stuff.

---

### Post by vexorian on 2012-08-26
> **Paqman said:**
> That's not quite correct.

32-bit Ubuntu can use more than 4GB of RAM, but it does it by using a system called PAE that is a bit of a kludge. Very few systems have both >4GB RAM and a 32-bit only CPU, but I guess they do exist and so PAE is a useful tool to have in the box.

I wouldn't bother using 32-bit on a <4GB RAM system with a 64-bit CPU unless it was very short on RAM. You'd have to get down to about 1GB or less for it to make sense installing 32-bit just for RAM purposes, as the 64-bit version will use slightly more RAM to do the same stuff.
So, at the end I decided to try a migration to 64 bit ubuntu.

It *is* much faster, to the point not even compiz seems to take away the feeling of it being blazing fast. That is one point to the ones recommending 64 bit.

But I ran into problems with installing WINE, at best this means that the smallest mistake by a dev forgetting to release an update in a i386 package when updating an amd64 package could cause you to run into dependency issues due to multiarch still being a young technology. So IMHO, saying that compatibility issues are a thing of the past in 64 bit ubuntu is not really so true...

---

### Post by thatguruguy on 2012-08-26
> **vexorian said:**
> So, at the end I decided to try a migration to 64 bit ubuntu.

It *is* much faster, to the point not even compiz seems to take away the feeling of it being blazing fast. That is one point to the ones recommending 64 bit.

But I ran into problems with installing WINE, at best this means that the smallest mistake by a dev forgetting to release an update in a i386 package when updating an amd64 package could cause you to run into dependency issues due to multiarch still being a young technology. So IMHO, saying that compatibility issues are a thing of the past in 64 bit ubuntu is not really so true...

I'm running the 64-bit version of Ubuntu on 4 different boxes, and Wine runs fine on each one.

---

### Post by synaptix on 2012-08-26
> **vexorian said:**
> So IMHO, saying that compatibility issues are a thing of the past in 64 bit ubuntu is not really so true...

I've been using 64 bit Ubuntu since 9.10, never had any issues. No issues either with Wine, even before multiarch came along.

---

### Post by vexorian on 2012-08-27
The issue I had was actually caused by multiarch.

Or rather, something about libfontconfig releasing a new version in amd64 architecture but not releasing it in i386. So if a package (read WINE) indirectly depended libfontconfig in i386 architecture, libfontconfig:i386 couldn't be isnstalled since its old version would conflict with the version of the amd64 one. Not being able to install it, WINE kept giving dependency errors.

So, I am just happy that 64bit ubuntu is so fast, but I would not recommed it to newbies that don't like package installation randomly not working because of multiarch inconsistencies.

---

### Post by Paqman on 2012-08-27
> **vexorian said:**
> The issue I had was actually caused by multiarch.

Or rather, something about libfontconfig releasing a new version in amd64 architecture but not releasing it in i386. So if a package (read WINE) indirectly depended libfontconfig in i386 architecture, libfontconfig:i386 couldn't be isnstalled since its old version would conflict with the version of the amd64 one. Not being able to install it, WINE kept giving dependency errors.

So, I am just happy that 64bit ubuntu is so fast, but I would not recommed it to newbies that don't like package installation randomly not working because of multiarch inconsistencies.

You might want to wait a bit and try the update again, it could just have been that your repos were out of sync or something. Failing that try a different server. I've got wine on my 64-bit machine and haven't had any issues with updates lately.

---

### Post by oldos2er on 2012-08-27
> **vexorian said:**
> The issue I had was actually caused by multiarch.


You weren't by any chance using aptitude, were you? aptitude has some problems with multiarch: [https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768)

---

### Post by vexorian on 2012-08-27
I have never in my life used aptitude.

But don't worry, I fixed the issue the day after it appeared. For some reason the i386 package was in the launchpad releases website, but apt-get couldn't get it for some reason (and I kept updating the packages list).

---

### Post by oldos2er on 2012-08-28
> **vexorian said:**
> I have never in my life used aptitude.


Ah well, never mind.  :)
Glad you sorted it out though.

---

