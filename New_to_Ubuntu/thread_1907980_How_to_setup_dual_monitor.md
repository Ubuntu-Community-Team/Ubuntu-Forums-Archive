---
title: "How to setup dual monitor?"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Shaq88 on 2012-01-12
Hi guys,
 
I am sure this question has been asked alot, but my situation is a bit different.
My question is divided to both the hardware part and the system installation.
 
My current setup is that:
 
LEFT: Computer A running Windows - Connected to a LCD screen (Screen A) by DVI cable.
RIGHT: Computer B running Ubuntu - Connected to another LCD screen (Screen B) by DVI cable.
 
LCDs are the same type and have both DVI and VGA connections.
 
What I wanna do is to setup Ubuntu to be shown widescreen on both Screen A and Screen B, while allowing an easy way to change back Screen A to show Computer A (Windows) by a single/double click.
 
Be advised both computers are totally seperate with different keyboard and everything, the only thing needed to be in common is actually to connectivity to Screen A with both DVI and VGA cable at the same time.
 
I know it can be done without any special hardware, what would be the best way to do that? and of course, how should I setup the system?
 
Thank you! :)

---

### Post by almikul on 2012-01-12
> **Shaq88 said:**
> What I wanna do is to setup Ubuntu to be shown widescreen on both Screen A and Screen B, while allowing an easy way to change back Screen A to show Computer A (Windows) by a single/double click.
It can be done quite easy, but you would still have to press a button on the monitor (to choose the input) and execute the script (via hotkey) in Ubuntu. So, it is not exactly a single/double click solution, per se. 

Can you first try to set the monitor A's input to VGA (via monitor menu) and see what happens? If Ubuntu does not switch to extended mode automatically, you would have to use xrandr. 

Could you post the outcome of ```
xrandr -q
``` when you are in the extended mode in Ubuntu (i.e., both screens connected to computer B)?

---

### Post by Shaq88 on 2012-01-12
Will do that as soon as I'll be near the computers (not at home, sorry).
 
If I understand, the videocard of Computer B (Ubuntu) is connected Screen A by VGA and Computer A will be connected to the same monitor by DVI?
 
Ubuntu will set extended mode automatically using both DVI and VGA ports of the Ubuntu's videocard and will be able to sync between them?
 
Thanks

---

### Post by Mark Phelps on 2012-01-12
With two monitors connected to your Ubuntu PC, I believe the default is going to be to mirror the same desktop on both screens.

To change that, you need to bring up the Display panel, uncheck the Mirror box.  You will now have two monitors - 1 and 2.

From what I recall, it made the monitor on the right the primary (which was really awful for me, as I always use the LEFT monitor as the primary).

To change this, at the top of the Display panel there is an image of both monitors.  Drag the image on the left to the right -- so they are swapped. NOW, the primary monitor will be on the left.

Also, once mirroring is turned off, if each monitor has its own resolution, you can set that in the Display panel.

---

