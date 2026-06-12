---
title: "Fresh install of Ubuntu, can't find drivers"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by mitchelvostrez on 2014-07-18
So I've just installed Ubuntu on my desktop, and I'm having a horrible time trying to get drivers. I have a three screen setup with an R9 290x, and when I try to go from one screen to the other, the mouse gets stuck on the edge of a screen for a second, and it's beginning to annoy me. I also can't connect to the internet through my Bigfoot Killer network card. I feel like if I can get those two issues fixed, I can get the rest on my own. Any ideas/advice?

---

### Post by TheFu on 2014-07-18
Generally, it is best to select only hardware that is supported directly by the linux kernel.  If you need to get driver software manually, that will likely be a thorn for the rest of the time you run any version of linux.  Even if the vendor provides a driver when you purchase the hardware, they won't usually maintain it for the life of the device - I've been burned by printers, RAID cards, USB devices, network cards, mice, and video cards over the years.

So ... the easiest answer is to only buy hardware where driver installation happens automatically - unless you want to be a driver maintainer yourself.  Not good for someone who is an "absolute beginner."

[http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) is related to the NIC you have. Without more data on the real issue, we cannot help. Is it driver, local LAN, WAN or DNS as the issue?  BTW, it is best to post 1 question per thread so that the different experts will respond.

But you are stuck today and need to determine the best drivers.  Well, .... [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) may be helpful. It provides commands and tips to track down the chip used. Hope it helps.

Linux drivers really shouldn't be something you manually have to install and configure.  That means there is a failure along the way if that happens. That failure can be "me", the maker (not supporting Linux well), or 1 specific distro choice. It is great when you just get the right hardware, connect it up and everything "just works."  That happens here because I'm careful about HW selection now - been burned too many times.  Saving $10 on a card isn't worth the 50 hrs of driver searching/maintenance that may come. It took me a long time to learn that - these days I get Intel PRO/1000 NICs - nothing else.  Specific printers which are known to be well supported, and low-mid-level nvidia GPUs, if the Intel GPU isn't built in.

---

### Post by Mark Phelps on 2014-07-18
For the R9, Additional Drivers should offer a proprietary AMD driver.  IF it does, you can install that, and by installing this way, NOT from downloading drivers from AMD, when you later do updates, you won't have to regenerate the drivers.

As to other drivers, it's not a simple matter of searching because very few hardware manufacturers actually provide Linux drivers.  Anything that doesn't work up front is most likely NOT going to work.  Sorry, but lack of drivers is a known Linux limitation.

---

### Post by Bucky Ball on 2014-07-18
> **TheFu said:**
> BTW, it is best to post 1 question per thread so that the different experts will respond.



^^^
This. 

Welcome. Perhaps edit one of the support requests out and put it in a new thread with a descriptive title (the networking issue will have more success in ***Networking & Wireless***). In that thread, please include the output of:

```
sudo lshw -C nework
```

... to get things started, along with the Ubuntu release/flavour you are using. Feel free to provide a link here. After that, I can move the screen issue to ***Multimedia & Video*** and tweak the title to suit. Good luck.

---

