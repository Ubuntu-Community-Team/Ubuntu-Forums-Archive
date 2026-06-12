---
title: "Script to adjust brightness with mouse wheel"
date: 2011-07-25
forum: Programming Talk
---

### Post by nzjethro on 2011-07-25
Ahoy oh wise Ubuntu users. I'm interested in writing a script to adjust the brightness of my screen when I scroll my mouse-wheel over the battery icon in the notification area. To make myself clear, you know how when you scroll your mouse wheel while hovering over the volume icon in the notification area (top panel for me), the volume is reduced or increased? Well, I'd like functionality like that for brightness when I hover over the battery (power management) icon.

I have some programming knowledge, but I'm in need of some help.
Is this kind of thing even possible?
And if so, how I go about writing such a programme?
What kind of script should I create?
How do I invoke it by scrolling the mouse-button over the battery icon?

Any help would be much appreciated.

:)

---

### Post by hakermania on 2011-07-25
Of course it IS possible :D
What you need in my opinion is the following:
a) Read the source code of the volume icon (which works with the wheel) to find a way to work with a whell
b) Find a terminal command to call it from your program which changes the brightness instead of increasing the volume.

To be more specific, you could take the source of the volume notification icon and simply change
a) The icon itself (its form, to have something like a sun or something that depicts brightness)
b) The command that the volume icon uses to adjust volume


It shouldn't be too hard ;)

---

### Post by nzjethro on 2011-07-29
Cool, thanks for that, I'll take a look over the weekend, and post if I run into any issues.

---

### Post by era86 on 2011-07-29
This would be pretty badass.  Please followup!

---

### Post by nzjethro on 2011-07-29
I will indeed. When/if I figure it out, I'll submit a HOWTO, and post a link here.

---

### Post by nzjethro on 2011-07-30
Aw man, I feel unworthy of having running Ubuntu. Before getting up to my elbows in code, I decided to see what existed already. Right clicked the panel, Add to Panel, what did I see? Brightness Applet. All the functionality I wanted, without any work. Life's good. :D

---

### Post by hakermania on 2011-07-30
> **nzjethro said:**
> Aw man, I feel unworthy of having running Ubuntu. Before getting up to my elbows in code, I decided to see what existed already. Right clicked the panel, Add to Panel, what did I see? Brightness Applet. All the functionality I wanted, without any work. Life's good. :D
LG but I hoped you'd managed to do that ;)
On the one hand its nice to make things on your own and on the other hand you shouldn't reinvent the wheel :)
So, wait for another challenge :)

---

### Post by stevenswall on 2011-08-01
I've been looking all over, but is there a brightness applet for Ubuntu 11.04 with the Unity interface? (Not the Classic, aka, gNome 2 -Unity interface) I can't add things to the panel in the same way as 10.10, and would appreciate it if someone could point me in the right direction.

---

