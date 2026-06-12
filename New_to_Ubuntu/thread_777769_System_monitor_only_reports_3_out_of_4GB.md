---
title: "System monitor only reports 3 out of 4GB"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by leotemp on 2008-05-01
Maybe I just don't have my Linux goggles on yet but when i look at system monitor under memory it reports 3Gigs instead of 4, I'm guessing a gig is a GB but hell i don't know, at any rate, is this normal or should i check my ram? I just bought this memory but it was like 45 bucks for 2 GB so i wouldn't be surprised.

---

### Post by SOULRiDER on 2008-05-01
What kind of system do you have, 32 or 64 bit? 32 bit processors cant use all of your RAM.

---

### Post by leotemp on 2008-05-01
Intel Q6600 quad core 64bit, but I installed the 32 bit ubuntu though as I am a wary newb and my experience with 64bit Vista was f-ing brutal.

---

### Post by dtrot55 on 2008-05-01
I don't know if Linux acts like Windows when it comes to RAM but I do know in Windows even if you put in 4 gigs it will only show 3.25 gigs of ram.  So that might be the issue..but don't quote me on it.

---

### Post by nightfox91 on 2008-05-01
This is the case for any 32 bit OS, windows or ubuntu. It will only report up to 3.** GB of memory no matter what you have.

---

### Post by SOULRiDER on 2008-05-01
> **leotemp said:**
> Intel Q6600 quad core 64bit, but I installed the 32 bit ubuntu though as I am a wary newb and my experience with 64bit Vista was f-ing brutal.

Thats why, if you want to take advantage of your 4 GB, you will have to use 64 bit Ubuntu. If you decide to install it dont worry about problems that may arise, you cana sk for help in the forums.. and remember, this si not windows :p (thank god)

---

### Post by kosmic on 2008-05-01
Yap, that's true 3.25GB is the memory limit of a 32 Bits System.

The only way to get 4 or more memory is to use a 64Bits system or configure your 32 bits system to use PAE (physical Address Extension) - [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension).

---

### Post by Cap'n Redbeard on 2008-05-01
Hi Folks,

Please remember, 1 Gb is a north american term for 100 Mb. 1 Gig is really 1 thousand, NOT 100 Mb.

Also, when you format you end up with less than you bought (e.g. this 40Gb H/D is actually 3.4Gb). Best part of a meg (i.e. 840kb) is used up as system memory with a wintel box.

Was Millenium at the end of 1999 or 2000 ?

Or then again, is yer RAM working properly ?

:)

---

### Post by bensode on 2008-05-01
> **SOULRiDER said:**
> Thats why, if you want to take advantage of your 4 GB, you will have to use 64 bit Ubuntu. If you decide to install it dont worry about problems that may arise, you cana sk for help in the forums.. and remember, this si not windows :p (thank god)
The 32bit Ubuntu kernels have PAE enabled built in.  In my experience though it's never fully gotten to 4GB under 32bit.  As for the 64 bit editions I have been running 64 bit since 7.04 and haven't had a problem with normal use.  Just remember if you run Vmware or other software installed outside of apt, make sure you install the ia32-libs so that you can compile 32bit apps to run under 64bit.  

I also have a Dell Precision M65 laptop that is 64 bit but has a 32bit chipset so even with a 64bit OS, I still can't get more than 3.25G of RAM on it.  Yeah ... Dell got into some trouble with that.  MAke sure that Intel chipset you have is also truly 64bit BEFORE you take the trouble of installing a 64bit OS only to find out that there was a hardware limitation.

---

### Post by itsbradman on 2008-05-01
What are you talking about?  1GB is NOT a North American term for 100MB.  1GB IS a North American term for 1000MB.  Where did you find this utterly false information?

---

### Post by SunnyRabbiera on 2008-05-01
well the thing is though memory management in linux is completely different then it is in windows, in windows it seems it purposely eats up memory, in linux it only uses memory when it is needed :D

---

### Post by Dark Hornet on 2008-05-01
Well, I own a Q6600, and I am running 8.04 x64 and I love it.  It is very snappy, and so far I have had no issues with compatibility.  I use my Ubuntu computer for EVERYTHING except for a few games that I have not been able to get working under WINE yet.  Good luck, and give x64 a try...and remember, if you run into any issues, just ask...we are more than happy to help.

Darkhornet

PS--and as a side note..I can see ALL 8 GB of my RAM  :lolflag:

---

### Post by jimv on 2008-05-01
> **Cap'n Redbeard said:**
> Hi Folks,

Please remember, 1 Gb is a north american term for 100 Mb. 1 Gig is really 1 thousand, NOT 100 Mb.



WTF?

I think you're pretty confused there, mate.  1 gigabyte of RAM = 1024 megabytes.  That's the same everywhere.

If you're talking gigabit vs gigabyte, a bit is 1/8 of a byte, and this a gigabit would technically be 125 megabytes.  But that has nothing to do with RAM.

---

