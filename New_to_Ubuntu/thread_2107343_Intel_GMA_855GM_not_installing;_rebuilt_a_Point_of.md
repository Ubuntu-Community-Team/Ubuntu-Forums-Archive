---
title: "Intel GMA 855GM not installing; rebuilt a Point of Service into a desktop.  Tips?"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by TheAdmiralty on 2013-01-21
I'll start by introducing myself as being brand new to the Ubuntu forums and OS in general; my knowledge stops at basic navigation and package installation.  Always wanted to learn more about it, and have just been given an opportunity to do so.

For those of you who don't like reading about peoples' projects, skip to the TL;DR at the bottom.  I like to leave something for those who enjoy strange hardware as much as I do. :)

I was given two Fujutsu TeamPOS 2000's when a local store got a new system installed; they obviously hadn't been touched since they were installed about 10 years ago.  I picked the nicest looking one, gutted it, refinished it in matte black, made an entire new front panel, and combined everything i could from both systems and rebuilt it... looks pretty nice for having been a cash register for a decade.  It runs a Pentium M 1.6Ghz/400Mhz FSB and an Intel 82852/855GM with 1GB of DDR memory.  Since everybody likes pictures:
[http://i579.photobucket.com/albums/ss235/Mark3Website/Photo0146_zps3178bca9.jpg](http://i579.photobucket.com/albums/ss235/Mark3Website/Photo0146_zps3178bca9.jpg)
[http://i579.photobucket.com/albums/ss235/Mark3Website/Photo0147_zpsa20cec99.jpg](http://i579.photobucket.com/albums/ss235/Mark3Website/Photo0147_zpsa20cec99.jpg)
...sorry for the quality, best my phone could muster at the time. I'm going to put everything back in the case tonight; I'll update it when that happens.  I'd remove the entire upper panel if I could, but it's needed to boot; the far side is completely lined with tiny switches for every single port, fan, and device that's soldered to this thing.  There used to be a floppy drive (no optical drive at all), but that was torn out when I learned it could boot over USB.

Anyway, Ubuntu is having some serious problems turning a POS into a desktop computer.  The motherboard is built on a doublt-riser system, shaped kind of like a sidways "U" with about five pounds of ports that I'll never have a use for; I didn't expect it to install any drivers or anything to make use of them, and it didn't.  

The main problem is that it isn't detecting the GPU properly, and the monitor attached to it is limited to 1024x768, when it should be at 1280x1024.  It looks surprisingly bad, even though what I'm shooting for isn't exactly a high resolution.  Aside from that, is there anything I can do with that top panel of ports?  Not that I'll be using it, I just hate having junk hardware that isn't even detected.  And I wonder if that DVI-DFP port works...

**TL;DR:**

How do I get my monitor to its proper resolution of 1280x1024 with an Intel 855GM and/or how do I get this 855GM to be properly detected/driven?

---

### Post by windscape on 2013-01-21
Hi,

Hopefully the information [here]("https://wiki.ubuntu.com/X/Config/Resolution") will help.

---

### Post by TheAdmiralty on 2013-01-21
Took a while to figure out what everything did, but it appears to work with help from that link, windscape.  Thanks... not sure why I didn't find that earlier.  cvt command copied into newmode and then addmode got it to come up.  Looks great!

---

