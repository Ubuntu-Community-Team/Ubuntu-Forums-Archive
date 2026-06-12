---
title: "Wacom tablet unusable in Oneiric"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by osarusan on 2011-10-10
I'm not sure what the cause of this problem is, but since upgrading to Oneiric I have been having serious problems with my wacom pen.

The model is Cintiq 21UX.

The problem is that the pen jumps erratically to the top left corner of the screen while I use it. This happens while the pen is pressed as well, resulting in straight lines being drawn all over the page in GIMP, or icons and windows being dragged off the screen  while trying to move them somewhere.

I am also unable to select any menu items in GIMP. I can open the menus, but not select any options.

This happens whether I use the Wacom Graphics Tablet settings included with Oneiric, or set everything manually with xsetwacom.

---

### Post by Favux on 2011-10-10
Hi osarusan,

Does this involve a button press?  If so it sounds like a Ubuntu specific server bug that was fixed in Natty.

Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/806256](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/806256)  Notice Thomas Parquier has already reported the bug has recurred in Oneiric.

linuwacom-discuss discussion of the bug:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf1xpqdV%2BChLF9L4-ssa37Kmn1%3Dizka1ox5z34mg4dPA4Q%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf1xpqdV%2BChLF9L4-ssa37Kmn1%3Dizka1ox5z34mg4dPA4Q%40mail.gmail.com&forum_name=linuxwacom-discuss)

If this is what you are seeing you should join Thomas on the bug report.  Or are you seeing something else?

---

### Post by osarusan on 2011-10-10
Hi Favux,

This seems to be something different.

Pressing the buttons does nothing out of the ordinary. They work just fine. The erratic behavior happens seemingly at random, while the stylus is being pressed down.

It doesn't happen constantly. Sometimes I will be able to paint a number of strokes in GIMP with no issues. Then, next it will happen about 5 times per second, jumping erratically between where the stylus is touching the tablet and the top left corner, the top edge of the screen, or the left edge of the screen.

Nothing that I am doing appears to be triggering this behavior, other than using the stylus. I can't reproduce it on command, but it happens every time I use the stylus, sometimes the moment the stylus touches the screen, and sometimes just a few seconds after I have been using it.

---

### Post by ranch hand on 2011-10-10
This may have to do with the update in xorg and xserver-xorg-core that has been hanging up in Debian Sid and testing for a good while now.

One of the things held back in the wacom stuff for xserver.  Ubuntu (I checked the repos) is still using the xorg et al that does not want to remove things like Gnome for your system (so am I).  I am sure this will straighten out soon.

I have been sure of that for about 2 weeks now though.

This is the xorg stuff that really goes with the current kernel version.  When that comes in it should, I think, fix the problem.

---

### Post by Favux on 2011-10-11
I think ranch hand might be right because it is sort of sounding like the QT bug.  See if the screen shot in this post looks at all similar to what you are seeing:  [http://ubuntuforums.org/showpost.php?p=11304776&postcount=803](http://ubuntuforums.org/showpost.php?p=11304776&postcount=803)  I link to the launchpad bug on it in the post below and that has a link to the flip side, or pressure part, of the bug.

Otherwise I this is likely a new bug.

---

### Post by osarusan on 2011-10-11
Hmm yep that is very close to my problem. The streaks on mine also go to the left edge and the top edge of the screen, not just the corner, but essentially that looks spot-on to what is happening on my PC.

Hopefully they get this fixed soon... with only a few days until the release it seems like a big bug to me (at as a professional artist...).

Is there a manual fix for this, or will I have to wait for a fix to come through? For now this is a deal breaker for me, and I guess I will have to stick with Natty until this gets fixed.

---

### Post by ivanohe on 2011-10-11
Hello,

Well, looks like I've not posted to right bug report, since I've exactly the same problem with my intuos4.
This erratic behavior doesnt happen with mypaint.

---
Thomas Parquier

---

### Post by Favux on 2011-10-11
As far as I have seen there isn't a patch or whatever to fix this.  I think it is a new bug and we're not sure where it is.

Hopefully it is just a temporary mismatch between the Wacom kernel or X drive and the X server (ABI mismatch?).  And when the hung up X server comes through all will be well.  Obviously to have the lines going up to left upper corner (0,0) means somewhere the coordinates are being lost.

---

### Post by robert shearer on 2011-10-11
> **osarusan said:**
>  The streaks on mine also go to the left edge and the top edge of the screen, not just the corner, but essentially that looks spot-on to what is happening on my PC.

Yes, same happening here lines to top and left and top-left corner.

Tried mypaint and that works perfectly.

Wacom pen and touch-fun.

---

### Post by Favux on 2011-10-11
There look to be two bug reports on this:
[https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/863154)
[https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/868864](https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/868864)

The png in the first bug report looks awfully like the Qt bug.

---

### Post by Favux on 2011-10-12
Also is this only affecting folks in Gimp?

People are reporting MyPaint and Inkscape work fine.

---

### Post by osarusan on 2011-10-12
It's not just GIMP. The desktop is also affected -- trying to select icons or drag windows on the desktop causes it to jump and select everything, or drag windows off the top left corner of the screen.

I just gave MyPaint a try -- the stylus seems to draw properly with no jumping. However, the problem with being unable to activate any menu items with the stylus persists. I can open the file menu, but trying to select Save or Quit or any other item has no result unless I use the mouse and not the stylus. This same issue happens in GIMP, if I try to use the menus, or select brushes, or zoom, etc., in addition to the jumping.

---

