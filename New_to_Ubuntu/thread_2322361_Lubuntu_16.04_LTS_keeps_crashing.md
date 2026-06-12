---
title: "Lubuntu 16.04 LTS keeps crashing"
date: 2016-04-27
forum: New to Ubuntu
---

### Post by q123q on 2016-04-27
Hi,

newly installed Lubuntu 16.04 LTS keeps crashing. Not just the op.system.More often the Firefox is crashing too.I was using Google Maps,and Street View, and it was fine. But when I open up Facebook it keeps crasing after 2-3 minutes of use,and sometimes the whole op.system crashes.
Cups not working,and lot of other issues discovered by other users.Looks the 16.04 has lot of bugs.
Any idea to solve it?

Processor        : 2x AMD Processor model unknown
Memory        : 761MB (428MB used)
Operating System        : Ubuntu 16.04 LTS
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA ATI SB

---

### Post by oldrocker99 on 2016-04-27
768 MB is pretty low for RAM.

And this forum, as it says on the top, this sub-forum is for chat, not support &#8211; hence the name. If you need technical help, please post in an appropriate support sub-forum.

Please do.

---

### Post by DuckHook on 2016-04-28
*Your thread has been moved to **New to Ubuntu** as a forum that is more relevant to your issue.*

---

### Post by q123q on 2016-04-28
> **oldrocker99 said:**
> 768 MB is pretty low for RAM.(...)

I checked the memory in the PC, and it has one 1024MB module in it. Checked the BIOS,and it says it has 1024 MB RAM, but Lubuntu says 761MB.
What is wrong?

---

### Post by RobGoss on 2016-04-28
Using a low amount of Ram will have a negative affects on your system. I'm running 16.04 with no bugs so I would have to disagree with you on that

These day the Linux distribution are using more resources so it would be a good ideas to have enough Ram to run the operating system and 16.04 requires more Ram then what you have so if you want your system to perform better you might have to increase the Ram.

---

### Post by mörgæs on 2016-04-28
> **RobGoss said:**
> 16.04 requires more Ram then what you have so if you want your system to perform better you might have to increase the Ram.

No, Lubuntu itself (without browsers) runs fine with much less than 700 MB of memory. I would expect the limit to be around 256.

---

### Post by RobGoss on 2016-04-28
Yes you are correct I was reading something else Lubuntu does use less Ram and for the most part should run fairly well with that amount I would think

Something else might be causing it to crash..

---

### Post by q123q on 2016-04-28
News: I took the 1 x 1 GB Ram out, and placed it to the other slot,next to where it was.Now seems to be okay.
I've had the same problem with an another desktop PC:after 2-3 years it started crashing in the first 30 min of use.I took the 2 x 1 GB Ram out,and placed back.It was fine for an another 2 years.After that,it started crashing again, on the same Win XP. I took the memories out, and back.Now it's working fine again.
I suspect the same problem with this AMD desktop PC too. Like mörgæs said:'Lubuntu itself (without browsers) runs fine with much less than 700 MB of memory. I would expect the limit to be around 256.'
The 768 MB Ram can not be the cause of the crashing.
See what happens in the next few days.

---

### Post by DuckHook on 2016-04-28
What you have just described points very heavily to a hardware problem. The removal and re-seating of the memory almost clinches it. Nothing wrong with the OS, but either a faulty MB or RAM module.

If nothing further OS-related happens, then please mark thread *solved* so that others can benefit from your solution.

If you wish to troubleshoot a HW problem, I am sure the members in the *Hardware* forum would be happy to help you.

Good luck and Happy Ubuntuing!

---

### Post by q123q on 2016-04-28
Yes, it's very likely a hardware problem.I bought this PC to my mother-in-law in a 2.hand PC store.So I had no prev.experience about it. Some friends installed Win 7 on it, but that is really too much for this 768 MB Ram machine.She said 'some problems' about the Win 7, but I thought that, this is because the low memory.But those could be also crashes due to the memory or memory slot fault.
I'll post how it's going after few days.
Thanks.

---

### Post by Rocky_Bennett on 2016-04-29
I have an Intel i5 4690 with 16 gb of RAM and Ubuntu 16.04 has been crashing on me regularly.

---

### Post by q123q on 2016-04-30
> **Rocky_Bennett said:**
> I have an Intel i5 4690 with 16 gb of RAM and Ubuntu 16.04 has been crashing on me regularly.

That PC looks okay, but I have installed the same Lubuntu 16.04 to my father's desktop PC, and that keeps freezing.It was okay with 14.04

---

### Post by mörgæs on 2016-05-01
If we need to take a look at that please post all hardware details.

---

### Post by maglin2 on 2016-05-02
> **Rocky_Bennett said:**
> I have an Intel i5 4690 with 16 gb of RAM and Ubuntu 16.04 has been crashing on me regularly.

If you want to pursue this you'd probably be better to start your own thread, but just a thought:

I updated to 15.10 to 16.04 and had a stable system. There were still bits of both present though (eg two software centres), so I decided to do a fresh install of 16.04. This did not prove stable until I remembered to apply the proprietary intel driver. Since then all is stable (fingers crossed). (I think this driver may have been applied by default in 15.10, but I can't be sure).

Edit - this was wishful thinking. Instability (occasional freezes) of 16.04 ongoing.

---

### Post by q123q on 2016-05-06
My father's PC had a 32bit edition 16.04 on it(it's a 64 bit PC).Yesterday I managed to connect to it via VNC. The Firefox just disappeared during use.No crash msg at all.After boot up there was an error msg.The 'before boot up' memory test gave no errors.So I just installed Mint 17.3 MATE 64bit on it.
See how it goes.

---

### Post by sampsung on 2016-09-07
I've got troubles too with Lubuntu 16.04. Firefox keeps crashing and twice the operating systems has been stuck. I already completly reinstalled the Firefox and checked that there is no broken packets. My laptop is a Thinkpad X201s with 8 gb of ddr3 memory, 256 Gb ssd and i7 processor. I guess that this machine is not powerful enough to run Linux Lubuntu and I should just buy Windows 10 (wich I hate).

---

### Post by mörgæs on 2016-09-07
It's certainly powerful enough. 

First I suggest that you monitor exactly what triggers a crash. Firefox, Chromium, Midori, other browsers... 

Please post when you have more details.

---

