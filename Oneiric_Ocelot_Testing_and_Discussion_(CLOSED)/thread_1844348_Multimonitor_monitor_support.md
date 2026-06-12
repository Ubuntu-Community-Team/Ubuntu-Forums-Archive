---
title: "Multimonitor monitor support"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by schievelbein on 2011-09-14
It is a real shame that they are being so hard on using only Unity.  For many of us like me that have multiple monitors, Unity is not a choice.  I installed 11.10b and spent 3 days trying to get my 3 monitors to work, only to be told MANY times that Unity does not and will not support multiple monitors.  So now I am back to 11.04 and trying to figure out where to go from here.

---

### Post by cariboo on 2011-09-15
I moved this to a separate thread, as it had nothing to do with the thread it was in.

What's the problem, I have unity and gnome-shell running on a dual monitor setup, it shouldn't be to hard to add a third monitor, aside from the two monitor limitation most video cards have built in.

---

### Post by meborc on 2011-09-15
> **schievelbein said:**
> It is a real shame that they are being so hard on using only Unity.  For many of us like me that have multiple monitors, Unity is not a choice.  I installed 11.10b and spent 3 days trying to get my 3 monitors to work, only to be told MANY times that Unity does not and will not support multiple monitors.  So now I am back to 11.04 and trying to figure out where to go from here.

install Xfce. You don't need to use Unity if you don't like it. Xfce will give you a very similar experience to gnome2.

Check out Xubuntu live cd to see if it is more to your liking.

---

### Post by schievelbein on 2011-09-18
Thank you for the move and the advise.
I have tried XFCE and almost every flavor of Ubuntu and a lot of the Linux variations.  My complaint was that I barely have my three monitors on Nvidia cards working under 11.04 using Gnome.  The mouse moves to all three screens and I can open windows in any of the three, but I can not move windows between the monitors.  I have red every thread on the subject and tried so many edits to xorg.config, that I have it memorized, but I still do not have it working as well as I did back in the windoze days....

With 11.10b and even 11.04 with Unity, using three screens was really bad, the same xorg.conf used with gnome comes up with the unity bar in the middle of the center screen and the mouse unable to click on anything.  It was not so bad with 11.04, because I could choose to regress back to gnome, but even with that, my side monitors were worthless separate x-window sessions with no mouse clicking.  I guess I am just surprised that there are no developers that used three or more monitors, or maybe the message is just not getting through that there are a lot of us out here wanting a solution.  

If anybody knows of a solution short of buying ATI cards or a $600 GTX590 card, I would love to know about it.

---

### Post by cariboo on 2011-09-18
Did you try twinview?

---

### Post by schievelbein on 2011-09-18
I can either twinview the left two monitors or the right two monitors or the outside two monitors....

I would like to have all three as one continuous workspace to move windows around onto...

---

### Post by cariboo on 2011-09-19
Can you get one continuous desktop using any other distribution or operating system?

---

### Post by schievelbein on 2011-09-19
Yes, On Windoze7 and Mint I get on continuous screen.
With XFCE I can move windows between screens, on Gnome, I cannot though.
I have narrowed it down to a problem with Xinerama and Gnome, since it works with XFCE.

---

