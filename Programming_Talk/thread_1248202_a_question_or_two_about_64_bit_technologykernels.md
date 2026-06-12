---
title: "a question or two about 64 bit technology/kernels"
date: 2009-08-23
forum: Programming Talk
---

### Post by cooltd825 on 2009-08-23
Okay, so I've recently been given an older Mac with Jaguar (1.33 GHz is *slow* in a laptop now?? :) ) and the operating system has actually grown onto me.  Yes I know, shoot me now.  But it got me attached, and I got a used but still pretty recent iMac at a very good price.  At just under a year old, this computer supposedly uses the "full potential of 64 bit computing" through Leopard.  

Coming from a Windows/Linux background, I was shocked at how seamless the move from 32 bit to 64 bit went.  No driver issues or anything!  Supposedly.  After doing some snooping on my own iMac I realized I wasn't, in fact, running a 64 bit operating system at all.   Leopard has 64 bit apps, and my computer has a 64 bit processor, but the kernel itself is still only running 32 bit.  I'd have to install a custom (and to Apple, illegal) kernel just to be able to use my processor's 64 bit processing!  Now that Snow Leopard is due for release extremely soon, I've been reading that your system won't even boot into a 64 bit kernel unless it's "forced" to, if you're fortunate enough not to have a MacBook.  The only thing I can think of that would literally need 64 bit computing is if an application needed more than 4 GB of memory, without including the obvious advantages having a pure 64 bit system/hardware would bring.  

But this brings me to my main question..  Apple tries to cover this up by saying along the lines of, "Oh having a 64 bit kernel wouldn't be useful anyway.  It would be exactly the same as 32 bits".  As I understand how a processor can run on 64 bit technology, and an application written for it can take advantage of that, I don't even begin to understand how the system kernel deals with everything.  If I'm correct, a 32 bit kernel can convert a 64 bit application's data into 32 bits for the processor (even if the processor is AMD64), but it's not nearly as fast as using both with a 64 bit kernel, right?  Is Apple right in saying a 32 bit kernel would be the same to the end-user as running a 64 bit kernel, or are they really so understaffed and lazy that they can't write drivers for their own hardware that can support a truly 64 bit operating system?

If anyone has comments, insight, or wants to plain out yell at me for rambling on, by all means go ahead.  Thanks for helping out!

---

### Post by TheStatsMan on 2009-08-24
My c++ code runs much quicker on 64 bit ubuntu that on 32 bit ubuntu. I haven't compared times from other languages. 64 bit also allows you to see much more ram. I am not sure why they don't use 64 bit but it could be related to an experience that a guy at work had. He tried running 64 bit ubuntu on his mac and had problems with overheating where it would just shut down. I think I remember him telling me that this seemed to be a standard problem. Google may help answer the question. You would also expect a mac to run smoothly out of the box because it only has to work for the small range of computers they put together. Ubuntu and Windows have to run on any number of configurations.

---

