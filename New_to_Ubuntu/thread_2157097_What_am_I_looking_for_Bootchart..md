---
title: "What am I looking for? Bootchart."
date: 2013-06-24
forum: New to Ubuntu
---

### Post by Halpm on 2013-06-24
My 12.10 laptop with gnomeshell is booting quite slowly. It has never booted particularly fast, and I feel it's probably rather slow for its specs. (quad core 2.2 ghz, 8 gig ram - takes nearly 90 seconds to boot and login). I've enclosed a bootchart, but I need help in understanding what it means! Never seen one of these before...
Cheers!

Edit - can't upload a bootchart.png of a size that's readable with the forums attachment rules, so here's a link to it in dropbox:  [http://db.tt/Dg20wdtr](http://db.tt/Dg20wdtr)

---

### Post by ajgreeny on 2013-06-24
That is certainly slow, and there seem to be one point where things are dragging behind:-

At 4 secs there is an exe? that seems to take about 20 secs. to finish; why an exe I do not know, that seems to point to a windows system, so is this a wubi install?

xorg starts at about 42 secs and takes a long time to get going properly, but at least other things are happening at the same time as that, though there are several things that seem rather slow, eg network manager, setvtrgb, and a few others at the bottom of the chart.

However, it's the 20 second delay at the start for that exe that bothers me most as nothing else is happening while that is going on.

If this is a wubi install I will have to drop out of this as I do not know or understand wubi enough to give you any really useful suggestions.

---

### Post by Halpm on 2013-06-24
Don't know what that is - there has never been windows on this machine. It puzzled me as well to be honest... How does one go about finding out what it is and if it can be removed?

---

### Post by Halpm on 2013-06-24
Hmm - just found this: [http://georgovassilis.blogspot.dk/2011/12/exe-process-on-slow-ubuntu-bootchart.html](http://georgovassilis.blogspot.dk/2011/12/exe-process-on-slow-ubuntu-bootchart.html) I have never (consciously) fiddled with the order in which anything is booted or torn down on shutdown. Is this what's happening to me? How do I make it not happen to me? :D

---

### Post by ajgreeny on 2013-06-24
Looks very similar, but I have no idea how to do what the linked post says is needed to ensure that / is unmounted properly at shutdown.

Sorry about that, but at least you have a clue as to what search you now need to make.

Good luck.

---

### Post by oldfred on 2013-06-24
I have never understood bootcharts. 

So I always look as dmesg and look for long times between tasks, outright errors, warnings or some task that keeps trying to load and repeats later but then either fails or works.

I did find mounting my NTFS partition slowed booting a lot. But my SSD boots in 10 secs after grub enter and about 40 sec on hard drive. My system is a dual core Intel about 6 years old with 4GB of RAM.

---

### Post by Halpm on 2013-06-24
Ok - There are two sections of the dmesg output that show large time gaps, one is here:
[   28.162110] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.162168] wlan0: associated
[   46.092846] bbswitch: version 0.7
[   46.092853] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   46.092860] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP

And the other here, near the end of the boot:
[   46.092951] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   46.094569] bbswitch: disabling discrete graphics
[   47.607803] pci 0000:01:00.0: power state changed by ACPI to D3
[   94.209707] CPU4: Package power limit notification (total events = 1)
[   94.209709] CPU5: Package power limit notification (total events = 1)
[   94.209711] CPU6: Package power limit notification (total events = 1)

Can't see it has anything to do with the phantom "exe" in the bootchart though.

Just out of interest, does the gap meant that it's the item before the gap that's taking the time, or the item after?

---

### Post by oldfred on 2013-06-24
I think it is the one after (but not 100% sure).
so I might see what bbswitch is?
And is there some kernel mode setting on power limits?

---

### Post by tgalati4 on 2013-06-24
Perhaps a lot of time is spent turning off or detecting the graphics card.  I found this reference for bbswitch:  [https://github.com/Bumblebee-Project/bbswitch](https://github.com/Bumblebee-Project/bbswitch)

Try turning off discrete graphics in BIOS and then blacklist the bbswitch module and see if that speeds things up.

Use:

```
modinfo bbswitch
``` to see what switches are available for the bbswitch module.  If you want to use discrete graphics all the time, then turn off the embedded graphics in BIOS.

Your bootchart looks normal except for the graphics detection, and just about every subsystem is waiting for the graphics to be initialized by the Xorg server.

---

### Post by Halpm on 2013-10-16
Ok - there was a physical fault on the hard disc. A new hard disc and a fresh install has fixed the problem.

---

