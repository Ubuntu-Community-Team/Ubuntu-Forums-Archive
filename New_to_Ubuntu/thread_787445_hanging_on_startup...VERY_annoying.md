---
title: "hanging on startup...VERY annoying"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mason_feduccia on 2008-05-08
Hello, everyone.
I've recently installed Gutsy on a Gateway notebook that had vista preinstalled (...i had no choice:() 
...Anyway, everything was going great until this one time a few weeks ago when I had to reboot. Grub loaded okay, but when it was time for the login screen to appear, the screen went black and the cursor was up, but that's as far as it got...it just seemed to repeat attempts to load the display server...? 
...just sort of "hangs" there...

I'm completely lost, so ANY advice whatsoever would be tremendously helpful!

Thanks, guys.

---

### Post by garyedwardjohnston on 2008-05-08
I would reinstall.

Sry :)

---

### Post by spiderbatdad on 2008-05-09
Always make sure windows was shut down cleanly before booting Ubuntu. Try editing the kernel line by pressing F6 at the grub options screen. Delete the end of the line: (--quiet splash) and boot.

> I would reinstall sry :)Is generally bad advice.

---

### Post by mason_feduccia on 2008-05-15
Okay, so I tried deleting "quiet splash" and it did the same thing...


Could frequently using the power button to shut down be a cause of a problem like this?

I really just need to be able to access some music files, and if anything just burn them onto cds and reinstall...

---

### Post by Xiong Chiamiov on 2008-05-15
> **mason_feduccia said:**
> 
Could frequently using the power button to shut down be a cause of a problem like this?


Well, it's not a good idea, though if you're using ext3, it won't be as much a problem, since it's journaled.

> **mason_feduccia said:**
> 
I really just need to be able to access some music files, and if anything just burn them onto cds and reinstall...

You can do that by booting off the CD, if it comes to that.

Now, on to the actual problem at hand:
My guess is that is has something to do with xorg.conf and/or your video card driver.  What kind of card do you have, and are you using the restricted drivers (if you know)?

---

### Post by spiderbatdad on 2008-05-15
Try booting into recovery mode and looking for a graphics driver under the System>>Administration>>Hardware Drivers (or Restricted Drivers) tab.

---

### Post by mason_feduccia on 2008-05-15
The video card is an Integrated ATI Radeon® X1270...
and I'm pretty sure I found the proper driver with the restricted drivers manager....
I mean, it was working PERFECTLY until it just froze completely one day and I used the power button to shut down...it's been doing this ever since...

(The notebook's a Gateway M-1616, if that helps any.)

Also, sometimes after I let it try to load for a while, a message will appear reading something like:
The display server has been shut down several times in the past few minutes, and it is likely that something bad is going on. 
...and then some other useless information that I can't recall...


I'll try booting to safe mode and see if I can get anywhere with that.

I really appreciate this, guys.

---

### Post by mason_feduccia on 2008-05-15
Well it was worth a try :(


Okay, I've decided to just back things up and reinstall.

Could anyone tell me how I would go about accessing files on my hard disk using the live cd?
I've looked and I'm not seeing anything familiar...

---

