---
title: "Better system monitor in xfce4"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by jamesrl on 2011-10-24
I just moved from gnome2 in 10.04 to xfce4.8 in 11.10 (after briefly trying and hating unity/kde4).  So far I like 95% of it, however the xfce4 applets for system monitors are inadequate for my needs.  

Is there a way to install something akin to gnome-system-monitor applet in the panel, so I can preferably see moving graphs of cpu usage, memory usage, and network usage?  I find this information about state over the past 30 seconds extremely useful and the xfce4 apps only seem to tell you the current state which is pretty useless unless you are constantly monitoring it.  

I've heard the XFApplet may be able to do this -- has anyone had success running with 11.10/xfce4.8 (I can't seem to find it in the repos)?  

I'm tempted to write an xfce panel applet to do it, though have never written panel plugins before.

---

### Post by arochester on 2011-10-24
Conky? - [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by gsmanners on 2011-10-24
> **jamesrl said:**
> I just moved from gnome2 in 10.04 to xfce4.8 in 11.10 (after briefly trying and hating unity/kde4).  So far I like 95% of it, however the xfce4 applets for system monitors are inadequate for my needs.

XFApplet uses the old Gnome system that they've abandoned for about three years now, so that's not really an option. I don't know. I like the CPU Graph that's built-in myself, but I guess it depends on what you specifically need.

Conky is nice, but it doesn't go into the panel. It sits in the background which makes it kind of obligatory to move your windows out of the way to see what's going on there (which I've always found a little distracting).

I suppose if you find you *need* a fancy graph, you could install gnome-system-monitor and use that, but that won't go into an applet either. It's kind of a take-what-you-can-get situation at the moment, I'm afraid.

---

### Post by Flymo on 2011-10-24
Conky works well for us in Xubuntu Lucid.  We're half-a-planet away from that machine or I'd offer the .conkyrc file to get you started.

Xubuntu's low-resource composting means that you can have transparency of unfocused windows without a Core i7 (would you believe a single Atom?) and still get a reasonable response.  

With transparent unfocused windows you can get a glimpse of the monitor despite a busy desktop.  Well - it works for us! ;)

---

