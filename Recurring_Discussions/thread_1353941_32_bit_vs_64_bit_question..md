---
title: "32 bit vs 64 bit question."
date: 2009-12-13
forum: Recurring Discussions
---

### Post by mattweed9 on 2009-12-13
I was wondering, would the 32 bit possibly run better then the 64 bit? I know the 64 bit versions are some what newer,and was just wanting to know if maybe I'd have more success with the 32 bit version maybe.

---

### Post by NoaHall on 2009-12-13
64 bit will maybe be a bit faster, if that's what you mean.

---

### Post by Hetepeperfan on 2009-12-13
> **mattweed9 said:**
> I was wondering, would the 32 bit possibly run better then the 64 bit? I know the 64 bit versions are some what newer,and was just wanting to know if maybe I'd have more success with the 32 bit version maybe.

Heey,

I'm Running a 64 and a 32 bit linux version. Basically a 64 bit Ubuntu install work just fine! But it depends on what you'll need. If you don't need to do any very high precision computing you'll probably be fine with a 32 bit operating system. If you'll don't need any special stuff you will keep things more simple to install a 32-bit version, there is no reason to do it the hard way if you don't need the 64 bit precision any way.

You can of course make 2 installs bot the 32 and the 64 bit and examine what you like.

I've run into some difficulties when some of the programs i'm running need 32 bit libs. And then it seems hard to install the 32 bit version of the same program. While on my 6-8 year old 32 bit machine everything runs just fine.

best

---

### Post by cartisdm on 2009-12-13
> **mattweed9 said:**
> I was wondering, would the 32 bit possibly run better then the 64 bit? I know the 64 bit versions are some what newer,and was just wanting to know if maybe I'd have more success with the 32 bit version maybe.

Generally my rule of thumb is to run 32-bit unless for some reason I can't get something working.  If it ain't broke, don't fix it.

Also, I believe it is recommended to have 4GB of RAM install or you won't see much improvement

---

### Post by cenzorrll on 2009-12-13
64-bit operating systems allow the processor to be more efficient with computations as you have 64 bits per cycle rather than 32 bits, and also lets the processor use more ram.  32 bit is maxed out at around 4Gb of ram, whereas 64 bit can access supposedly access somewhere in the terabytes.  

HOWEVER, you need programs optimized for 64-bit processors to see any improvement, unfortunately most "64 bit" programs are just 32 bit programs that work on 64 bit processors.  So at the moment there basically is no difference between the two except that you can access more ram with a 64 bit OS.

---

### Post by howefield on 2009-12-13
> **cenzorrll said:**
> HOWEVER, you need programs optimized for 64-bit processors to see any improvement, unfortunately most "64 bit" programs are just 32 bit programs that work on 64 bit processors.

Where are you getting your information from ?

I'd say most 64 bit programs are just that, 64 bit.

---

### Post by hazelsct on 2009-12-13
Aside from memory issues raised above, 64-bit has a better instruction set with more available registers, but bulkier code.  So if a 32-bit piece of code just fits in cache, it will run faster than a 64-bit piece which is too big, cache misses are a huge performance hit.

If you're not sure, go with 64, and you can still install 32-bit apps like Flash.

---

### Post by QIII on 2009-12-13
This is a recurring discussion.

---

### Post by Joeb454 on 2009-12-13
> **QIII said:**
> This is a recurring discussion.

Correct ;) - Moved to Recurring Discussions

---

### Post by mattweed9 on 2009-12-14
Um, I think I was misunderstood. I meant, is 32 bit any more stable then 64 bit. I know the benefits of 64 bit and yes my system is made to run 64 bit OS's. I just wasn't sure if 64 bit was unstable compared to the 32 bit version. Do people who run the 64 bit version and have problems, have any better luck running 32 bit?

---

### Post by NoaHall on 2009-12-14
> **mattweed9 said:**
> Um, I think I was misunderstood. I meant, is 32 bit any more stable then 64 bit. I know the benefits of 64 bit and yes my system is made to run 64 bit OS's. I just wasn't sure if 64 bit was unstable compared to the 32 bit version. Do people who run the 64 bit version and have problems, have any better luck running 32 bit?

No. They are equally stable in my view, but I'd always go for 64 bit. This isn't 2001 anymore :)

---

### Post by mattweed9 on 2009-12-14
Thats what I figured, thank you.

Edit:

As a side note, I am surprised 64 bit isn't more common then it is today. Seems like just now, more and more computers are coming with 64 bit OS's.

---

### Post by cartisdm on 2009-12-14
> **mattweed9 said:**
> 
Edit:

As a side note, I am surprised 64 bit isn't more common then it is today. Seems like just now, more and more computers are coming with 64 bit OS's.

I am to actually, it seems like whenever I talk about 64-bit OSs people look at me like I'm crazy

---

### Post by cascade9 on 2009-12-14
> **cartisdm said:**
> Generally my rule of thumb is to run 32-bit unless for some reason I can't get something working.  If it ain't broke, don't fix it.

