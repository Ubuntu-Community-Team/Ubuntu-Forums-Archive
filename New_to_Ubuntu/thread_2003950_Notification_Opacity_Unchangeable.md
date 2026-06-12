---
title: "Notification Opacity Unchangeable"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by aduda on 2012-06-14
Hey all,

Up until now I've been running a dual boot of Windows 7 and Ubuntu 12.4 with XFCE. A few days ago I decided to wipe everything and do a clean install of Xubuntu. When it first started up, notifications acted how I wanted them to, with adjustable opacity settings. However after remounting my old /home directory, the notifications are 100% opaque. I can bring up the Notifications Menu with Applications > Settings Manager > Notifications or with ```
xfce4-notifyd-config
``` and then change the opacity, but the notifications don't adhere to the changes. The other options work however, i.t. position, theme and timeout.

Clearly somewhere in /home lives some file that controls notifications, I just can't seem to find it. It's obviously a minor thing, but I've been slowly switching over to Ubuntu and I want to learn all I can. Can anyone help me?

Thanks in Advance!

---

### Post by brainwash on 2012-06-15
You can try to change the value by using the Settings Editor (xfce4-settings-editor). If that does not work either, simply delete the corresponding config file in your HOME folder (and relog):
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml
```

---

### Post by aduda on 2012-06-15
Thanks for the reply! Unfortunately that didn't work.

Based on your reply I tried:

1)Running xfce4-settings-editor from terminal and altering the values under xfce4-notifyd.

2)Altering the value in ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml directly and relogging.

3)Removing ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml and relogging.

The opacity of the notifications does not change. Is it possible that xfce4-notifyd is getting the value from somewhere else?

---

### Post by brainwash on 2012-07-04
So there is one more thing to check..

Compositing might be disabled for your current user account, but it is required to display transparent notifications. Navigate to Settings Manager > Window Manager Tweaks > Compositor and activate it (you can uncheck the various shadow options, if you don't need the extra eye candy).

---

