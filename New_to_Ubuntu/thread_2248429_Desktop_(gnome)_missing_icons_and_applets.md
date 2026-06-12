---
title: "Desktop (gnome) missing icons and applets"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by kglading on 2014-10-14
I'm not sure how this happened but the icons (applets) are no longer showing in the top portion of the desktop.  Also, I'm not sure the startup items which should show there are actually launching.  I tried doing a restore and even tried installing another windows manager but I'm not even getting the icon on the extreme right which allows me to restart, log off, etc.

I've modified the grub script to start in text mode and used
 sudo start lightdm
but nothing has fixed the problem.

---

### Post by ibjsb4 on 2014-10-14
Desktop (gnome)?  That does not narrow it down.
Is this gnome-flashback?
[https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
Ubuntu gnome?
[http://ubuntugnome.org/screenshots/](http://ubuntugnome.org/screenshots/)
Unity is also built on gnome.
Is this v14.04?

This info will help you get an answer.

---

### Post by kglading on 2014-10-15
> **ibjsb4 said:**
> Desktop (gnome)?  That does not narrow it down.
Is this gnome-flashback?
[https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
Ubuntu gnome?
[http://ubuntugnome.org/screenshots/](http://ubuntugnome.org/screenshots/)
Unity is also built on gnome.
Is this v14.04?

This info will help you get an answer.

OK.  In the mean time I uninstalled GNOME and reinstalled it and reinstalled Unity.  No difference.  I have set it up so I can select the desktop at login.  I get four options.  Here they are and the symptoms:
GNOME  This does not have the symptoms because it is a different layout from Flashback but it seems to be working (but it isn't what I want.)
Gnome Flashback (Compiz)  Has the problem
Gnome Flashback (METACITY) Has the problem
Ubuntu (Unity)  No problem, everything seems to be working but it isn't what I want.

---

### Post by deadflowr on 2014-10-15
Is the whole panel empty, or only the right side?
Might be a problem with indicator-session.

It this 12.04 or 14.04.

---

### Post by kglading on 2014-10-15
> **deadflowr said:**
> Is the whole panel empty, or only the right side?
Might be a problem with indicator-session.

It this 12.04 or 14.04.

It is 14.04 and only the right-hand side is empty.  I'll try to attach a screenshot.

---

### Post by ibjsb4 on 2014-10-15
Try these commands in terminal.
```
sudo apt-get update
killall gnome-panel
sudo apt-get install --reinstall gnome-panel gnome-applets
sudo apt-get -f install
```
Let us know if you get any errors.
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

A work-a-round
Can you Windows key + Alt + Right-click on a blank spot of the top panel and go to 'Add to panel'?

From there you should be able add whatever you want, to the panel.

---

### Post by kglading on 2014-10-15
> **ibjsb4 said:**
> Try these commands in terminal.
```
sudo apt-get update
killall gnome-panel
sudo apt-get install --reinstall gnome-panel gnome-applets
sudo apt-get -f install
```
Let us know if you get any errors.
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

A work-a-round
Can you Windows key + Alt + Right-click on a blank spot of the top panel and go to 'Add to panel'?

From there you should be able add whatever you want, to the panel.

Your suggestion only ended up making my problem a bit worse as everything ended up gone from the upper panel.

Using Alt+Right Click allowed me to add some applets/icons but the ones I wanted weren't listed.

I reinstalled a lot of the Gnome packages and installed several I didn't have installed and in Metacity (I haven't tried Compiz yet) I was able to recover what I needed but now I need to look up how to reposition the applets in the panel.  

Basically, I think my problem is solved, at least to the degree that I have the applets and menus I want on the top panel even if I want to reposition some.

Thanks for your patience and help.;)
[LIST]
[*] 	 		 			:wink: 		
 	
[/LIST]

---

### Post by ibjsb4 on 2014-10-15
killall gnome-panel - restarts the gnome panel
install --reinstall gnome-panel gnome-applets - reinstalls the packages in case of corruption
apt-get -f install - is the command to fix broken packages

Your problems exists because of other problems with your install, not because of the commands.
> Using Alt+Right Click allowed me to add some applets/icons but the ones I wanted weren't listed.
The extra applets are located in the package 'gnome-applets'.
> but now I need to look up how to reposition the applets in the panel
Alt + r-click on the panel icon and move.

---

