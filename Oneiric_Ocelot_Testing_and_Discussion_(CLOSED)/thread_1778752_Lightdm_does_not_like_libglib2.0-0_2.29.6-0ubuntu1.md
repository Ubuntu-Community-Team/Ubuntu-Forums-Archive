---
title: "Lightdm does not like libglib2.0-0 2.29.6-0ubuntu1"
date: 2011-06-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-09
I had done a reinstall after my last problems so was using gdm for login and after hearing good things about libglib2.0-0 2.29.6-0ubuntu1 upgraded. All was fine until I tried to go back to lightdm. 

All the same problems were back but much easier to work around. The fun part was that in unity 3d when you use the command sudo dpkg-reconfigure gdm and it displays the selection box the up arrow will not let you select GDM. Instead it pops up a screen shot dialog box. 

I had to get into unity 2d to change the selection. Is there a command that will force GDM or lightdm with no selection box? 

Now where does this bug get reported against?

Bill

---

### Post by ronacc on 2011-06-09
see my reply in the previous thread

---

### Post by mc4man on 2011-06-09
At least here am going to use the new glib and gdm and wait for whatever needs adjusting...

---

### Post by Harry33 on 2011-06-09
There is a new version coming soon.

> glib2.0 (2.29.6-0ubuntu2) oneiric; urgency=low
  * 90_git_lock_issue.patch: git patch to fix lock issues


Here:
[https://launchpad.net/ubuntu/oneiric/+source/glib2.0/2.29.6-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/glib2.0/2.29.6-0ubuntu2)

---

### Post by mc4man on 2011-06-09
> * 90_git_lock_issue.patch: git patch to fix lock issues
Don't think it's related to the lightdm problems

---

### Post by ronacc on 2011-06-09
I updated to libglib-2.6.29-6-0ubuntu2 , reconfigured for lightdm and rebooted . no help both wired and wireless cannot be enabled , clicking network settings brings this notice ( se SS ) , also wont sutdown from the menu had to sudo reboot in a term to get back to gdm to post this .

---

### Post by mc4man on 2011-06-10
new release of lightdm resolves the recent network, ect. issues
lightdm 0.3.7-0ubuntu2

---

### Post by sparker256 on 2011-06-10
> **mc4man said:**
> new release of lightdm resolves the recent network, ect. issues
lightdm 0.3.7-0ubuntu2
The new release fixed my system also and will mark this thread solved.

Bill

---

