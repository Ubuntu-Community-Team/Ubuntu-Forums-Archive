---
title: "Ubuntu on Stand-Alone or External SSD?"
date: 2015-01-09
forum: New to Ubuntu
---

### Post by rbengr on 2015-01-09
I had a very helpful discussion here yesterday about putting Ubuntu on a dedicated computer (Asus G2S).  Now I would like to get opinions on the option of putting Ubunto on an external SSD.  It would connect to my existing Macbook which is partitioned and pretty full.  The SSD option would be more convenient for me but if it's too much trouble compared to the Asus option, I will go with the Asus.  Any opinions appreciated.  Thanks.

---

### Post by TheFu on 2015-01-09
Can you live with bad performance?  That's USB.  USB3 is faster, but still has queuing issues in my experience.  That means it is good for single-use needs, like streaming media or backups, but terrible for running an OS. Lots of people live with this, but why use an SSD if the performance will be so bad and limited by the connection?

OTOH, if you can connect via eSATA - fantastic. That is just like an internal drive in every way to the OS.  Do MB have eSATA?

---

### Post by mc4man on 2015-01-09
For the last 18 months or so have only run ubuntu installs thru usb3 ssd's. Not too sure it's a good deal long term or at all.
With high quality ssd's have found the performance to be great initially though the first drive degraded severely after 10 months, now is more suited one thing at a time if writing. 
In the case of this drive (Angelbird SSD2go) still not sure if performance drop is local to some drive breakdown or garbage collection. Seeing as one can't run trim or secure erase on usb there's nothing to be done.  (maybe send drive to manu, probably won't.
The next laptop I get must have an esata port, then ext. ssd's  can be addressed.

So I got a new one less than half the price (Adata), it works fine but for how long currently unknown. 

There is also a potential issue with usb3 'emissions' that can interfere with wifi but in an older laptop likely not an issue.
( as wifi ant. was commonly in the top rather than the board area.

---

### Post by rbengr on 2015-01-09
Thanks for the responses.  It seems there will be a speed penalty to pay if I install an external SSD.  So much for that option.  I'm now looking at all the files on my Macbook and doing some pruning.  Perhaps there will be enough free space to accomodate Ubuntu.

---

### Post by mc4man on 2015-01-09
As far as speed I've found a really good usb3 ssd drive (not a pen drive) to be probably quicker than a typical internal laptop  hdd. (or at least not worse. 
The question here is for how long when running an Os or multiple Os'es vs. just using for file storage.

---

### Post by oldfred on 2015-01-11
Part of issue with SSD and USB is that trim is not supported. So that would be why system slows down a lot when system gets full.

Something about you have to have AHCI to support trim, and USB driver is totally different than SATA drivers and does not use AHCI.

---

### Post by mc4man on 2015-01-11
> **oldfred said:**
> Part of issue with SSD and USB is that trim is not supported. So that would be why system slows down a lot when system gets full.

Something about you have to have AHCI to support trim, and USB driver is totally different than SATA drivers and does not use AHCI.

To me that's the biggest issue (and why I'll go for eSATA in the future.
Now my first drive that's completely stuffed did list "Auto-TRIM" in it's spec's. but don't think it's either happening or what I thought it meant.
To further compound for some unknown reason at some point I did a full format on the drive which probably is a poor, (very),  idea on a usb ssd
secure-erase may be helpful here but again not available via usb.

---

### Post by sudodus on 2015-01-11
If you get an 'internal' SSD and get a separate casing with eSATA and USB 3 connections, you can move it to a computer with eSATA to get it trimmed from time to time to avoid degrading. Even simpler, you can open the casing and connect it to a regular SATA port to get it trimmed.

---

