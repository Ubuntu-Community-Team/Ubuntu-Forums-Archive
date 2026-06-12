---
title: "Looking for a bug workaround..."
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-09-09
This is the bug in question: [https://bugs.launchpad.net/unity/+bug/839769](https://bugs.launchpad.net/unity/+bug/839769)

To summarize, I cannot use 3 finger touchpad taps as middle-click in unity oneiric (and I have posted about this elsewhere).
It has been by far my biggest issues throughout this testing phase and the bug has been marked as "won't fix".
Although that particular bug only affects me, I have seen other, similar bugs related to it.

So the question is, does anyone know of any workarounds or anything I can uninstall to get my 3 finger tap behaviour back?

Unless I can revert this, any further use or testing of any ubuntu release for the forseeable future is out of the question.

---

### Post by jbicha on 2011-09-09
If that's your biggest issue with Oneiric, then we must be doing pretty good!

I don't think my touchpad does multitouch, but if you just want a middle click shortcut, press the left & right touchpad buttons simultaneously if your hardware has 2. There may be other shortcuts depending on where you're trying to use middle click. Middle click is rather uncommon since very few laptops have an actual third button and laptops are outselling desktops. The Firefox "open in new tab" shortcut is either middle click or CTRL+click.

It was explained on the bug report why three-finger tap won't do what you want in Unity. Perhaps you could try GNOME Shell.

---

### Post by x-shaney-x on 2011-09-09
Heh, my biggest issue yes but certainly not the only one :)

I don't actually use the buttons with my touchpad at all since they are quite stiff.
I struggled to adopt a touchpad at all, always using a mouse instead but I forced myself to keep trying for convenience.
Now I have gotten used to it in KDE and natty unity it's hard to try to change how I use it now and don't really want to when I can 3 finger tap everywhere but unity 3d.

---

### Post by SushiR on 2011-09-10
Same problem here. I'm just used to it and it's working fine in Natty. And I don't really understand why configurability of an input device is disabled by design.

---

### Post by x-shaney-x on 2011-09-10
Well the devs seem to think being able to move a window with 3 finger tap is more useful than opening/closing tabs, pasting etc.

Maybe it is for some or maybe even most people I dunno so I suppose it leaves the minority in the lurch.
I don't see why window moving couldn't have been invoked by holding down the 3 fingers instead of tapping, which would have enabled both middle-clicking and window moving possible.

If this was a global change in how touchpads work or something I suppose I could learn to live with it but when it is only unity 3d and nothing else acting like this then it leaves a sour taste for me.

---

### Post by Larkspur on 2011-09-10
> **SushiR said:**
> Same problem here. I'm just used to it and it's working fine in Natty. And I don't really understand why configurability of an input device is disabled by design.

Reading the comment from Chase Douglas, it looks less of a "won't fix" and more of a "can't fix at the moment."

As for a middle-click workaround, run xev and see if a middle click is mapped to the top left-hand corner of the touchpad.  It is on my synaptics pad.

---

### Post by x-shaney-x on 2011-09-10
Yes, the wording in particular: 

> We are working on a new architecture for utouch that may allow for this  behavior to be restored, but that is a ways off at this time.Trouble is, that doesn't sound like something one can really be very hopeful about at the moment.
It MAY be restored but certainly not in the near future and I would assume at least another 2 or 3 releases.

Yes I can use touchpad corners for right and middle click and that its what I originally tried when switching over to touchpad.
Trouble is, my touchpad is level with the laptop casing and even has exactly the same texture so it is difficult to hit the right spot, even when looking at it so not ideal or as easy as 3 finger tap (though of course I can't blame unity devs for that :) )

I guess I can stick some small raised stickers over the right spot or something and try to get the hang of it to keep my options open or something...

---

