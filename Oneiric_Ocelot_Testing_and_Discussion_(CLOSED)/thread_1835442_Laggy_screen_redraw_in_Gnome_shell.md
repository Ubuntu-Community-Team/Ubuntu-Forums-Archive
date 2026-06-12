---
title: "Laggy screen redraw in Gnome shell"
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pressureman on 2011-08-29
Is anyone else experiencing slow/delayed screen redraws with Gnome shell? My box is fully up to date as of writing this, and I'm using an Intel GM45 "Mobile 4 Series Chipset Integrated Graphics Controller" in a Thinkpad T500.

It mainly seems to affect Firefox, switching between tabs. Sometimes the tab does not redraw, and shows the content of the tab I just switched from. I've also seen it affect Komodo Edit (which is built on top of Mozilla), and often the last line in a terminal window does not update as it should.

Hopefully these problems are just transient and will be fixed in a later release, but I was just curious if anybody else had seen them.

---

### Post by travishume on 2011-08-29
Yes, I've seen this behavior for a few days now. I haven't used Firefox and Chrome is unaffected but gnome-terminals as well as GVim windows are often not redrawn correctly.

I'm also using a Thinkpad but with an i915 adapter.

---

### Post by Dark_Ronius on 2011-09-01
I was getting an issue where a menu (e.g. bluetooth, messaging) would only be drawn when I tried to open a second menu.. then there would be no lag in opening any of them up. This extended to anything that needed to be re-drawn; for example, when clicking a link in Firefox nothing would appear to happen until I interacted with something else on the desktop, which would then cause everything on the screen to "refresh".

I defected to openSUSE for about an hour to see if that would work any better, but I was getting exactly the same problem. I'm guessing this is either some kind of problem in Gnome Shell or with compatibility with graphics drivers?

---

### Post by sgage on 2011-09-01
> **pressureman said:**
> Is anyone else experiencing slow/delayed screen redraws with Gnome shell? My box is fully up to date as of writing this, and I'm using an Intel GM45 "Mobile 4 Series Chipset Integrated Graphics Controller" in a Thinkpad T500.

It mainly seems to affect Firefox, switching between tabs. Sometimes the tab does not redraw, and shows the content of the tab I just switched from. I've also seen it affect Komodo Edit (which is built on top of Mozilla), and often the last line in a terminal window does not update as it should.

Hopefully these problems are just transient and will be fixed in a later release, but I was just curious if anybody else had seen them.

No such problem here (nvidia graphics).

---

### Post by pressureman on 2011-09-01
> **Dark_Ronius said:**
> I was getting an issue where a menu (e.g. bluetooth, messaging) would only be drawn when I tried to open a second menu.. then there would be no lag in opening any of them up. This extended to anything that needed to be re-drawn; for example, when clicking a link in Firefox nothing would appear to happen until I interacted with something else on the desktop, which would then cause everything on the screen to "refresh".

Yeah that pretty sounds like the same thing as I'm seeing. I also found that pressing any key (even just alt or shift) seems to trigger the screen to redraw when it gets into a state like that.

What video hardware do you have?

I don't think it's Gnome shell per se causing the problem, but rather libmutter/libclutter (and possibly in conjunction with particular video hardware).

---

### Post by Trockendeck on 2011-09-12
I have the same problem although i'm not using Ubuntu. After a while of running the desktop, terminal windows don't seem to redraw correctly. Especially when exiting VIM the screen stays the same. I have to hit return a few time for the terminal to update the screen. What works though is to close the terminal window and open a new one.

As pressureman pointed out it's probably libmutter/libclutter causing the issue because a freshly opened window does not show this behavior. I hope it gets fixed soon. It's the most annoying bug in gnome3.

(nvidia graphics here)

---

### Post by sgage on 2011-09-12
I commented earlier that I hadn't seen this issue, but in the past few days, I have seen something like it.

It doesn't happen until after a couple of hours of uptime in GS, and seems to gradually get worse. Not so much screen redraws as lags in response to clicks. 

I had been running ricotz/testing, and reverted back to stock OO repos, and at first I thought it was better. But no. I'm back in ricotz now, and we'll see how it goes.

I figure it's a mutter/clutter thing.

---

### Post by pferraro on 2011-09-12
I'm having window redraw problems myself, usually upon scrolling.  This is also on intel hardware.  How many of you with this problem are also using the xorg edgers ppa?  I am, for one.

---

### Post by sammiev on 2011-09-12
> **pferraro said:**
> I'm having window redraw problems myself, usually upon scrolling.  This is also on intel hardware.  How many of you with this problem are also using the xorg edgers ppa?  I am, for one.

The same problem here but only with FF7. I don't have it with FF6.

---

### Post by splicerr on 2011-09-12
Same problem here, with open source radeon drivers. Probably this bug:

[https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/834214](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/834214)

As per the upstream bug,

[https://bugzilla.gnome.org/show_bug.cgi?id=657071](https://bugzilla.gnome.org/show_bug.cgi?id=657071)

launching gnome-shell like this from fall back mode and there's no redraw issue here.

```

CLUTTER_PAINT=disable-clipped-redraws:disable-culling gnome-shell --replace

```

---

### Post by Bobhuber on 2011-09-12
I'm getting the same problem in Natty 11.04 running FF 7.0b5 so my guess would be Firefox.

---

