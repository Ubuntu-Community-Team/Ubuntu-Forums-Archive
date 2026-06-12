---
title: "32bit or 64bit ubuntu 10.04 on Lenovo Thinkpad SL510?"
date: 2010-05-01
forum: Recurring Discussions
---

### Post by vickoxy on 2010-05-01
Hi,
need a little help here. I am probably going to buy this thinkpad sl510:

&#8226; Core 2 Duo T6570 2x 2.10GHz 
&#8226; 2048MB &#8226; 250GB &#8226; DVD+/-RW DL 
&#8226; Intel GMA X4500HD (IGP) max.384MB shared memory 
&#8226; 4x USB 2.0/Gb LAN/WLAN 802.11abgn/Bluetooth/eSATA 
&#8226; HDMI 
&#8226; ExpressCard/54 Slot 
&#8226; 7in1 Card Reader 
&#8226; Webcam (2.0 Megapixel) 
&#8226; 15.6" WXGA non-glare LED TFT (1366x768)

and don´t know if i should install 32bit or 64bit Ubuntu? I am no power user-internet, word processor, little bit of photography and videos...

1) should i install 64bit version (pros and cons)?
2) if there is only 32bit version of some apps. do they work on 64bit system?
3) does 64bit system requires more power (cpu/ram usage, increasing temp...)?


Thanks

---

### Post by P4man on 2010-05-01
This is asked quite often, you may want to search for it n this forum to get lengthy threads with all details.

The short version: go ahead and install 64 bit version. Its a bit faster, although it does require marginally more ram (but you have plenty for ubuntu). 

Almost all linux software is available as both 32 and 64 bit, and if you use the repositories you need not even worry about it. I keep forgetting which version I run, I just install the software I want and its taken care off automatically. And yes, you can run 32 bit apps on 64 bit OS if you should have an odd/old compiled 32 bit only app.

---

### Post by vickoxy on 2010-05-01
> **P4man said:**
> This is asked quite often, you may want to search for it n this forum to get lengthy threads with all details.

The short version: go ahead and install 64 bit version. Its a bit faster, although it does require marginally more ram (but you have plenty for ubuntu). 

Almost all linux software is available as both 32 and 64 bit, and if you use the repositories you need not even worry about it. I keep forgetting which version I run, I just install the software I want and its taken care off automatically. And yes, you can run 32 bit apps on 64 bit OS if you should have an odd/old compiled 32 bit only app.

Thanks-i will do it. Still one question-with hardware compatibility shouldn´t be problems?

---

### Post by P4man on 2010-05-01
best way to find out is just run the livecd. I have no way of knowing if your wifi, soundcard, webcam and what not will work. I do think the intel 4500 gpu isnt the best supported, but try it out.

---

### Post by Jakiejake on 2010-05-21
I'm Just about to download the 64 bit version

---

### Post by vickoxy on 2010-05-21
Sorry, i forgot to respond. I installed 64bit and it works really fast, smooth and i see no need to install 32bit.

The only annoying thing is that if use my headphones, i need to manually disable (in audio settings) internal laptop speakers, and than to activate them again. But i think thas this could be common lucid issue. But, important is that everything works out of the box: bluetooth, wifi, suspend... i had never better linux machine :guitar:

---

### Post by Jakiejake on 2010-05-21
> **vickoxy said:**
> Sorry, i forgot to respond. I installed 64bit and it works really fast, smooth and i see no need to install 32bit.

The only annoying thing is that if use my headphones, i need to manually disable (in audio settings) internal laptop speakers, and than to activate them again. But i think thas this could be common lucid issue. But, important is that everything works out of the box: bluetooth, wifi, suspend... i had never better linux machine :guitar:

Same Here,
Running It Now
It's Great worth the switch and most programs are available

---

### Post by philinux on 2010-05-21
Moved to Recurring Discussions.

---

### Post by vickoxy on 2010-05-25
Wanted to ask-is there big difference in heat emissions between 32bit and 64bit. 
Does anyone knows if/how much more power consumes/heat emissions has 64bit system?

---

### Post by vickoxy on 2010-05-29
bump

---

### Post by Shining Arcanine on 2010-05-29
> **vickoxy said:**
> Wanted to ask-is there big difference in heat emissions between 32bit and 64bit. 
Does anyone knows if/how much more power consumes/heat emissions has 64bit system?
The differences are insignificant. Any other possible consideration (e.g. operating system) would make a far greater difference in that area than the instruction set used will.

---

### Post by vickoxy on 2010-05-29
Well, but i just want to stay with linux... No idea what distro could improve things....

---

### Post by hedgeborn on 2010-08-04
What about the fact that Adobe has pulled the 64-bit Flash driver for Linux?

I would think that might be a factor for more than a few people.

I hear people saying the 64-bit version works fine, but when I do a little investigating, it seems otherwise and now Canonical themselves is not recommending the 64-bit version of Ubuntu for general use (see their website)

Personally, I'm going with the 32-bit version. I need Flash to work reliably and I will have 4 gb of RAM to work with. Really not going to make a big difference for me or for the average user. I'd rather know things are going to work as well as possible then to go with 64-bit which Canonical is even apprehensive about recommending.

---

### Post by _h_ on 2010-08-04
> **hedgeborn said:**
> What about the fact that Adobe has pulled the 64-bit Flash driver for Linux?

They are still developing it, and should work fully in the next major update of Flash.

---

### Post by Paqman on 2010-08-04
> **hedgeborn said:**
> I need Flash to work reliably

I think the supposed dodginess of Flash on 64-bit has been *vastly* overstated. I can honestly say Flash performance just isn't an issue on my 64-bit machine.

---

### Post by _h_ on 2010-08-04
> **Paqman said:**
> I think the supposed dodginess of Flash on 64-bit has been *vastly* overstated. I can honestly say Flash performance just isn't an issue on my 64-bit machine.

Have to agree here. 64bit flash works fine on my 64bit ubuntu. 1 out of like 30 videos it will be buggy, but that's not at all bad.

---

### Post by SunnyRabbiera on 2010-08-04
I say use 32bit, though it is a known fact that linux is better at 64bit then any other OS right now

---

### Post by pinguy on 2010-08-05
> **Paqman said:**
> I think the supposed dodginess of Flash on 64-bit has been *vastly* overstated. I can honestly say Flash performance just isn't an issue on my 64-bit machine.

I couldn't agree more.

---

### Post by bigseb on 2010-08-05
Go x64.

---

### Post by hedgeborn on 2010-08-17
Aren't there other issues (problems) associated with 64-bit?

I was under the impression that some apps won't work well with it, it may break things etc.

Seems strange that Canonical themselves weren't recommending it for "regular desktop use" yet everyone who's running it says it works great.

---

### Post by coady on 2010-08-20
I've had the 64 bit version of Lucid installed on an R500 Thinkpad for about a week now... and I can't find anything that's not working. Its working like a dream...!

---

