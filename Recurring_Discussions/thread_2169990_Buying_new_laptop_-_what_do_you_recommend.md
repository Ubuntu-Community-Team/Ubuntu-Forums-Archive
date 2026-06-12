---
title: "Buying new laptop - what do you recommend?"
date: 2013-08-24
forum: Recurring Discussions
---

### Post by PopsTheSailor on 2013-08-24
I currently have a Toshiba laptop and have had nothing but problems with it's ability to connect and stay connected to my wireless network at home. I dual boot on it and under Windows 7 it works flawlessly so it is a problem with Ubuntu. It worked great until I went from 11.xx to 12.xx and 13.xx. For other reasons (so no need to try and fix my problem), I'm going to buy a new laptop and wanted to know who has bought one in the last month or so that they could recommend? With technology changing so fast, if you haven't made your purchase recently then I probably wouldn't be able to find it so really looking for ones that are relatively new.

---

### Post by PopsTheSailor on 2013-09-06
Bump.

Hasn't anyone bought a laptop lately that has good wireless connectivity?

---

### Post by Bucky Ball on 2013-09-06
*Thread moved to **Recurring Discussions**.*

Hi pops2. There is a ton of info out there about compatibility and a lot of threads on this already. 

If you want to fix the wireless on your current laptop try posting back in ***Networking & Wireless*** and provide machine model and wireless card. Give the output of these commands from a terminal:

sudo lshw -C network
iwconfig

Give as much info about what you've tried and what is happening as you can muster. That will get things off to a good start. (Have a look at the last link in my signature for clues about posting a support thread.) Good luck. 

PS: I'm running a Toshiba Satellite Pro L510. Faultless. That obviously doesn't help you much but Toshiba is generally a great choice. Your problem is rather down to the wireless setup and that's probably fixable (although I know you've been trying). Let's try putting a few heads together on it. Post a link to the new thread back here if you post one. ;)

---

### Post by craig10x on 2013-09-06
I've found that Toshibas with intel processors run ubuntu really fine....my latest Toshiba 17" laptop (which is my desktop) has an intel i3core and works great...

---

### Post by Bucky Ball on 2013-09-07
> **craig10x said:**
> I've found that Toshibas with intel processors run ubuntu really fine....my latest Toshiba 17" laptop (which is my desktop) has an intel i3core and works great...

Snap. Mine a 14'' but same Intel i3. All good. Don't think processor really an issue, though. My last laptop, a HP, used AMD and that also ran faultlessly.

---

### Post by PopsTheSailor on 2013-09-07
Yea, I'm not worried about the processor. I'm have wireless issues today and want to avoid that in the future.

---

### Post by craig10x on 2013-09-07
Oh yeah...forgot to mention that mine also has the intel graphics...it's all intel...lol

But yeah, Toshibas and Hps with amd's do fine also...though i suspect the amds usually need the proprietary driver for best performance...
Intel is unusual in that the open source and proprietary is identical... therefore, ubuntu offers no proprietary driver for intel because there is no difference...

I have found Toshibas also to be very reliable...the only thing i was too crazy about in them in the past was the keyboards which did not have the best typing feel...however, in more recent years they went to the flat (mac style) keys which i find great to use..Of course, these days i think most brands of laptops use them now also...

The wireless aspect i cannot comment on because i only use the ethernet connection directly to my cable internet...although the drop down menu from the top of my ubuntu panels shows wireless is turned on and i can see various wireless networks in my area on it..if that means anything...;)

---

### Post by Bucky Ball on 2013-09-07
As I mentioned previously:

> **Bucky Ball said:**
> 
If you want to fix the wireless on your current laptop try posting back in ***Networking & Wireless***. Give the output of these commands from a terminal:

sudo lshw -C network
iwconfig


If you haven't tried there already, it's worth it as more than one head is better than one ... ;)

Basically, from what I can gather, you are really looking to buy a new laptop with a wireless card that works out of the box. It seems a bit drastic if the only reason is you can't get the wireless working in this one. If you haven't posted in the appropriate section for help then it's an expensive fix. Of course, there's no guaranteeing we can fix, but impossible without some detail.

Anything with Intel wireless should/will be fine and most Broadcom and Realtek, which gives you a huge range of options. Avoid anything with wireless that was released five minutes ago, though, or anything totally exotic and extremely new. They can be problematic.

Out of curiousity, have you connected to the ethernet via a cable with the machine you are having wireless trouble with and checked additional drivers or done an update?

Anyway, that is for another thread in the appropriate sub-forum and I'll have to moderate myself for getting off topic if I keep asking about that! Might be a good idea if you have a research for a machine that suits your requirements and find out what wireless it has then post that here. We can probably help you find out whether that is going to work ok.

---

### Post by PopsTheSailor on 2013-09-07
Nope, it's not the only reason I need to buy a new laptop. Therefore, as you mentioned, I just want to avoid wireless issues so I'm looking for recommendations for current model laptops that don't have problems with the wireless.

---

### Post by kaldor on 2013-09-07
Get a ThinkPad T430 (or T430s) and select the Intel wireless option when ordering. Great machine for Linux overall.

Link: [http://shop.lenovo.com/us/en/laptops/thinkpad/t-series/t430/](http://shop.lenovo.com/us/en/laptops/thinkpad/t-series/t430/)

I made the mistake of not selecting the Intel wireless card (very well-supported), but everything else works flawlessly. If you go this route I recommend selecting the i5 processor and the 1600x900 display.

---

### Post by tajreed on 2013-09-08
What about Touch Screen vs. none Touch.

---

