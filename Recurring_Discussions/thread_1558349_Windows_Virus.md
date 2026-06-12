---
title: "Windows Virus"
date: 2010-08-22
forum: Recurring Discussions
---

### Post by ki4jgt on 2010-08-22
Hey guys, I know this isn't the place, but I didn't know where else to ask this than to the Ubuntu community. (LOL I love you guys, you're family) :-)

Anyway, I was wondering if there was ever a windows virus written specifically to take out another virus, and what the penalties (By Law) were for someone who wrote it?

---

### Post by Ryan Dwyer on 2010-08-22
It's called antivirus software. It runs constantly without your permission. It either doesn't have an option to close it or if it does then it requires a password. When you kill the task it restarts. And it decreases your computer's performance while it scans without your consent.

Sounds like a perfect definition of a virus to me.

---

### Post by ki4jgt on 2010-08-22
With the exception that you're the one who installed it!

---

### Post by sikander3786 on 2010-08-22
> **Ryan Dwyer said:**
> It's called antivirus software. It runs constantly without your permission. It either doesn't have an option to close it or if it does then it requires a password. When you kill the task it restarts. And it decreases your computer's performance while it scans without your consent.

Sounds like a perfect definition of a virus to me.

But Antivirus runs with your permission while a virus doesn't need any permissions. And all antivirus don't ask for a password on exit.

I haven't heard of a virus created to remove another virus.

Not a support thread I guess. Think this should be moved to the cafe. I have grabbed a bean though :lolflag:

---

### Post by Elfy on 2010-08-22
moved to recurring

---

### Post by Ctrl-Alt-F1 on 2010-08-22
> **Ryan Dwyer said:**
> It's called antivirus software. It runs constantly without your permission.

No.

> **Ryan Dwyer said:**
> It either doesn't have an option to close it or if it does then it requires a password.

No.

> **Ryan Dwyer said:**
> while it scans without your consent.


No.

> **Ryan Dwyer said:**
> 
Sounds like a perfect definition of a virus to me.

No.

:popcorn:

---

### Post by d3v1150m471c on 2010-08-22
> **ctrl-alt-f1 said:**
> no.



No.



No.



No.

:popcorn:

+1

---

### Post by Ryan Dwyer on 2010-08-22
I realise not all antivirus software is like that, but I've experienced antivirus software that works exactly as I described. It was very annoying.

---

### Post by ki4jgt on 2010-08-22
Still, I've never ran accross any like that, except Synaptic, The worst part was it required a password to uninstall it, and I had to go online to find it of all things

---

### Post by ki4jgt on 2010-08-22
And really??? Recurring??? How many times has this topic come up? If I may ask.

---

### Post by Calash on 2010-08-23
A while back we got hit with a nasty worm..the name escapes me but it was at least 3 years ago.

The worm was bad but manageable.  Then we got hit with a second worm.  Apparently somebody designed a worm that used the same exploit as the first but with better (ie, faster) network scanning and a payload that would try to patch the system it was on.

The "helpful" worm caused so much network traffic that it had our company offline for a good day before they got it all filtered.

Outside of that I have read about a few other "helpful" viruses that used known exploits to patch systems.

I can not speak on penalties but personally I would treat both as the same crime.  The so called "helpful" virus caused us more damage than what it was trying to stop.

---

### Post by ki4jgt on 2010-08-24
Nice!! :-) Love it! Wonder if it wasn't so network consuming, if you'd feel the same way. So how far behind the original was the helper worm, (how long did it take you to get infected by the second virus after you were infected with the first one?

---

### Post by Calash on 2010-08-24
Both hit our network in the same day. 

The fixer worm was Nachi

[http://vil.nai.com/vil/content/v_100559.htm](http://vil.nai.com/vil/content/v_100559.htm)

> 
Intentions of the worm 
This worm spreads by exploiting a hole in Microsoft Windows. It instructs a remote target system to download and execute the worm from the infected host. Once running, the worm terminates and deletes the W32/Lovsan.worm.a process and applies the Microsoft patch to prevent other threats from infecting the system through the same hole. When the system clock reaches Jan 1, 2004, the worm will delete itself upon execution.


We had more issues from this thank the lovesan worm it was trying to fix.  In part I believe it was due to it hammering our proxy server and killing any internet out of the network.


Edit:  My god...that was in 2004?!?!  I have been at this place way too long..all the years just blend together now :)

---

### Post by betrunkenaffe on 2010-08-24
Did a research project on it back in university. The main concerns have already been displayed by one such implementation. By exploiting the same means of transportation, only infect-able machines will be targeted however the effect on the networks and the machines will be very similar in the short run.

That "fix" looks to have been poorly designed as it likely used a lot of network traffic to carry it's payload.

---

### Post by Calash on 2010-08-24
> **betrunkenaffe said:**
> Did a research project on it back in university. The main concerns have already been displayed by one such implementation. By exploiting the same means of transportation, only infect-able machines will be targeted however the effect on the networks and the machines will be very similar in the short run.

That "fix" looks to have been poorly designed as it likely used a lot of network traffic to carry it's payload.

It actually caused more network traffic.  In part it was due to having a more aggressive scanning, along with needing to download the payload from Microsoft.  The act of it scanning also caused RPC crashes on some systems forcing sporadic rebooting.  The resulting slowness prevented us from being able to download any repair utilities for ether virus.

As I recall I spent a couple of late nights going system to system with a USB key to get things cleaned up.

---

### Post by ki4jgt on 2010-08-24
And that's when you went to linux! LOL J/K, that's about the time I was running my first linux sys though. Loved that fact that it was different, and that I could do things that most windows users couldn't even dream of

---

### Post by Calash on 2010-08-24
> **ki4jgt said:**
> And that's when you went to linux! LOL J/K, that's about the time I was running my first linux sys though. Loved that fact that it was different, and that I could do things that most windows users couldn't even dream of

LOL

Actually I went to Linux in 2008 when I built my Mythbuntu box (8.04).  I have been using it as my primary desktop since.  Last year I moved my work computer to Ubuntu and have 2 virtual machines for Windows Desktop and testing.

My job is primarily Windows support so I can never get away from it, even if it drives me crazy at times :)

---

### Post by ki4jgt on 2010-08-24
Been there, done that!

---

