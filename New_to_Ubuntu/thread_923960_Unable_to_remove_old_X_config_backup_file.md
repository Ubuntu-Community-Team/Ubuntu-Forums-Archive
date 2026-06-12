---
title: "Unable to remove old X config backup file"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by raj727 on 2008-09-18
I'm using Ubuntu 8.04 with an Nvidia 6800GT graphics card.  I've installed the restricted drivers for Nvidia and adjusted the resolution to the maximum available for my monitor (1920*1200) using Nvidia X Server Settings.

When I go to "Save to X Configuration File", I get the following error:

"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'"

The resolution does change to 1920*1200 but after shutting down and restarting my computer, the resolution defaults back to 1680*1050.  I can change it but I don't know how to save the settings for 1920*1200.

Is there some options/commands to save the new settings?

---

### Post by jamesrl on 2008-09-19
I would guess you can't remove it because you don't have root privleges to write in the /etc/X11 without typing in your password first.  Before running the command prefix it with sudo (or if you are doing it from a graphical environment gksudo)

---

### Post by overdrank on 2008-09-19
Hi and as jamesrl pointed out ```
gksu nvidia-settings
```

---

### Post by raj727 on 2008-09-19
What is the command I would use?  I had been adjusting the resolution and trying to save it using the GUI options available.

---

### Post by jamesrl on 2008-09-19
> **raj727 said:**
> What is the command I would use?  I had been adjusting the resolution and trying to save it using the GUI options available.

So close the current Nvidia-settings if it is open, then type in Alt-F2 (to run an Application) and type in 
```
gksu nvidia-settings
```
reconfigure it to your settings and it should now be able to save the configs in the directory /etc/X11/

---

### Post by raj727 on 2008-09-19
It works.  Thank you!

---

