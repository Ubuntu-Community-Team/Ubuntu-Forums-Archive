---
title: "ok, fcked myself over. how to reverse and get win xp back?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by arikun on 2008-05-25
so i guess i copied over xp...brilliant :(  question now is how do i get it back, or can i even do that...i used some backup programs, but now i find out  something about it only being a real backup if it was done during bootup...so, im fcked once again. w/e i do have is in two external drives. one i cannot access, need to force close it but only the admin can, so how do i do that..??
second has the files copied.
](*,)
any idea what i can do now???
any help will be greatly appreciated!

---

### Post by skymera on 2008-05-25
You overwrite XP?  Did you not follow the Ubuntu installation carefully?

You can't get it back because 1. it's formatted and been written over in a whole new FS.

You can resotre however if you had an image of your drive.
Or a snazzy backup routine.

Do you have XP CD? If so, then thats how you can reinstall.

---

### Post by bumanie on 2008-05-25
I put this in your original post. It is not a good idea to make a new post about the same issue as it gets confusing following two posts.
You could try test disk from [here]("http://www.cgsecurity.org/wiki/TestDisk") Read the documentation carefully. It is not the most expansive, but it has saved other's before. It is a data/partition recovery program that can run from a live cd. Could also try photorec (same kink) or trinity rescue disc which has a ntfs undelete program on it - it also is a live cd. Good luck. Try to leave that drive unwritten to until you have the rescue discs. There is also ntfsprogs in synaptic that has a ntfsundelete program also. Unfortunately, I am not expert in using these, but you can't really end up any worse than you are now, so it's worth a go. With ntfsundelete, you have to send the output to a partition other than the one where you are retrieving the information from. Read up on all these before you decide which one to follow/try. Good luck.

---

### Post by arikun on 2008-05-25
> **skymera said:**
> You overwrite XP?  Did you not follow the Ubuntu installation carefully?

You can't get it back because 1. it's formatted and been written over in a whole new FS.

You can resotre however if you had an image of your drive.
Or a snazzy backup routine.

Do you have XP CD? If so, then thats how you can reinstall.

all it wanted from me was sn, pw, and time....

---

### Post by HyperHacker on 2008-05-25
I accidentally created an empty EXT3 filesystem overtop of an NTFS partition I was using once, and R-Studio managed to recover most of it. It's not free though. :( Also, I was fortunate in that it wasn't the partition Windows was on, so I still had an OS to run it from. If your drive has another partition that can fit Windows (even 98 will do) you could install it there temporarily to run R-Studio from to recover the main partition. Just make sure you do NOT touch that partition beforehand.

There's probably a free Linux boot CD that can do the job, but I don't know of one. Either way, I managed to recover nearly everything after formatting it with another filesystem, so if you didn't actually install something on it, your chances are pretty good. NTFS has a backup of the filesystem that's less likely to get wiped out.

Windows will probably be hosed, but you may be able to recover anything important you had stored there and repair it using the install disc (though I would suggest copying anything important to another drive, formatting, and reinstalling).

---

### Post by skymera on 2008-05-25
> **arikun said:**
> all it wanted from me was sn, pw, and time....

I gives partitioning options.
Which i think you assumed was correct.

By default it uses "Guided" install which uses the whole disk or first partitions.

I realised that on my laptop when i had 50GB Ubuntu on a 50GB disk, and i knew XP didnt shrink.. :lolflag:

---

