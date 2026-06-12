---
title: "display problem after suspend on Dell Mini 10"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by bjord on 2012-11-19
Hi,

I'm brand new to Linux and this is also my first post.  I loaded Ubuntu 12.04 LTS onto the dreaded Dell Mini 10 (Inspiron 1010) with the GMA 500 graphics chip.  I didn't know this was "the dreaded" config before I started the install.

I had the black screen during booting, after the splash, but thanks to these forums got that fixed.  I also got the wireless to work, and despite being a little slow given the hardware, all is working quite nicely now.

My issue comes after the computer resumes after a suspend.  The bottom 20% of the screen is a static solid color.  Either white or the off-pink of the background.  I cannot get it to reset by logging off and back on, nor using the change to tty6 -> tty7 trick.  I can only fix it if I shut down and reboot.

I searched the forums but didn't see this issue posted yet.  I saw some threads about having issues with the suspend command.  That worked, although it took a while for the drive to stop.  But it did work and then resume afterwards, but only the top ~80% of the screen was correct.

As I said, I'm brand new to Linux, so if you want to inquire about any specs, also let me know any commands I'll need to look them up.  

Thanks in advance for any help you all have!
~Alex

Hardware: Dell Inspiron Mini 10
1 GB of memory and 160 GB HDD with 40 GB partitioned for Ubuntu 12.04 LTS

---

### Post by mikewhatever on 2012-11-21
I've had to use the following on the same setup:
```
sudo mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video
```
Resuming from suspend produced a black screen before that.

---

### Post by bjord on 2012-11-22
> **mikewhatever said:**
> I've had to use the following on the same setup:
```
sudo mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video
```
Resuming from suspend produced a black screen before that.
mikewhatever,

This worked like a charm and the computer suspends and "wakes up" much quicker now as well.  

Thanks!  This is a nice little usable Ubuntu-book now!

---

### Post by darkeale on 2013-09-26
Just in case anyone else is looking for it, I can confirm that this fix works on my MSI u180 netbook as well.  Thanks!

---

