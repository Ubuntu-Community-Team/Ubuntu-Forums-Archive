---
title: "This mornings Update failed, need fix!"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by Kellemora on 2011-11-17
Hi Gang

Everything was fine until I installed this mornings update.

Is there a way to REVERSE what was downloaded this morning.
Moving back to a previous kernel does not help, as whatever this mornings download changed has nothing to do with the kernel.

I've rebooted several times to no avail.

In the upper Panel the Main System Installed links are missing!
The Ubuntu Logo, Applications, Places & System links are all gone.

I'm running version 10.04.?  the last kernel number ended in 35 I think, but this mornings Update Manager did not change the kernel.

Thanks

TTUL
Gary

---

### Post by Kellemora on 2011-11-17
Can I take it that NO RESPONSE means there is NO WAY to UNDO the Update Manager Updates.....

What this is telling me is to no longer trust the Ubuntu Update Manager and Ignore the suggested updates unless something in the list is something I've been needing updated and couldn't find from the Original Author.

TTUL
Gary

---

### Post by 3rdalbum on 2011-11-17
The Update Manager should not change the layout of your Gnome Panel. It can't, in fact, as this is governed by the user account and not by root. If your menus have disappeared, it must be due to something else.

Have you tried right-clicking the panel, choosing "Add to Panel..." and choosing the Main Menu applet to add?

---

### Post by hansdown on 2011-11-17
Hi, Kellemora.

10.04 is notorious, for icons disappearing.

I added cairo dock, for those times, that my username would disappear.

---

### Post by Kellemora on 2011-11-18
Hi 3rdalbum

That's what I did as a work around for now!
Added the Menu Applet.

I now know for certain that it's the Update that messed it up somehow!
Because I have another computer that has 10.04 on it but I normally run it in 8.04.
Decided to reboot into 10.04 and all was fine with it.
Installed the items from the Update Manager, things looked OK.
Then I rebooted and POOF the same items are now missing from that computer.
Considering it has not been used for anything else while in 10.04, nothing I could have possibly done would have caused it!
Booted it back into 8.04 since that's my preferred OS on that machine anyhow!

They should make it possible to UNDO the most recent Update from the Update Manager for when things like this happen!

I also should have written down the names of the files it was overwriting as there were tons of them on that machine, it had been so long since I loaded 10.04 on it.

TTUL
Gary

---

### Post by Zill on 2011-11-18
> **Kellemora said:**
> ...I also should have written down the names of the files it was overwriting as there were tons of them on that machine, it had been so long since I loaded 10.04 on it.
I suggest you check the log...
```
cat /var/log/apt/history.log
```

---

### Post by Michael Dooley on 2011-11-18
> **Kellemora said:**
> Everything was fine until I installed this mornings update.

Is there a way to REVERSE what was downloaded this morning?
Moving back to a previous kernel does not help, as whatever this mornings download changed has nothing to do with the kernel.

Synaptic can help you sort this out.

System - Administration - Synaptic Package Manager - password - File, History. Synaptic should display the packages that were installed, updated and removed. You can try removing previously installed packages that you *think* might be causing your problems.

best wishes...

---

