---
title: "Control+Alt+Shift+Up/Down Not Working"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by loganellis17 on 2013-10-17
I updated from Ubuntu 13.04 to Ubuntu 13.10 today, and everything works now except the keyboard shortcuts for shifting an application up or down a workspace. The ones for left and right work perfectly. I'm not sure if its a feature in 13.10 or just something wrong, but either way I really need to get it so that I can shift things verticall between workspaces without having to click the icon every time. 

Thanks!

---

### Post by mc4man on 2013-10-17
I had a bug in dev on the workspace switching bindings for up & down being incorrectly set, but as I really don't use Wall never checked the up dn bindings for moving a window within a wall. (& I guess those fixing didn't either.

So what could be  happening is your binding is being set to shift+super+prior & shift+super+next (prior & next may be Page up Page dn), see screenshot

To fix install compizconfig-settings-manager, open it (ccsm in Dash),  go to Wall plugin & fix the binding, just click on the little X button on far right of binding line, it will set back to actual default

Edit: filed new bug
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1241282](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1241282)

---

### Post by loganellis17 on 2013-10-18
This worked! Thank you so much :)

---

