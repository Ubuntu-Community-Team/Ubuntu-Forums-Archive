---
title: "Restoring default panel settings in classic view"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Norm24 on 2011-10-16
I prefer the classic gnome view and while customizing the panel I like an idiot deleted the panel.I can't figure how to restore the default settings and currently only have access to the programs that are on the desktop.Any help would be appreciated.

---

### Post by westie457 on 2011-10-16
> **Norm24 said:**
> I prefer the classic gnome view and while customizing the panel I like an idiot deleted the panel.I can't figure how to restore the default settings and currently only have access to the programs that are on the desktop.Any help would be appreciated.

Run this in a terminal  ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

Might not work though as it is for Gnome2

---

### Post by Norm24 on 2011-10-16
It worked sort of.I now have a panel on the bottom that I can now add to and I was able to get Applications and Places menus back by adding the Menu Bar option.

Now that I know how to restore the panel I would love to have it on top but for some reason the bottom panel can't be deleted and if I try to remove launchers/applets and send them to trash I get an error message and the items can't be deleted.

I can create a new panel but I don't see any point in having duplicate panels.Anyways having it on the bottom is no big deal and I can live with it.I do appreciate your help and thanks.I'm not going to mark this thread as solved yet in case others want add to it.

---

### Post by Lisiano on 2011-10-16
As far as I remember, to reset Gnome (Fully, not just panels) you needed to delete the ~/.gnome2 and ~/.gconf, but deleting just the ~/.gnome2 folder should be enough, if you are afraid to delete it, you can just rename the folder to... Let's say ~/.gnome2_bak

---

### Post by Norm24 on 2011-10-16
I've discovered a major issue with having the panel on bottom.Any window you minimize goes behind the panel and can't be recovered.

I now have two open FF tabs that can't recovered.Even after a restart And relaunch of FF those two tabs autumatically minimize.

I get frustrated with my own stupidity sometimes!

---

### Post by sadaruwan12 on 2011-10-16
Hi, Found this script while going through the net hope this helps

[Link]("http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/")

And another one

[Link]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html")

---

### Post by Norm24 on 2011-10-16
When I log in as Guest(using gnome classic)everyting is as it should be,panel on top with volume control,battery indicator etc.

Looking like I'm doing a clean install,but because all the settings are screwed up I see no point in backing up /home.I'll copy all my documents and bookmarks to disk and go brandy-new!

---

