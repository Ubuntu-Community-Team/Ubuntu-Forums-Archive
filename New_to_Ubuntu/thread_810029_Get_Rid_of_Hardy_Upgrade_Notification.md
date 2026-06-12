---
title: "Get Rid of Hardy Upgrade Notification"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by thornate on 2008-05-27
I'm running eeeXubuntu so I can't upgrade to Hardy yet (when I tried, it buggered several things up and I had to reinstall Gutsy from scratch). Is there any way to get it to stop the updater telling me that the upgrade is available?

---

### Post by mivo on 2008-05-27
I believe you can right-click on the notification icon, select Preferences and then change your options in the Update tab. Just change "Release upgrade" to "never". :)

---

### Post by kansasnoob on 2008-05-27
Just go to Synaptic and click on Settings > Repositories .......... then click on the Updates tab.

At the bottom of that window you'll see a "Release Upgrade" option. Just select "never".

That should do it.

---

### Post by thornate on 2008-06-12
Ummm... I don't have that option. I have:

Important Security Updates
Recommended Updates
Pre-released Updates
Unsupported Updates
(only the first two are checked)

Then there are the options for how often to check for updates. 

Nothing about "Release Upgrade".

---

### Post by Sef on 2008-06-12
Check for software sources and updates.

---

### Post by sdennie on 2008-06-12
The other option is to go to System->Preferences->Sessions and uncheck Update Notifier from the startup programs.

Edit:
Of course, that will stop Update Notifier from ever telling you that updates are available and you'll have to run it manually.

---

### Post by azurepancake on 2008-06-12
I am curious. Couldn't you stop the notifications by going into the /etc/apt/sources.list file and perhaps comment the line that corresponds with that particular update, and then refresh with "sudo apt-get update"?

Or is that a bad idea, because other updates come from that address as well? Or perhaps I am misunderstanding.. Anyone know?

Thanks

---

### Post by thornate on 2008-06-12
Hmmmm... I still want to get Gutsy updates, which do happen occassionally. It's just mildly irritating that whenever they happen, I also get a message telling me to upgrade to Hardy.

---

### Post by niteshifter on 2008-06-12
Hi,

I have no idea if this will work with eeeXubuntu, but for GNOME (Ubuntu) the Configuration Editor (gconf-editor on the CLI) can be used to control Update Manager.

It will also work in plain old Xubuntu (as a fair amount of that is GNOME) but it's not installed by default. Use Synaptic, search for gconf-editor, mark it and click apply.

I checked the listed dependencies in my Xubuntu 7.10 VM, they're all present. Downloaded gconf-editor in the VM and tried it - works. Did not pull anything else in. Also did not make a menu entry for it, so run it from a terminal:
```
gconf-editor
```

To change (see attached screenshot from GNOME, layout same in Xfce):

Start gconf-editor (Configuration Editor)
Expand the apps entry in the tree view (left pane).
Scroll down to update-manager and click on it, right pane has the settings.
Uncheck the check_dist_upgrades box.
Close the Configuration Editor.

Now, when Update Manager runs, no more distribution upgrade message / button.

---

