---
title: "Launcher lockup"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by canadianwriterman on 2011-10-05
I've noticed recently that when I minimize an open app and then reclick on the app's icon in the launcher, nothing happens. I have to right click on the launcher icon, quit the app and reopen it. Oddly, if I use ALT-TAB and select the app, it does bring it back on-screen. This behaviour is frequent, but not consistent.

---

### Post by ubj on 2011-10-05
> **canadianwriterman said:**
> I've noticed recently that when I minimize an open app and then reclick on the app's icon in the launcher, nothing happens. I have to right click on the launcher icon, quit the app and reopen it. Oddly, if I use ALT-TAB and select the app, it does bring it back on-screen. This behaviour is frequent, but not consistent.

Disable "Show minimized windows in switcher". Personally i would just use Unity 2d and wait for [unity 4.24.0 "SRU1"]("https://launchpad.net/unity/+milestone/4.24.0") or Ubuntu 12.04.

---

### Post by mc4man on 2011-10-05
There are continuing issues on minimized windows - seems have have gotten worse (much

Previous to last upgrade there was one scenario where a minimized window couldn't be raised - 
When a window(s) of the same window group was open on another workspace(s), the lone minimized window on a Ws couldn't be raised
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/838055](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/838055)

Now it seems a minimized window can't be raised if any other window of the same workgroup is open anywhere, ie. spread is not raising minimized windows
 bug on
[https://bugs.launchpad.net/unity/+bug/868185](https://bugs.launchpad.net/unity/+bug/868185)

the above issue fixed with 4.22.0-0ubuntu2

---

