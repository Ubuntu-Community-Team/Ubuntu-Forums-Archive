---
title: "Would ubuntu 32bit/ 4 gb RAM run better than Ubuntu 64 bit/ 4 gb ram?"
date: 2013-10-25
forum: Recurring Discussions
---

### Post by ripx2 on 2013-10-25
Got a work desktop, mainly for tropubleshooting...its win 7 32 bit. Im gonna dual boot so I can play with it on my lunch hour, but im not sure, with 4 gb RAM, if I should go 64 bit( I read if its over 2 gb, do 64) or if 32 bit would be super fast with 4 gb RAM>...

Your thoughts???

Its a dell gx520, 2 dim slots, 4 gb RAM max.

---

### Post by deadflowr on 2013-10-25
64 bit is faster.

---

### Post by QIII on 2013-10-25
[I]Moved to **R**[B]ecurring Discussions.


[/B][/I]This well-beaten horse is still quite dead.

---

### Post by rrnbtter on 2013-10-25
Greetings,
32bit with 4gig of ram runs fine. If you have native 64bit software then you should use the 64bit OS. The felt speed will vary depending on machine architecture. I would think though that if your motherboard is maxed out at 4gig of RAM then run 32bit. If it is upgradeable to above 4Gig then install the 64bit version.

---

### Post by craig10x on 2013-10-25
I'd run 64 bit ubuntu if i were you....i do....i have 4gb of ram...even on 64 bit, the most ram ubuntu takes is about 1 gb on my laptop...this is assuming your computer is 64 bit of course...

---

### Post by Skyline_8650 on 2013-10-25
Go for 64 bit, on my system it's proven to be much more stable then a 32bit install, I don't notice any speed differences. I too have not seen ubuntu use over a 1024MB of ram.

---

### Post by unixpcguy on 2013-10-25
I have a laptop that only seems to take 64 bit OS. If that's what it calls for then use that. I also have another system that can use 32 bit and/or 64 bit on a Gigabyte motherboard. However I prefer mostly 64 bit. You can max out your ram with 64 bit OS which is nice.

---

### Post by deadflowr on 2013-10-25
> **unixpcguy said:**
> I have a laptop that only seems to take 64 bit OS. If that's what it calls for then use that. I also have another system that can use 32 bit and/or 64 bit on a Gigabyte motherboard. However I prefer mostly 64 bit. You can max out your ram with 64 bit OS which is nice.

Slightly off topic on this, but Ubuntu's 32 bit version comes with [PAE]("http://ubuntuforums.org/newreply.php?do=newreply&p=12828546") enabled.
If your system can't handle PAE, then it can't run the 32 bit version.
This might be why you can't run the 32 bit version.

---

### Post by 3rdalbum on 2013-10-26
If this computer came with Windows 8, you need 64-bit.

You should be running 64-bit anyway. 99.99% of Linux software and 100% of important software is 64-bit, and there will be a speed improvement for intensive processing tasks.

---

### Post by Xubuntist on 2014-03-31
Excuse me for reviving this thread. I promise I **have** looked elsewhere for the answer but it's, frankly, confusing. 

Running  **lscpu** tells me the following:
```
$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               1200.000
BogoMIPS:              4400.20
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K

```

OK, so far I've found that this tells me I am running 32-bit Xubuntu on a 64-bit-capable processor. But what it doesn't tell me is whether I have a 64-bit motherboard. I've read elsewhere that this isn't a relevant question and that what your motherboard is or isn't capable of is determined by your CPU and your OS. Is this correct? If so, it certainly simplifies things.

**BUT**...

The computer i'm concerned about is a home-built one with an ASUS P5LD2-X/1333 motherboard. I have checked the ASUS site and it states the following:
```
**64-bit CPU support**. This motherboard provides excellent compatibility and flexibility by suppor
```
Yes, it's not my typo, it just ends like that. If you do a search on Google for that phrase you'll find it on all ASUS mobo pages. I would have loved to know how the sentence ended, but never mind.

So, the ASUS site tells me that the motherboard has full 64-bit support, and **lscpu** tells me that the CPU is 64-bit enabled. Further down it also, sadly, tells me:
```
2 x240-pin DIMM, **Max. 4 GB**, DDR2 667/533/400 Non-ECC,Un-buffered Memory. Dual Channel memory architecture.
```
Alright, so I now have the information that I really needed. The computer currently has 2Gb RAM and if I max it out to the measly 4Gb and install the AMD64 version of Xubuntu I can take advantage of all of that 4 Gb.

So, my question really is: in (X)Ubuntu, how can I tell **without opening up the case, closing it again, booting up and running off to the manufacturer's website** what is the 32/64-bit capability of the motherboard fitted? The reason I ask is that I would like to be able to have this information to hand **before** installing Xubuntu. I now know that the computer I'm working on should have had the AMD64 version installed and I'll have to do that now and hope it doesn't break anything, I guess.

I really would be very grateful for your help here because I've read so many posts on the subject, most of which the mods have relegated to "recurring posts" but which nevertheless do not appear (to me, anyway) to address this specific motherboard question that is worrying me.

Thank you very much in advance for your guidance.

---

### Post by Xubuntist on 2014-03-31
Just an addendum to add to my confusion
```
$ sudo uname -pim
**i686 i686 i686**
```
Could somebody explain why it is telling me that, based on the information I gave in the post above?

I'm sorry for all the, probably noob, questions. I truly am confused. :(

---

### Post by Xubuntist on 2014-04-02
[CENTER][ATTACH=CONFIG]251650[/ATTACH]
[/CENTER]

---

