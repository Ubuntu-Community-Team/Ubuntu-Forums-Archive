---
title: "It was just a matter of time..."
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Glkanter on 2011-10-06
I was messing around with the Monitor function, configuring 2 displays, one being a TV set, and I did it.

I can't recover back to the way things ought to be. I can't see the "System" choice at the top of either screen, so I can't get to "Preferences", so I can't get to "Monitors".

I *can* do a lot of other things, like open a browser, or reboot and use the Grub system to get to a terminal.

So... if someone could just give me some instructions for resetting things using the terminal, I should be OK.

I tried using the Grub recovery and failsafe display mode, but Monitor wouldn't let me change any settings.

Thanks!

---

### Post by pjd99 on 2011-10-06
Either Alt-F2 or go to a terminal:

gnome-display-properties

That brings up the "Monitor Preferences" window for me (11.04 Classic). You need to be in an X session for this to work.

---

### Post by Glkanter on 2011-10-06
Thank you!!!!

That was *really* wonderful!

I'm sure you can appreciate how much your response means to me.

Garry

---

### Post by audiomick on 2011-10-06
Garry, I _*think*_ you can avoid that happening in the first place by designating the screen with the larger resolution as the primary screen. What also helps is if the two screen are set so that the top edges are at the same height.

What happened (I guess... ;)) is this: When you set up the two screens, the x server makes a single screen that encompasses both monitors, with a resolution equal to the width of both screens  (assuming they are side by side) and a height equal to the higher of the two. That means there is a bit of the virtual screen that is above and or below the smaller of the two monitors. That is where your panel will have disappeared to.

---

### Post by Glkanter on 2011-10-06
Thanks for that input.

The 2 screens are very different. A 25" Samsung SyncMaster P2570 flat screen digital hot rod, and a 15 year old 42" projection TV in another room.

I had the Samsung (incorrectly) as the 2nd screen at 1920 * 1080 & the projection at 1024 * 768 (I think).

But the projection TV did not show the top or bottom. And I use Remote Droid, so I *could* have used the mouse.

I'll try making the monitor the 1st screen, like it should have been, and see from there...

But I'll be more careful this time.

---

### Post by Glkanter on 2011-10-06
Well, I managed to get the Samsung to be the left-most screen (the mouse cursor exits to the right), but that makes no difference as to seeing the panel at the top on either screen.

The only approach that has worked is to select the box for "same image on both screens" and put the resolution way low.

Maybe if I put the Ubuntu stuff (Applications, Places & System) on a left-side panel that would get me around this little bump?

---

### Post by Glkanter on 2011-10-06
So as I test this out, a panel on the left, set to autohide becomes visible on the* right-hand* side of the Samsung, and with a little bit of cat & mouse, I can get to the Gnome Menu Bar.

Which, along with the terminal solution, puts me in pretty good shape overall.

Thanks, guys!

---

### Post by audiomick on 2011-10-06
Glad you found a solution. Have fun with it. ;)

---

### Post by Glkanter on 2011-10-06
I'm trying to *legally* watch American Baseball playoffs without paying for cable TV.

It is without a doubt, a lot of monkey business, but as an experiment, and for $ saving, it's not too bad.

I still wonder why the panels act so squirrelly?

Garry

---

### Post by audiomick on 2011-10-06
Can't help you there. I've noticed now and then that they don't do what I expect, but I have no idea why.

---

