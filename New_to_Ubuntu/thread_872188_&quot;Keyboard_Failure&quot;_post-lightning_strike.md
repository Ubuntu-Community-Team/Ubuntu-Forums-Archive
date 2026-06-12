---
title: "&quot;Keyboard Failure&quot; post-lightning strike - Hardware issue or not?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-07-27
I'll try and make a long story short...

I have a brand new server running Ubuntu Server (Hardy).  Everything has been running just fine.   

I use the server to stream movies and music to my XBox 360, which I was doing on this rainy afternoon.

All of a sudden, a loud noise, bright flash, and sparks shot up from behind my entertainment center.  Every car alarm went off on the block - seemed like we were struck by lightning!

Surprisingly enough, everything stayed on - the TV, Xbox, Server, etc. - even the cable!  

A couple of hours later I decided to mess with my new server via SSH on my laptop.  At one point I had to reboot and noticed that it was taking unusually long and a "Keyboard Failure" was prompted.   I went over to the server and noticed that both the keyboard and mouse (plugged into USB ports) were no longer working.

They work just fine on my laptop.

Strangely enough, the external USB hard drive I have plugged into the server is still working fine.  To test, I temporarily unplugged the USB Hard drive and plugged in the keyboard to the same USB slot.  Same thing - "Keyboard Failure" which leads to no functionality at all.  Same thing for the mouse.  What's going on here?  I'm so confused.  

Any help would be appreciated.

---

### Post by hardyn on 2008-07-27
if you saw sparks and smoke and fire and badness inside the house, oh yes, something is damaged.

was it a USB or PS2 keyboard?  PS2 keyboards are fused, although the fuse used for the keyboard looks much like a resistor with only one black stripe.

I have seen this fuses blown a few times for various reasons, but it does not seem to take much.  The good thing is the fuse can be replaced, the back thing is you have to be pretty competent with a soldering iron.

try a different keyboard, after that, i would suspect the motherboard has been damaged.

---

### Post by TMcKSmith on 2008-07-27
No smoke - but sparks, yes.  And I'm not quite sure that it came from the server either.

The keyboard is USB.  I figured something may have happened to the motherboard - but why would my external USB drive work on a certain USB slot, and not the USB keyboard?

---

### Post by Pro-reason on 2008-07-27
So, you get keyboard failure if you plug your USB keyboard into your desktop PC but not if you plug it into your laptop PC?  Hmm.  Strange.

It would seem that your peripherals work, but something has happened to the desktop PC.  Let's hope it is not too major.  Hopefully, it is software damage.  If you boot from a live CD, do you still get keyboard failure?  If you do, then your computer is physically screwed and I wouldn't know how to start fixing it.  If the keyboard starts working, then that means that you just need to reinstall Ubuntu to fix the problem.

---

### Post by TMcKSmith on 2008-07-27
> **Pro-reason said:**
> So, you get keyboard failure if you plug your USB keyboard into your desktop PC but not if you plug it into your laptop PC?  Hmm.  Strange.

It would seem that your peripherals work, but something has happened to the desktop PC.  Let's hope it is not too major.  Hopefully, it is software damage.  If you boot from a live CD, do you still get keyboard failure?  If you do, then your computer is physically screwed and I wouldn't know how to start fixing it.  If the keyboard starts working, then that means that you just need to reinstall Ubuntu to fix the problem.



Good idea - I'll give this a shot now.

---

### Post by TMcKSmith on 2008-07-27
I popped in the Ubuntu Server installation disk and the keyboard/mouse are still not working.  Looks like I'm screwed.

I still don't understand why it reads a USB drive but not a USB keyboard...but maybe the hardware is just screwy.

---

### Post by Pro-reason on 2008-07-27
> **TMcKSmith said:**
> I popped in the Ubuntu Server installation disk and the keyboard/mouse are still not working.  Looks like I'm screwed.

I still don't understand why it reads a USB drive but not a USB keyboard...but maybe the hardware is just screwy.

It would seem that it's not the USB bus that is damaged, but the hardware that deals with stuff like keyboard input.  Internally, your computer may convert USB keyboard input into something similar to the data it would receive via PS/2.  You could connect a PS/2 keyboard and see what happens.

In any case, I don't think you can reply on that motherboard any more.

---

### Post by hardyn on 2008-07-27
why would the peripherials not be damaged... might have something to do with chassis grounding or electrical isolation, opto couples etc... something that a keyboard does not have.

---

