---
title: "missing icons in amarok"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by paranoid_humanoid on 2008-11-17
Hi,
i'm on ubuntu intrepid (not kununtu) and amarok has been working fine untill lately i installed a couple of kde apps from add/remove programs and then removed them. after that amarok went bizzirc and it's now missing most of its icons. i installed the package kdeartwork but it didn't help..
here's a screenshot:

---

### Post by stephanvaningen on 2008-11-17
Try un-installing amarok, and do:
```
sudo apt-get autoremove
sudo apt-get autoclean
```
and re-install amarok

what's the result?

---

### Post by paranoid_humanoid on 2008-11-17
i tried that yesterday. i even purged it. and it didn't change anything...

---

### Post by CatKiller on 2008-11-17
Does toggling the "Use custom icon theme" in Settings -> Configure Amarok... -> Appearance help at all?

EDIT: Otherwise, the Amarok configuration is, I believe, in ~/.kde/share/apps/amarok. You could rename this to something else to get a new profile that might work.

EDIT 2: As far as I can tell, the icons are provided by the amarok-common package. This might be the one to re-install if the icons really aren't there (/usr/share/apps/amarok/icons).

---

### Post by paranoid_humanoid on 2008-11-17
thank you for your reply.
resetting the "~/.kde/share/apps/amarok" directory didn't do anything. but unchecking the "use custom icon theme" brought back some of the icons but they are not the same as before. probably amarok came with a default custom icon theme and the native one is not full. it's not covering the icons for "collection" or "playback" in settings. and the icon amarok itself in the notification icon looks very ugly as if it was gif or an enlarged 16x16px image.
i don't think this solved it, but it's a temporary solution for now to make amarok usable, so thank you..
here are screenshots of the current situation..

---

### Post by CatKiller on 2008-11-18
Did you restart Amarok after you made the change?

Does checking that box again put it back to how it was in your first set of screenshots, or back to normal?

Have you tried re-installing amarok-common?

Those are all the things I can think of at the moment.

---

### Post by paranoid_humanoid on 2008-11-18
yes i have restarted amarok. the problem has been around for days now, and i've rebooted several times since then..

unchecking the option returns it back to the all-messing mode. so it's a problem of locating that custom icon theme.

yes, i have removed amarok-common along with the amarok package several times and reinstalled them back. i even purged them once, and it didn't matter at all..

my problem still persists...

---

### Post by CatKiller on 2008-11-18
As far as I can tell, all the interface icons are kept in /usr/share/apps/amarok/icons. Are the icons that you're missing there? Is there some identifiable problem with the ones that are missing that isn't exhibited by the others?

I haven't had any problems with Amarok, so I'm going by general principles here.

---

### Post by kaspar_silas on 2008-11-19
I had exactly the same program. I solved it, through synaptic, by:

1/ Removing all KDE packages.
2/ Completely removing all Amarok packages
3/ Installed kubuntu-desktop and it's auto related packages(I use gnome) 

this fixed the icons. However it is hardly an elegant solution.

---

### Post by go_beep_yourself on 2008-11-24
It's probably something wrong with your user's kde configuration. Try

[PHP]mv ~/.kde ~/.kde_old[/PHP]

---

### Post by paranoid_humanoid on 2008-11-25
removing all kde packages then reinstalling amarok did not work.
renaming .kde to something else and starting fresh did not work either..

sorry guys. this is really frustrating me. banshee is just too unstable to use :/

---

