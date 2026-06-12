---
title: "High fps, smooth gameplay, but ungodly lag"
date: 2015-09-26
forum: New to Ubuntu
---

### Post by pdickerson01 on 2015-09-26
Ok guys, so I apologise if this question has been answered already but Google has not given me the info I need to fix my problem.

So basically what's going on is I am fairly new to Ubuntu, and I'm still learning the way the OS works. I absolutely love it but whenever I try to play just about any game (I tried TF2, Portal 2, and Surgeon Simulator) it looks great, and feels good, but whenever I come into contact with a "solid object" ex.another player, a wall, or just about anything you can interact with, I lag realllyyyy bad and sometimes it even causes my system to freeze. What could be the cause/solution to this? I have played these games on Windows 7 on the same laptop with no issues btw.

I have a Toshiba Satellite L-745, Core i3 processor, 4gb of ram, 1tb Toshiba HDD.

If there is any more information I can provide to help speed this up, please let me know!

---

### Post by ajgreeny on 2015-09-26
It is probably a graphics card driver problem; what graphics hardware do you have, and have you installed any Additional Driver for it?

---

### Post by philinux on 2015-09-26
> **pdickerson01 said:**
> Ok guys, so I apologise if this question has been answered already but Google has not given me the info I need to fix my problem.

So basically what's going on is I am fairly new to Ubuntu, and I'm still learning the way the OS works. I absolutely love it but whenever I try to play just about any game (I tried TF2, Portal 2, and Surgeon Simulator) it looks great, and feels good, but whenever I come into contact with a "solid object" ex.another player, a wall, or just about anything you can interact with, I lag realllyyyy bad and sometimes it even causes my system to freeze. What could be the cause/solution to this? I have played these games on Windows 7 on the same laptop with no issues btw.

I have a Toshiba Satellite L-745, Core i3 processor, 4gb of ram, 1tb Toshiba HDD.

If there is any more information I can provide to help speed this up, please let me know!

Which version of Ubuntu have you installed?

---

### Post by Rob Sayer on 2015-09-26
As mentioned, you need to say which desktop version you're using and more hardware details.  Esp. the video card.  Copy/paste into terminal ...

sudo lshw -C video

... and copy/paste the results here, wrapped in [code] tags.

It's an i3 cpu in your machine so I doubt there are any additional drivers because you probably have intel integrated video (but not necessarily).  My suspicion is that you're using the Unity desktop and it's using too much power by itself.  But we'll see ...

---

### Post by pdickerson01 on 2015-09-26
Here are the results of sudo lshw -C video

[*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)]

I forgot to mention I am running 14.04, and I have Intel Integrated graphics.

Sorry about that lol:lolflag:

---

### Post by ajgreeny on 2015-09-26
I think you are likely to be disappointed with the performance of games using the integrated Intel graphics.

If you really want games to perform better you probably need to consider adding a stand-alone graphic  card, assuming there is physical space available to fit it, and if you can manage that, nvidia cards are probably the best to use.

---

### Post by ajgreeny on 2015-09-26
I think you are likely to be disappointed with the performance of games using the integrated Intel graphics.

If you really want games to perform better you probably need to consider adding a stand-alone graphic  card, assuming there is physical space available to fit it, and if you can manage that, nvidia cards are probably the best to use.

---

### Post by pdickerson01 on 2015-09-26
That's what I was afraid of. No big deal though, it was an old laptop I had lying around anyway. Now I have an excuse to buy bigger and better things. =d>

I think I'll get the GNOME 2 desktop to see if that cuts down on the lag.

---

### Post by mystics on 2015-09-26
Other lightweight desktops you could try are Xfce and LXDE.

However, as already mentioned, Intel integrated graphics aren't that good for gaming, and I've found real-time games even as old as 2007 can have a lot of lag issues on the same integrated graphics controller that you have. You might be able to get away with playing less resource-intensive games, such as smaller indie games and very old games, but games like Portal 2 will very likely have a lot of issues. I'm not sure if this is standard for TF2, but given that I've had similar issues on The Witcher (which released the same year), it doesn't surprise me you have trouble with it handling anything more than basic movement.

---

### Post by pdickerson01 on 2015-09-26
Strange thing is, I just decided to try Portal 2 again, ran perfectly fine on the highest visual settings. Strange. I joined a community game, and that worked fine as well. Didn't change any settings whatsoever. TF2 is still a bit laggy but is playable. Not sure what caused the lag, but it's not there as bad now, so whatever. Got lucky i suppose. :-k

---

### Post by mastablasta on 2015-09-28
> **ajgreeny said:**
> I think you are likely to be disappointed with the performance of games using the integrated Intel graphics.

If you really want games to perform better you probably need to consider adding a stand-alone graphic  card, assuming there is physical space available to fit it, and if you can manage that, nvidia cards are probably the best to use.

actually these old games should run well on HD2000. at least according to the tests made on windows. in fact many games from 2010, 2011 would run on this GPU (at least on low setting). 2nd gen intel is not that bad. but it should run 2005ish titles (or engines) just fine.: [http://www.notebookcheck.net/Intel-HD-Graphics-2000-100.37994.0.html](http://www.notebookcheck.net/Intel-HD-Graphics-2000-100.37994.0.html)

e.g.


> Half Life 2 - Lost Coast Benchmark 2005 
high 1024x768 100.6 FPS

> **pdickerson01 said:**
> Strange thing is, I just decided to try Portal 2 again, ran perfectly fine on the highest visual settings. Strange. I joined a community game, and that worked fine as well. Didn't change any settings whatsoever. TF2 is still a bit laggy but is playable. Not sure what caused the lag, but it's not there as bad now, so whatever. Got lucky i suppose. :-k

moving to lighter DE would still give it a boost. also check if there is any setting to disable desktop special effects while in full screen "game mode". I know KDE has this option available.

---

### Post by tristan16 on 2015-09-29
> **pdickerson01 said:**
> Strange thing is, I just decided to try Portal 2 again, ran perfectly fine on the highest visual settings. Strange. I joined a community game, and that worked fine as well. Didn't change any settings whatsoever. TF2 is still a bit laggy but is playable. Not sure what caused the lag, but it's not there as bad now, so whatever. Got lucky i suppose. :-k

I have an Nvidia GTX 760 in my Ubuntu, and I still get lag in TF2. It seems like some sort of cache problem or maybe just poorly written code in OpenGL. After playing for a few minutes, the graphic lag stops (internet lag is always there, lol). I have the proprietary Nvidia drivers installed, so it's not a problem with that.

---

