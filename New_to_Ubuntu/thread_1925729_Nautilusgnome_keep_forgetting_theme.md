---
title: "Nautilus/gnome keep forgetting theme"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-02-15
Recently have I encountered a bug where the theme seem to be forgotten by nautilus, what happens is that it stop displaying any icons and instead uses the blank text file icon for very thing including folders. Removing the ~/.cache/ folder fixes the problem for a short time, I'm guessing reboot, then i reoccur again, is there a more permanent fix?

---

### Post by sadaruwan12 on 2012-02-15
Ok this might help you 'cos there is a small error in some systems.

> Because of a race condition between the GDM and session calls to gnome-settings-daemon, Gnome can load without a theme.

For more information you can follow this bug report.

As a workaround, you can modify /etc/xdg/autostart/gnome-settings-daemon.desktop and replace 'Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon' with 'Exec=bash -c "sleep 20; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"'.

Note that "20" is an arbitrary value. You might have to fine tune this value and find the one that's right for you. If the session call is too soon it will fail because the GDM one is still alive. If it occurs too late it will only theme your panel but fail to theme your desktop and nautilus. In Virtualbox we found "20" to work quite well. On real hardware this value is likely to be smaller. The slower your computer is, the higher this value is likely to be.

This is not my work I took this from the MINT blog try the mentioned workaround might work for you.

I think this the same issue you're facing.

---

### Post by Frogs Hair on 2012-02-15
Run the following commands from the link in the terminal  .```
sudo apt-get remove nautilus-open-terminal
``````
nautilus -q
```
[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

