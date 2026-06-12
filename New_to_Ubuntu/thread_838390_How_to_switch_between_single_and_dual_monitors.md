---
title: "How to switch between single and dual monitors?"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-06-23
I usually use my laptop at my office desk connected to another monitor, using an extended desktop (dual monitors).

Sometimes, I leave the office. But then my laptop doesn't realise that a monitor is missing, and I can't use the computer.

I can solve this problem each time by changing the file [FONT=Courier New]/etc/X11/xorg.conf[/FONT] (I have a working copy of each version of [FONT=Courier New]xorg.conf[/FONT] so I can just copy the relevant version). However, that is a bit of a pain as either I have to remember to do this before shutting down, or I must boot in a recovery mode and make the change.

** Question:** Is it possible to write a script to check automatically when booting, and copy the relevent [FONT=Courier New]xorg.conf[/FONT] to [FONT=Courier New]/etc/X11[/FONT]?

---

### Post by markbuntu on 2008-06-23
What video card do you have and which driver is it using?

---

### Post by Paddy Landau on 2008-06-23
> **markbuntu said:**
> What video card do you have and which driver is it using?
I'm not entirely sure...

When I type
[FONT=Courier New]lspci | grep VGA[/FONT]
I get
[FONT=Courier New]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT]

When I open Applications -> Other -> Screens and Graphics, it shows the Graphics Card as
[FONT=Courier New]i810 - Intel Integrated Graphics Chipsets (Intel 945)[/FONT]

I hope that helps.

---

### Post by Paddy Landau on 2008-06-24
OK, I've found out how to tell whether I have a monitor running. I use the command
[FONT=Courier New] xrandr -q[/FONT]
and check the results with [FONT=Courier New]fgrep[/FONT]. I've written a script to make the change according to what's connected.

However, as the script replaces [FONT=Courier New]/etc/X11/xorg.conf[/FONT], it needs to run as a superuser. Therefore, putting it into the start-up (System -> Preferences -> Sessions) doesn't work.

Do you know how I can get this script to run at start-up as a superuser?

---

### Post by Paddy Landau on 2008-06-24
I've answered my own question about how to run it as root.

Use either update-rc.d or /etc/rc.local.

However, none of them works because of the timing of the run.

I shall just manually run the script whenever necessary.

---

### Post by Paddy Landau on 2008-07-01
Much easier option:

Use xrandr (see the [RandR HowTo]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")).

---

