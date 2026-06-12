---
title: "[SOLVED] Extreme Frustration: 8.10 Screen Resolution cannot fix"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Statik on 2008-11-29
Hey all,

I've done a new install of 8.10 on my previously 8.04 desktop. I used to run it at 1280x1024 24bit @50Hz on my Cicero 19" monitor. This doesn't seem to be possible in 8.10.

I have searched and searched the forums, trying the different solutions. I have an nvidia card, using the 1.77 drivers. The maximum resolution available through that is an odd 1360x768. The maximum available through Screen Resolution is 1024x768. I have edited xorg.conf to add 1280x1024 in the manner suggested in several threads here, rebooted, with no avail.

Can someone please help me get this monitor setup? This was my main video editing PC and the present resolution isn't sufficient to allow me to work.

Thanks in advance,

Statik

---

### Post by blackened on 2008-11-29
Eventually I'll get around to writing a howto on this stuff.

What is the model number of your monitor? If you know the hsync and vrefresh ranges for your monitor, then it should be as simple as plugging these numbers into xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

Plug in your ranges in place of mine:
```
Section "Monitor"
	Identifier	"Configured Monitor"
[B]	HorizSync          30-82
	VertRefresh        56-76[/B]
EndSection
```

Then restart X with
```
sudo /etc/init.d/gdm restart
```

Ctrl+alt+backspace can also be used to kill X if the GDM restart doesn't work.

---

### Post by thadacto on 2008-11-29
I can't help you, but I've got exactly the same problem on 8.04 also with nVidia (GeForce 6100). Most of the video queries in this forum seem to be about nVidia - can't be very compatible with Ubuntu. I was stuck on 600x400 for over a day and everyone was thinking it was the video driver. I'm now up to 800x600 and for the moment I'm staying there - leave well enough alone.
Good luck with your problem.

---

### Post by Statik on 2008-11-30
It was a freebie monitor, Cicero Product ID: DX-987NS Model: 986N

I'll go looking to see if I can find those # on the net anywhere.

Thanks

Statik

---

### Post by Statik on 2008-11-30
Looks like it might have: Line of frequent :30-86KHZ, field frequency :50-160HZ

I'll try that.

Statik

---

### Post by ets2006 on 2008-11-30
OMG - i have had same problem... i fixed by not using any of the NV-GLX drivers

Strangely the problem only exists on NVidia Cards!

---

### Post by Statik on 2008-11-30
Added the sync lines and it came up right away at 1280x1024@50. Looks great.

Thanks all.

I had tried someone else's xorg.conf sync lines and it crashed. This one worked perfectly.

Statik

---

### Post by blackened on 2008-11-30
> **Statik said:**
> Added the sync lines and it came up right away at 1280x1024@50. Looks great.

Thanks all.

I had tried someone else's xorg.conf sync lines and it crashed. This one worked perfectly.

Statik

The thanks button is your friend. Glad to see you got it working. Please mark this as solved.

---

### Post by Statik on 2008-12-01
Found it. Still getting used to the newer version of the forums. :oops:

Statik

---

