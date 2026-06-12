---
title: "Is anyone else getting kernel panics?"
date: 2008-05-18
forum: Other OS Talk
---

### Post by MONODA on 2008-05-18
Hi I have been using ubuntu since september but when hardy came out, I upgraded and used it for a day but then removed it. The reason for this was because I had gotten about 3 kernel panics that day (I know they were kernel panics because everything froze up, I couldnt go into a virtual terminal and the caps lock light was blinking). So I installed archlinux and everything has been working fine for a while, until once I was connecting my bluetooth mouse and my laptop with hidd --search and I got a kernel panic (same "symptoms" as before). I thought oh, probably the bluetooth driver failed bringing down the system. After a while I decided to dual boot with debian to try it out. It seemed pretty nice and I liked it, but then I got another kernel panic. Is this just me or is someone else getting the same thing. I am really starting to worry (either the quality of the linux kernel is dropping, or my new laptop is going crazy[probably that considering it has worked badly in every OS I put on it]) MINIX 3 is starting to look REAL nice ;) so can anyone tell me if they are getting any problems. Even if you arent it would help let me know that perhaps I am alone.

---

### Post by Mr A Mouse on 2008-05-18
I'm working with an hp dv6000 (athlon x2, 2gb, dual-boot Heron and Vista), with absolutely no problems except some unsupported drivers. (nVidia and Atheros, both of which will work with 3rd party drivers, I just haven't gotten off my lazy tail and installed them.)

---

### Post by MONODA on 2008-05-18
well thats good news since you are enjoying it (:D) and that might mean that the kernel is still being developed well but it also means that I may have some messed up parts (actually I cant say that since we have quite different parts.) but i wouldnt doubt that my hardware is messed up, the first time I turned it on I got a blue screen lol and it would not shutdown no matter how long I waited (With vista that is). anyone else can tell me anything?

---

### Post by will1911a1 on 2008-05-18
I'd suffer a kernal panic usually once a day in 7.10 (64 bit).  I installed the 32 bit release but switched to Arch shortly after and haven't had any problems since.

I love Ubuntu, but the lockups got pretty irritating.

---

### Post by opendevlite on 2008-05-20
i had a kernel panic before, what i did is just reinstalled the memory stick, and it was fix.

---

### Post by pelle.k on 2008-05-20
> I love Ubuntu, but the lockups got pretty irritating.
Well, arch have them too. Maybe not with your configuration, but it's still evident. Kernel 2.6.24, and to some extent 2.6.25 has got this "problem".

[http://bbs.archlinux.org/viewtopic.php?id=43932](http://bbs.archlinux.org/viewtopic.php?id=43932)
[http://bbs.archlinux.org/viewtopic.php?id=48199](http://bbs.archlinux.org/viewtopic.php?id=48199)

[edit]*I also have these freezes (hard lockups if you will), on hardy heron and slax too. SysRq-REISUB doesn't work at all*[/edit]

---

### Post by Antman on 2008-05-20
I have no issues running kernels 2.6.24 and 2.6.25 (fedora) on various machines.

---

### Post by meborc on 2008-05-20
first i would have suggested a fresh install instead of an upgrade... BUT then i read you get the same problem in debian... :confused: you are either a very unlucky man or an owner of some deeep hardware :)

---

### Post by will1911a1 on 2008-05-20
> **pelle.k said:**
> Well, arch have them too. Maybe not with your configuration, but it's still evident. Kernel 2.6.24, and to some extent 2.6.25 has got this "problem".

[http://bbs.archlinux.org/viewtopic.php?id=43932](http://bbs.archlinux.org/viewtopic.php?id=43932)
[http://bbs.archlinux.org/viewtopic.php?id=48199](http://bbs.archlinux.org/viewtopic.php?id=48199)

[edit]*I also have these freezes (hard lockups if you will), on hardy heron and slax too. SysRq-REISUB doesn't work at all*[/edit]

Oh I'm not saying Arch is immune, I'm saying that it's been a lot more stable for me.  It has yet to lock up on me.

---

### Post by MONODA on 2008-05-21
> first i would have suggested a fresh install instead of an upgrade... BUT then i read you get the same problem in debian...  you are either a very unlucky man or an owner of some deeep hardware 
I think that there is a problem with my hardware actually for many reasons. Ever since I got this laptop, it has seemed to be falling apart (media buttons dont work, cd drive scratching cds, cd drive making weird noises when ejecting cds.) Also, I havent had much luck with any OS on here, it seems that arch is giving me the least problems so I will stick with that. You can see my specs in my sig.

---

### Post by pelle.k on 2008-05-21
> it seems that arch is giving me the least problems so I will stick with that.
That is so funny, because you know i've been running arch since 2005, and everyones saying pclinuxos/mandriva/ubuntu has the best hardware recognition etc, but i have *always* had a better experience with the unpatched (well, almost unpatched...) vanilla packages in arch linux than in any other distro.
Of course i have to set it up myself, but it really does work better if you take the time to do just that. Take kernel suspend as an example. It's never been any problem on any of the computers i've set up with arch, but it seldom works in any other distro.

---

### Post by RedSquirrel on 2008-05-21
> **MONODA said:**
> I think that there is a problem with my hardware actually for many reasons.

Check the memory and make sure the CPU is not overheating.

---

### Post by MONODA on 2008-05-22
> Check the memory and make sure the CPU is not overheating.
i am sure the cpu is not overheating since I have conky up and running most of the time and see a low temp (aroun 34 C). As for the memory, that might be the problem but this laptop is still pretty new, I got it last june.

---