Also, I believe it is recommended to have 4GB of RAM install or you won't see much improvement

Not anymore.... 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

I would always go for 64bit over 32bit if your system supports it. Same as I would always go for i586 or i686 over i386 if you have a choice. *Edit- if your really low on RAM, 1GB or less then I would possibly still use 32bit. 1GB 'low' on RAM, how times change....

Only issue I've found in running 64bit is there are 64bit flash annoyances, but they can be worked around easy enough.

---

### Post by cartisdm on 2009-12-14
> **cascade9 said:**
> Not anymore.... 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

I would always go for 64bit over 32bit if your system supports it. Same as I would always go for i586 or i686 over i386 if you have a choice. *Edit- if your really low on RAM, 1GB or less then I would possibly still use 32bit. 1GB 'low' on RAM, how times change....

Only issue I've found in running 64bit is there are 64bit flash annoyances, but they can be worked around easy enough.

I just read through that article and it seems to only support my original statement.  The benchmarks were hardly convincing, buggy 64-bit programs, and the performance still needing high RAM requirements in order to work efficiently, I'm sticking w/ 32-bit unless I just get frisky;)

---

### Post by NoaHall on 2009-12-14
> **cartisdm said:**
> I just read through that article and it seems to only support my original statement.  The benchmarks were hardly convincing, buggy 64-bit programs, and the performance still needing high RAM requirements in order to work efficiently, I'm sticking w/ 32-bit unless I just get frisky;)

Trust me. They aren't buggy, it's faster, and it's better. Stop living in the past.

---

### Post by bowens44 on 2009-12-14
Been using 64 bit for a while now nad haven't seen any buggy programs that were less buggy in 32 bit.....except maybe flash but it's working great now.

---

### Post by cenzorrll on 2009-12-14
> **howefield said:**
> Where are you getting your information from ?

I'd say most 64 bit programs are just that, 64 bit.


come to think of it, i believe that information is through use of windows. i only recently started using linux 64 bit.

---

### Post by cascade9 on 2009-12-15
> **cartisdm said:**
> I just read through that article and it seems to only support my original statement.  The benchmarks were hardly convincing, buggy 64-bit programs, and the performance still needing high RAM requirements in order to work efficiently, I'm sticking w/ 32-bit unless I just get frisky;)

I'd call 64bit being faster at every benchmark (bar 64 bit flash non-alpha) "convincing". 

I havent found any buggy problems with 64 bit, maybe I'm just lucky? Or maybe your reading circa 2006/2007 reviews, or remembering what it was like than :P

I wouldnt call 2GB 'high RAM' in this age. 

Sticking with 32bit is fine, I'm not running your computer ;) But there is nothing wrong with 64bit, and its got advantages over 32 bit ,even for 'normal desktop' use, let alone if you ever do any real crunching (like audio or video encoding).

---

### Post by cartisdm on 2009-12-15
> **cascade9 said:**
> I'd call 64bit being faster at every benchmark (bar 64 bit flash non-alpha) "convincing". 


Barely higher in nearly all the benchmarks

> 
I havent found any buggy problems with 64 bit, maybe I'm just lucky? Or maybe your reading circa 2006/2007 reviews, or remembering what it was like than :P


True, I haven't tried 64-bit programs in at least 12 months so I will stop relying on that.  I just offered to buy a friend's laptop last night, if he takes me up on it that will be a Linux Only pc and I will try out 64-bit again ;)

> 
I wouldnt call 2GB 'high RAM' in this age. 

I was under the impression that 4gbs or higher was needed to see any improvements, but if 2GB is sufficient then I stand corrected.

> 
Sticking with 32bit is fine, I'm not running your computer ;) But there is nothing wrong with 64bit, and its got advantages over 32 bit ,even for 'normal desktop' use, let alone if you ever do any real crunching (like audio or video encoding).

Truth.  If anyone does any video/audio encoding then I absolutely recommend using a 64-bit OS.  It is really that much better and you will be happy.

---

### Post by cascade9 on 2009-12-19
That review was on 2GB, so that '4GB is needed for improvements' is petty much a myth these days. I'm sure if you benchmarked enough software, you would find something that needs 4GB to be faster, but it would be the exception, not the rule. 

As for 'barely higher', point. But like they say in drag racing 'seconds are made up of lots of 100ths of seconds'. Meaning if you really want to make things faster, you need to pay attention to every improvement you can get, not just the big ones. 

Anyway, the performance difference it similar to what I've seen with EXT3 vs EXT4. (which is widely acclaimed as 'faster than EXT3') Some large gains (eg audio encoding for 64 bit, large file transfers on EXT4). Most gains are minimal, but still there.

---

### Post by gs777 on 2009-12-19
I don't know what the theory says. But I have used both versions on my dual core lappu. .....64 bit is much faster in every aspect.Firefox rocks

---

