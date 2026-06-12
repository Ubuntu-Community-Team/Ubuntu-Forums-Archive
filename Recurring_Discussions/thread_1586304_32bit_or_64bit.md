---
title: "32bit or 64bit"
date: 2010-10-01
forum: Recurring Discussions
---

### Post by jmdlcar on 2010-10-01
I have an **AMD Athlon(tm) 64 X2 Dual Core Processor 4400+** and I'm running the Ubuntu 10.04.1 64bit but if I change it to the 32bit version will I see much of a change or not.

---

### Post by CharlesA on 2010-10-01
I doubt you'll see much a difference unless you have more then 4GB of RAM, but that's not a problem since Ubuntu will install the PAE kernel if you are connected to the internet.

---

### Post by mikewhatever on 2010-10-01
It depends. If you encode video and audio a lot, 64bit is a better choice. How much RAM do you have?

---

### Post by bark50 on 2010-10-01
I initially installed 64 bit 10.04 when it came out.  A couple months later I installed 32 bit because I was tired of flash problems.  With 32 bit, flash is fine, and I notice no differences in performance for the simple stuff I do like web surfing, word processing, and video conversion.

---

### Post by DougieFresh4U on 2010-10-01
Really? Again!
Search function is your best friend here at the forum :)

---

### Post by formaldehyde_spoon on 2010-10-01
> **jmdlcar said:**
> I have an **AMD Athlon(tm) 64 X2 Dual Core Processor 4400+** and I'm running the Ubuntu 10.04.1 64bit but if I change it to the 32bit version will I see much of a change or not.

You may see a drop in performance, depending on what you do.
Also, if you have 4+GB RAM you will have to use PAE, which is *another* performance drop compared to 64 bit.  > **bark50 said:**
> I initially installed 64 bit 10.04 when it came out.  A couple months later I installed 32 bit because I was tired of flash problems.  With 32 bit, flash is fine, and I notice no differences in performance for the simple stuff I do like web surfing, word processing, and video conversion.

You should have been using 64 bit Flash then. 32 bit Flash is a pain to use with 64 bit Ubuntu.  There is a new 64 bit Flash out, BTW.
If you aren't noticing a difference for video conversion you aren't paying close enough attention.

---

### Post by bark50 on 2010-10-01
> **formaldehyde_spoon said:**
>  

You should have been using 64 bit Flash then. 32 bit Flash is a pain to use with 64 bit Ubuntu.  There is a new 64 bit Flash out, BTW.
If you aren't noticing a difference for video conversion you aren't paying close enough attention.

Last April and May I was a regular lurker in the frequent my-64-bit-flash-doesn't-work threads here on the forums.  I can't remember all the fixes I tried, but I either ended up with a flash that played YouTube and not Hulu or played Hulu and not YouTube or would play neither.  I have hope, though, and I'll give 64-bit Ubuntu another dance when 10.10 is released.  

Yeah, that no difference in video conversion puzzled me.  With both 32-bit and 64-bit Ubuntu my system monitor showed 100% CPU usage and around a gig of memory being used.  I have a low-end AMD Phenom tri-core processor and 4 gig of memory.  Maybe it's my processor...??  Or maybe it's the program I use.  It's Handbrake, and I really like it.

---

### Post by formaldehyde_spoon on 2010-10-02
> **bark50 said:**
> Last April and May I was a regular lurker in the frequent my-64-bit-flash-doesn't-work threads here on the forums.  I can't remember all the fixes I tried, but I either ended up with a flash that played YouTube and not Hulu or played Hulu and not YouTube or would play neither.  I have hope, though, and I'll give 64-bit Ubuntu another dance when 10.10 is released.  

Yeah, that no difference in video conversion puzzled me.  With both 32-bit and 64-bit Ubuntu my system monitor showed 100% CPU usage and around a gig of memory being used.  I have a low-end AMD Phenom tri-core processor and 4 gig of memory.  Maybe it's my processor...??  Or maybe it's the program I use.  It's Handbrake, and I really like it.

The current(new) 64 bit Flash works fine with Hulu and Youtube.
Of course you'll still have 100% cpu usage with 64 bit: it's still trying to get the job done as quickly as possible.  64 bit will complete faster though.

---

### Post by coolbrook on 2010-10-02
I'll likely do a clean install with the 32-bit version now that the Meerkat RC is available.

---

### Post by formaldehyde_spoon on 2010-10-02
> **coolbrook said:**
> I'll likely do a clean install with the 32-bit version now that the Meerkat RC is available.

Why? If you have 64 bit hardware use a 64 bit OS.

---

### Post by NikoC on 2010-10-02
I have a 64-bit laptop so I installed Lucid 64-bit and haven't had any problems so far! It's a PC that I use daily in the office, so I can't really afford to play around with an unproductive system.

Also the 4GB of RAM was supported without any extra compiling or installing.

So I'm with formaldehyde_spoon on this one!

---

### Post by cjv8888 on 2010-10-02
I agree.  You should use 64 bit system for a 64 bit computer.  As for flash, the new 64 bit Adobe flash "square" plug in has been excellent with zero problem so far.

---

### Post by uRock on 2010-10-02
> **formaldehyde_spoon said:**
> Why? If you have 64 bit hardware use a 64 bit OS.
Because not all 32bit software runs on 64bit Linux and because he/she wants to. It doesn't hurt anything and flash doesn't eat the CPU with 32bit.

Moved to Recurring Discussions. This topic has been covered many of times lately.

---

### Post by mikewhatever on 2010-10-02
I use a 32bit OS on a 64bit machine because of Skype and Flash, none of which has stable 64bit versions. As for the testing Flash 64bit and Skype 64 packaged with 32 bit libraries, both don't work very well.

---

### Post by formaldehyde_spoon on 2010-10-02
> **mikewhatever said:**
> I use a 32bit OS on a 64bit machine because of Skype and Flash, none of which has stable 64bit versions. As for the testing Flash 64bit and Skype 64 packaged with 32 bit libraries, both don't work very well.

...
Flash for 64 bit: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) 
Skype for 64 bit: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/) 
Both rock solid for me.  

> **uRock said:**
> Because not all 32bit software runs on 64bit Linux And yet many of us manage to live very happily with 64 bit...strange.
Stuff that won't run on 64 bit you can count on one hand.  Unless this person happens to be someone who uses that software your point is irrelevant.  > and because he/she wants to.  Thank you for your insight.  I'm sure the person in question will also want to thank you for your assistance.  >  It doesn't hurt anything and flash doesn't eat the CPU with 32bit.
... No-one said it hurts anything (besides performance), and 64 bit also ''doesn't hurt anything''.
64 bit Flash doesn't ''eat the CPU'' either - not that you'd know that, because as you've said time and time again, you don't use it.

---

### Post by mikewhatever on 2010-10-02
> **formaldehyde_spoon said:**
> ...
Flash for 64 bit: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) 
Skype for 64 bit: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/) 
Both rock solid for me.  



Yeah, so what?
Should I use 64bit because it works for you? I don't think so.

---

### Post by formaldehyde_spoon on 2010-10-02
> **mikewhatever said:**
> Yeah, so what?
Should I use 64bit because it works for you? I don't think so.

? Is that what I said?

---

