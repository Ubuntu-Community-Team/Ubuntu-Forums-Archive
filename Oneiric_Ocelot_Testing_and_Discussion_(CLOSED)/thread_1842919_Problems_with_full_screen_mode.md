---
title: "Problems with full screen mode"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by clivejo on 2011-09-12
I'm having huge problem when I use an application in full screen mode.  Its as if my pointer is offset where I'm actually pointing to.

I also seem to lose the window title bars after a while and cant click on them.

Unity is slowly driving me insane!

---

### Post by mc4man on 2011-09-12
Do you mean maximized or fullscreen (as in firefox fullscreen

I was having a cursor offset issue back a ways, pre A3. It went away and never returned (though in the bug report it was mentioned as a known issue in wine at times), though I do fresh installs weekly or so.

If you have upgraded unity & compiz today then expect all sorts of window issues, the upgrade needs some fixing
(minimized windows remain unseen on the screen/desktop and other problems

---

### Post by clivejo on 2011-09-12
> **mc4man said:**
> Do you mean maximized or fullscreen (as in firefox fullscreen


Yeah full-screen mode, when the menu bar moves to the top along with all the window controls (which I absolutely hate!!)

Then in non-full screen (window) mode, I should be able to move the window by dragging the title bar, but it doesnt. Also the minimise and close buttons wont work either.

---

### Post by mc4man on 2011-09-12
Some of those issues where addressed by the unity/compiz updates today
(unity to 4.14.2-0ubuntu2
[https://bugs.launchpad.net/unity/+bug/840285](https://bugs.launchpad.net/unity/+bug/840285)

The upgrade created new problems - I've found that setting a default option to false takes care of, at least issues when minimizing windows.

In gconf-editor setting to false
/apps/compiz-1/plugins/unityshell/screen0/options/show_minimized_windows

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/847967](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/847967)

---

### Post by effenberg0x0 on 2011-09-12
I just got updates to Firefox in the last 15 minutes 
Maybe they're already looking into it.


```
Setting up firefox-globalmenu (7.0~b5+build1+nobinonly-0ubuntu1) ...
Setting up firefox-gnome-support (7.0~b5+build1+nobinonly-0ubuntu1) ...
Setting up python-cupshelpers (1.3.6+20110831-0ubuntu4) ...
Setting up system-config-printer-common (1.3.6+20110831-0ubuntu4) ...
Setting up system-config-printer-gnome (1.3.6+20110831-0ubuntu4) ...
Setting up system-config-printer-udev (1.3.6+20110831-0ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```

mc4man => Thanks for the tip. Totally works for focus problems when switching between desktop apps and virtualbox.

Regards,
Effenberg

---

