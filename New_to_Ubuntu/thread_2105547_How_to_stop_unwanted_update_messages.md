---
title: "How to stop unwanted update messages?"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by arroy_0209 on 2013-01-16
I keep getting notice from update manager regarding thunderbird (and related GNOME support), facebook/twitter plugins for Gwibber etc. I never use these on my ubuntu(12.04). How can I stop such update notices from coming? (These appear in a new window after I log in. I update only those I need and leave the rest. But the ones left out are notified whenever I log in later.)

---

### Post by iMac71 on 2013-01-16
do you have tried to uncheck the unwanted updates in the update manager window?
My suggestion derives from my past experience with Apple OSX, but it should work also on Ubuntu.

---

### Post by Warren Hill on 2013-01-16
Updates are important but you can disable the warning see here

[http://lifehacker.com/5295449/disable-ubuntus-annoying-update-manager-popup](http://lifehacker.com/5295449/disable-ubuntus-annoying-update-manager-popup)

---

### Post by mcduck on 2013-01-16
Uninstall the packages you don't want, and you won't get updates for them any more.

It's also possible to set the Update Manager to display a notification & icon instead of popping up the whole window, but it would of course still offer any available updates to any installed package.

...and it *is* possible to pin a package version to stop it from updating, but that only really makes sense in very specific situations and I don't think this is one of those situations as you removing the packages is easier and has more benefits (since you aren't even using them).

---

### Post by ibjsb4 on 2013-01-16
> **Warren Hill said:**
> Updates are important but you can disable the warning see here

[http://lifehacker.com/5295449/disable-ubuntus-annoying-update-manager-popup](http://lifehacker.com/5295449/disable-ubuntus-annoying-update-manager-popup)

Thats an old link and will no longer work.

Don't want update notification?  Remove update-manager, works for me  :)

---

### Post by mcduck on 2013-01-16
> **ibjsb4 said:**
> Thats an old link and will no longer work.

Don't want update notification?  Remove update-manager, works for me  :)

The OP only wanted to get rid of update notifications for certai  applications he's not using.

Anyway, the instruction in the link still work, you just have to use *dconf-editor* instead of *gconf-editor*. ;)

---

### Post by ibjsb4 on 2013-01-16
> **mcduck said:**
> Anyway, the instruction in the link still work, you just have to use *dconf-editor* instead of *gconf-editor*. ;)

If you have to use dconf then the instructions in that link do not work ;)

---

