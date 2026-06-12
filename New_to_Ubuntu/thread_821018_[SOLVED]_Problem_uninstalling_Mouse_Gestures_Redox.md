---
title: "[SOLVED] Problem uninstalling Mouse Gestures Redox from FF3?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Slim Backwater on 2008-06-06
I'm running Firefox 3 Beta 5 under Ubuntu 8.04, upgraded from 7.10.

I had three non-functioning extensions left over after the upgrade; "Mouse Gestures Redox 2.0.0", "SafeCache" and "SafeHistory" and I'm having trouble uninstalling Mouse Gestures Redox.

For all three extensions, I clicked uninstall and then restarted Firefox.  The SafeCache and SafeHistory extensions were removed from the list, but "Mouse Gestures Redox" remains.  The only active button is "Enable", but clicking it doesn't seem to do anything.  I don't think it's active, but I'd like to get it off the list.

Any ideas how to get this stubborn extension off the list?

Thanks,

Slim

*Edit maybe Enable did do something.  After restarting the Preferences and Disable buttons are active but they aren't doing anything, even after restarting.

I found the mousegestures.org website which lead me to an apparent bug in 8.04's Firefox 3 Beta. [https://bugs.launchpad.net/bugs/217812](https://bugs.launchpad.net/bugs/217812)

It got it off, there might be a more concise way, but this is what I did:

I rm -r ~/.mozilla/firefox/xxxxxxxx.default/extensions/{FFA36170-80B1-4535-B0E3-A4569E497DD0} (xxx represents a profile name?)  Directory identified from this thread:
[http://www.mousegestures.org/forum/viewtopic.php?id=30](http://www.mousegestures.org/forum/viewtopic.php?id=30)

then I restarted FF,  then I reinstalled Mouse Gestures Redox, restarted, enabled, restarted, disabled, uninstalled, restarted, (it remained in the list) reinstalled, enabled, reinstalled (yes two installations in a row), now FF showed that it was installing, and I had a cancel button.

I cancelled and it went away.  To clean it up, I rm'ed the directory again.

---

