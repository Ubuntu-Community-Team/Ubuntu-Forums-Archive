---
title: "Third Time's The Charm?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by tentel on 2008-04-30
Hello all,

I've tried installing Ubuntu Gutsy Gibbon twice before on my HP dv6436nr Laptop.

The first time, I tried the 64-bit version (I have an AMD CPU), but I had so many problems it was basically unusable.  ON top of the typical Broadcom junk, a bunch of other things were driving me nuts as well.  I eventually gave up and went back to Vista.

A few months later, I came in for round two.  This time I used the 32-bit version, and everything went great. Aside from having no wireless internet (I tried ndiswrapper and fw-cutter but to no avail) I was very impressed.  I loved the OS, I loved compiz, and I was using the command line so much that within three days I was actually starting to understand what I was typing in.
But I gave up within a week. I just couldn't get online.  No matter what I tried, from posting on here to researching on google till my eyes hurt I just had no success.

However, not long after I had gone back to Vista, I read that there were new native broadcom drivers being used.  I think they were called b43 as opposed to the old BCM43xx (I could be just imagining this though).

Anyways, what are the odds that I'll have better luck with Hardy Heron?
Has anything changed with respect to wireless drivers since Gutsy?


Thanks
-Tim

---

### Post by artir on 2008-04-30
> 
Anyways, what are the odds that I'll have better luck with Hardy Heron?
Has anything changed with respect to wireless drivers since Gutsy?

Yes. They have included new broadcom drivers. Get hardy and try it. It should just work.

---

### Post by ByteJuggler on 2008-04-30
I have an HP laptop, NX6125, not exactly the same as yours then, but it also includes an BCM43xx wireless (lspci lists it as Broadcom Airforce One 54g extreme or somesuch, perhaps you can post the output of your of "sudo lspci" to check/compare.)  

Anyway, the driver in Hardy is still not complete/doesn't deal well with low signal/lots of obstruction situations (which is what I've got).  The default driver would barely get a connection and usually then drops it pretty quickly once its got it (just like Gutsy did for me.)  The very good upside is I've managed to get it to work very well with ndiswrapper.  Very stable now, moreso than it was with Gutsy.  So for practical intents and purposes I can forget about wireless issues now. :)  So perhaps you may be luckier going the NDiswrapper route as well this time!?

Broadly speaking I followed the documentation here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

My specific chipset btw was the  BCM4318 (rev 02) with Pci ID 14e4:4318 (rev 02) 

You must find and post yours with "lspci -n | grep '14e4:43'" as documented above. Also note the Hardy specific comments here and there (in bold.)  But yes, that did work for me.  (You have to make very sure the blacklisting has taken hold/worked otherwise you'll be tearing your hair out, btw.)

---

### Post by tentel on 2008-04-30
That is awesome.

And thank you for the quick reply.


Just two more questions:

I'm planning on dual-booting Vista and Ubuntu.  That is what I did last time.
Is there any way to do that without using the GRUB bootloader?
I'd rather just use the windows one unless anybody can give me reason why I shouldn't.



Also, how should I format the Ubuntu partion?  I forget what the different options are.  I think I used ext3 or something like that last time.  I can't really remember, though I do remember I was confused last time.



Thanks
-Tim

---

### Post by ByteJuggler on 2008-04-30
> **tentel said:**
> That is awesome.

And thank you for the quick reply.


Just two more questions:

I'm planning on dual-booting Vista and Ubuntu.  That is what I did last time.
Is there any way to do that without using the GRUB bootloader?
I'd rather just use the windows one unless anybody can give me reason why I shouldn't.



Also, how should I format the Ubuntu partion?  I forget what the different options are.  I think I used ext3 or something like that last time.  I can't really remember, though I do remember I was confused last time.



Thanks
-Tim

If you want to dual boot and use the Windows boot loader, then I suggest using Wubi.  That also avoids having to repartition your Vista partition at all.  If you want to repartition your disk I would recommend using GRUB simply because it knows about booting multiple operating systems, including Windows.  Windows's boot loader on the other hand isn't especially friendly towards booting anything but Windows.  (But it can be done, if you really really really want to.  It's just not a very standard setup and you'll have less people with experience to go to for help.  I certainly have no idea offhand how to manually set that up.  WUBI is a special case which doesn't boot into a seperate partition, and in any case it's all automatic so nothing to worry about... )

---

### Post by tentel on 2008-04-30
I'll give this stuff a try as soon as possible.
Finals week is coming up next week so I'm not usre how soon i'll be able to work on this, but I'm sure I'll be posting questions/results soon.

Thanks for the feedback everyone.
-Tim

---

### Post by tentel on 2008-04-30
> **ByteJuggler said:**
> If you want to dual boot and use the Windows boot loader, then I suggest using Wubi.  That also avoids having to repartition your Vista partition at all.  If you want to repartition your disk I would recommend using GRUB simply because it knows about booting multiple operating systems, including Windows.  Windows's boot loader on the other hand isn't especially friendly towards booting anything but Windows.  (But it can be done, if you really really really want to.  It's just not a very standard setup and you'll have less people with experience to go to for help.  I certainly have no idea offhand how to manually set that up.  WUBI is a special case which doesn't boot into a seperate partition, and in any case it's all automatic so nothing to worry about... )


I am planning on using WUBI, just to try it out, but I do plan on installing it on it's own partition eventually.

That is a good point about the Windows bootloader, I'll just stick with GRUB.

---

### Post by ByteJuggler on 2008-04-30
> **tentel said:**
> I'll give this stuff a try as soon as possible.
Finals week is coming up next week so I'm not usre how soon i'll be able to work on this, but I'm sure I'll be posting questions/results soon.

Thanks for the feedback everyone.
-Tim

By the way, I'm running *64bit *Hardy on my laptop, using Ndiswrapper... I originally expected that to be problematic, but even that's fine... cool huh?

---

### Post by tentel on 2008-04-30
I'll probably give the 64-bit version a try.
I have AMD so why not?

---

