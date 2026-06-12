---
title: "Add and Remove programs"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2008-07-23
I lost my add and remove prgrams button while messing around in synaptic.

I really need it back!

---

### Post by UbuntuNerd on 2008-07-23
Go > System > Preferences > Main Menu Layout and check to see if the Add/Remove is selected

---

### Post by AutumnPhoenix on 2008-07-23
errm I may have deleted that, too.

I can only acess my menu by right clicking.

and I'm not very sucessful in using synaptic to install things

---

### Post by Bigtime_Scrub on 2008-07-23
That sounds like you installed Fluxbox. That desktop works in a similar way. Do you remember what you installed?

---

### Post by AutumnPhoenix on 2008-07-23
i didn't install anything...i kind of irrationally started deleting programs after my taskbar disappeared thinking that I could reinstall everything and make it work that way.  Now I "installed" a bunch of things using synaptic that never actually installed

---

### Post by Bigtime_Scrub on 2008-07-23
> **AutumnPhoenix said:**
> i didn't install anything...i kind of irrationally started deleting programs after my taskbar disappeared thinking that I could reinstall everything and make it work that way.  Now I "installed" a bunch of things using synaptic that never actually installed

I was just asking if you installed anything...

So from what I gather you don't have any taskbars?

---

### Post by AutumnPhoenix on 2008-07-23
> **Bigtime_Scrub said:**
> I was just asking if you installed anything...

So from what I gather you don't have any taskbars?

no my taskbar was gone this morning.  I don't know why.  So I set out trying to fix it myself...but I think I made it worse.

---

### Post by stevoo on 2008-07-23
[https://answers.launchpad.net/ubuntu/+question/32666](https://answers.launchpad.net/ubuntu/+question/32666)
maybe that can help you ?

---

### Post by kk0sse54 on 2008-07-23
Just log out or press control + alt + backspace if you have to and then when you come to the login screen click on sessions and just make sure it's on gnome (or xfce, whatever you were running before).

---

### Post by Bigtime_Scrub on 2008-07-23
I would check first to see if the panels were deleted first then check to see if they were uninstalled.

Go to where the panel should be and right click. Check the menu that pops up to see if there is an "new panel" option. If there is select it and get your panels back.


If you don't have that option, open a terminal. Since you don't have panels enter "Alt+F2" and scroll down to terminal.

```
sudo apt-get install gnome-panel
```

See what that does. If you get your panels back you will need to add the app launchers by right clicking and "+ adding to panel" feature.

---

### Post by AutumnPhoenix on 2008-07-24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel is already the newest version.
The following packages were automatically installed and are no longer required:
  menu libgengameng4c2a libgoffice-0-common ggzcore-bin python-gdata
  linux-headers-2.6.24-17-generic compizconfig-backend-gconf libtrackerclient0
  libggzmod4 libsgutils1 totem-common compiz-plugins epiphany-data libkonq4
  libggz2 linux-headers-2.6.24-18-generic liblua5.1-0
  compiz-fusion-plugins-extra libggzcore9 timidity python-xlib compiz-core
  compiz-fusion-plugins-main linux-headers-2.6.24-17 linux-headers-2.6.24-18
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


How do I acess the panel now?

---

### Post by AutumnPhoenix on 2008-07-24
when I click panel in the xface setting manager it does nothing

---

