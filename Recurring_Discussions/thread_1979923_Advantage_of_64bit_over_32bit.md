---
title: "Advantage of 64bit over 32bit"
date: 2012-05-14
forum: Recurring Discussions
---

### Post by Deepak J on 2012-05-14
Is there any practical advantage of using 64bit instruction set when compared with the 32bit instruction set other than the fact that the 64bit can handle memory size more than 4GB efficiently.

I want to know if there is any difference in the performance and speed of the functioning the computer.

I at presently am using a 32bit Ubuntu 12.04 OS and I wouldn't mind reinstalling the OS once more to a 64bit version.

Thanks in advance.. :D

---

### Post by mcduck on 2012-05-14
Yes, there is. But if you see any difference or not depends on what kind of tasks you use your computer for.

Any applicaton that needs to handle large numbers or high precision numbers gets a significant performance boost on a 64-bit system, as doing the same job on a 32-bit system would require breaking it down into multiple stages thus of course taking much longer time to execute.

...on the other hand, typical desktop apps like word processors, web browsers etc don't need to deal with such things, so most common situatons when you'd see benefits from a 64-bit system are video and sound encoding, 3D graphics renderign and other similar media processing tasks. Assuming, of course, that the programs you are using are actualy made to be able to benefit from the 64-bit features.

---

### Post by jadtech on 2012-05-14
> **Deepak J said:**
> Is there any practical advantage of using 64bit instruction set when compared with the 32bit instruction set other than the fact that the 64bit can handle memory size more than 4GB efficiently.

I want to know if there is any difference in the performance and speed of the functioning the computer.

I at presently am using a 32bit Ubuntu 12.04 OS and I wouldn't mind reinstalling the OS once more to a 64bit version.

Thanks in advance.. :D

there is a lot of difference  between what can be done with 32bit and 64 bit  dual core quad core and such  how ever the average user uses less then 10% of what there computer ability  most gamers and web surffing  speed and such requires technology brute strength so to speak ( loads of RAM) to make internet conection  faster and such ..

if you were doing lots of calculation or  like pixar animation stuff not only is the ram handy but haveing a true 64bit processor make a big differnece ..

---

### Post by flemur13013 on 2012-05-14
I recently tried 32 and 64 bit 10.04; the only obvious difference was in video conversions, which were considerably faster w/64.

---

### Post by mörgæs on 2012-05-14
Moved to Recurring Discussions.

---

### Post by QIII on 2012-05-14
In terms of performance, the normal user will see little difference.  Guys like me definitely would.

Two things:

1.  Software developers and the industry have moved to 64 bit and don't like maintaining extra code.

2.  Remember what happened to the 8 and 16 bit hangers-on.

---

### Post by bobzr on 2012-05-14
I've been using 64-bit for several years now. The question should be why use 32bit instead of 64bit.

---

### Post by oldfred on 2012-05-14
If you have enough RAM then it makes sense to use 64bit. Some say the break point is really between 2 & 3 GB of RAM.

Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Advantages and Disadvantages of 64bit. (Plus install Guides) from 2008
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
Benchmarks Performance on 9.04
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by Deepak J on 2012-05-15
The other day I read somewhere that though the modern machines are shipped with 64 bit compatible processors, most of the popular softwares are still supported by 32 bit systems. And the transition from 32 to 64 bit can take some time to occur. Should I consider that piece of advice or will the software firms start shipping 64 bit ones the sooner or later.

Also is there something like 'downward compatibility' for this 64 bit systems. I mean can we still run 32 bit programs on the 64 bit sys..?

---

### Post by rai4shu2 on 2012-05-15
Actually there's a lot of discussion lately about support for x32 (or running 32 bit apps on 64-bit systems). There are definitely advantages both ways, but it mostly depends on your CPU (and the amount of caching it can do).

---

### Post by Deepak J on 2012-05-15
> **rai4shu2 said:**
> Actually there's a lot of discussion lately about support for x32 (or running 32 bit apps on 64-bit systems). There are definitely advantages both ways, but it mostly depends on your CPU (and the amount of caching it can do).


my specs are as follows
Intel Core2 Duo E7400 - 2.8 GHz, 3 MB cache
2 GB - DDR 2 
On board 128 MB graphics(planning to upgrade to a 1GB GPU)

I basically do music creation,mixing and editing. Programming - mainly C 'n C++, casual gaming and surfing the net

---

### Post by Paqman on 2012-05-15
> **Deepak J said:**
> The other day I read somewhere that though the modern machines are shipped with 64 bit compatible processors, most of the popular softwares are still supported by 32 bit systems.

That's probably written from a Windows perspective. With open source software supplying a 64-bit version is as simple as compiling it against that system. So everything that's available in the repos as 32-bit is also available as 64-bit.

> 
Also is there something like 'downward compatibility' for this 64 bit systems. I mean can we still run 32 bit programs on the 64 bit sys..?

Yes, although you'll probably find you don't need to. It used to be necessary for stuff like Flash, but I haven't had to run any 32-bit software for years now.

---

### Post by mips on 2012-05-15
If you have a 64-bit CPU there is no reason why you should not run 64-bit linux.

Things like audio & video encoding are faster, compressing & uncompressing files are faster, encryption based apps are faster, compiling source code is faster, memory reads & writes are faster and a few other things I have forgotten about.

Software availability on Linux has **not** been a issue for several years now, everything in the 32-bit repos is available in the 64-bit repos. Do not confuse generalised statements which refer more to windows with linux, currently windows lags linux in 64-bit support (apps & drivers hence running 32-bit apps on windows 64-bit).

I've been running 64-bit linux since 2006, back then there were a few issues you had to work around but these days there is absolutely no reason not to go 64-bit if you have the hardware.

---

### Post by Deepak J on 2012-05-16
Thanx guys for the advices. I'm gonna straight away switch to 64 bit version.

---

### Post by rai4shu2 on 2012-05-16
Yeah. You don't get x32 without a solid 64-bit system to begin with, and they haven't even implemented it, yet. So, there's really no point in avoiding 64-bit. In particular, once gcc stable has x32 support. Then the benchmarks can start guiding us down that path (what apps work better that way and which don't).

---

