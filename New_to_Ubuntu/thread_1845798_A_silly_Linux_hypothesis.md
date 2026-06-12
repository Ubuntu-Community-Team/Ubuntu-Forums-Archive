---
title: "A silly Linux hypothesis ?"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by youralibaba on 2011-09-17
Hi there gurus,

I want to ask that does linux save your hard disk life more than windows ? While watching a movies, I noticed on windows that hard disk activity light flickers a lot but in case of linux it does not flicker too many times. Does this mean that linux's memory management is far better than that of windows ?

---

### Post by ubudog on 2011-09-17
Linux does not use as much of the system's power (eg. memory) as Windows, so that might be a reason.  Not as much memory means not as much swapping to disk which means not as much light flashes.  :)

---

### Post by anewguy on 2011-09-17
In a given scenario, linux would probably use less memory, for example, than Windows.  Given the same amount of memory available, the same CPU(s), etc., one would expect the disk to flash less because with linux using less memory there isn't as much activity to the swap file/partition.

Dave ;)

---

### Post by youralibaba on 2011-09-17
> **anewguy said:**
> In a given scenario, linux would probably use less memory, for example, than Windows. Given the same amount of memory available, the same CPU(s), etc., one would expect the disk to flash less because with linux using less memory there isn't as much activity to the swap file/partition.
 
Dave ;)
 
Thanks for the answer guys, but does this also mean that your hard disk life would get extended ?

---

### Post by JC Cheloven on 2011-09-17
HD life depends on several factors (including luck he he). Among the more relevant ones is how often it parks its heads. They're usually designed for ~600000 parks. 

Laptops use to park a lot to save battery and prevent the effects of eventual shaking etc. Less than 15 parks/hour should be ok. Interestingly, the number of parks is stored in the disk. You can find it using an utility called smartctl (in the package smartmoontools in the repos). You can also disable parking, using hdparm. 

Also important is how much the head writes (and to a minor extent, reads) to the disk. Windows likes to do a lot of user-hidden stuff, related to antivirus and who-knows-what else. That can easily make a difference in favor of linux.

Cheers
JC

---

### Post by tgalati4 on 2011-09-17
More Windows disks fail simply because there are more machines running Windows.  It would be hard to differentiate because music/video editing can take it's toll on a hard disk whether in Windows or in Linux.

Any operation that has long, sustained writes will reduce life on a consumer-grade drive, because the extra current required to write causes the heads to heat up.  After a long video editing session, those little heads get toasty and warp.  Once warped, you get read errors.

After checking my 2-year-old WD 320 GB laptop drive I have the following:

329,258 parks (91% life left)
3061 power-on hours (96% left)
0 write or read errors.

That's 107 parks per hour, but the SMART rating seems to think that's OK.

Here's an interesting link:  [http://www.sagaforce.com/~sound/wdantiparkd/](http://www.sagaforce.com/~sound/wdantiparkd/)

I really think hard drive wear depends on your use case and not really driven by operating system.  Although there may be bugs and excessive parking which can contribute to hard drive failure, your personal use case will determine it's demise.

Taking a laptop and recording a 2-hour concert at a nightclub will likely shorten it's life.

---

