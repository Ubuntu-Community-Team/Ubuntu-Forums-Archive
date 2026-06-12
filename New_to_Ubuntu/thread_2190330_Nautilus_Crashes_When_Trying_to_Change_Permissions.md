---
title: "Nautilus Crashes When Trying to Change Permissions While on Root (Ubuntu 13.10)"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by anqa071599 on 2013-11-26
So, here's what happened:

I open the terminal and type in "sudo nautilus" and Nautilus opens and these errors pop up in the terminal:

> (nautilus:3508): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Then I go and right-click a folder/file in the Nautilus window that just opened, go to Permissions, and when I change the owner from root to my username, Nautilus crashes and this error pops up in the terminal:

> (nautilus:3524): Eel-CRITICAL **: eel_timed_wait_stop: assertion 'wait != NULL' failed
**
ERROR:nautilus-properties-window.c:1907:unschedule_or_cancel_owner_change: assertion failed: (file != NULL)


Please help?

---

### Post by Frogs Hair on 2013-11-26
When opening a graphical application as root use gksu or gksudo . I don't know if this will make a difference , but give it a try.

---

### Post by mc4man on 2013-11-26
At this point (nautilus 3.8/3.6), it's a pretty bad idea to run "sudo nautlius", so as mentioned,  you should refrain from doing so. 
You also might want to check your home folder for any  root owned files & if so, then  deal with appropriately.

---

### Post by anqa071599 on 2013-11-27
> **Frogs Hair said:**
> When opening a graphical application as root use gksu or gksudo . I don't know if this will make a difference , but give it a try.

I tried this, and when I right-click a file and press Properties, Nautilus crashes with the same error above. 

> **mc4man said:**
> At this point (nautilus 3.8/3.6), it's a pretty  bad idea to run "sudo nautlius", so as mentioned,  you should refrain  from doing so. 
You also might want to check your home folder for any  root owned files & if so, then  deal with appropriately.

This is why I am trying to run Nautilus as a root, some files in my home folder are root-owned, and I can't access them. Is there another way to make me the owner?

BTW, thanks for the reply guys.

---

