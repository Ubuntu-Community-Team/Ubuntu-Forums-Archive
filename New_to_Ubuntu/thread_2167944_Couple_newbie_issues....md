---
title: "Couple newbie issues..."
date: 2013-08-15
forum: New to Ubuntu
---

### Post by tom15 on 2013-08-15
Hi guys, new to Linux in general but have been running LinuxMint 15 for about a month. Decided I should practice with other distros too so today installed Ubuntu 13. Got a few issues I can't figure out.

1- Need to add myself to a group for VirtualBox shared folders. Of course the users and groups app no longer does groups. I installed Gnome System Tools but it's not there. Software manager says it's installed but I have the same user accounts program as before. I have rebooted.

2- Installed Tor browser bundle. Ran it successfully but chose "hide" on the Vidalia screen. On Mint this puts it in the tray, on Ubuntu it just disappears it. Now I can't get to it to exit. 

3- I have a launcher on desktop that I would like to add to the sidebar. No clue how.

Thanks for any help!

---

### Post by tom15 on 2013-08-15
Figured out #1. Had to search for the users and groups app, it did not put it in my settings. Seems odd but there it is.

---

### Post by newb85 on 2013-08-15
First, in Ubuntu versions, the two digits after the first decimal are as important as the ones before it.  13.04 and 13.10 are completely different releases (although 13.10 hasn't been released yet).

#2 - By default, the Ubuntu system tray isn't accessible to programs that don't use AppIndicator.  Could it be that Vidalia/Tor does not?

#3 - While a program is running, you can right-click its icon on the launcher and lock it to the launcher.  I'm guessing that launcher is a carryover from your Mint desktop, since Ubuntu doesn't support adding launchers to the desktop anymore.

---

### Post by tom15 on 2013-08-15
> **newb85 said:**
> First, in Ubuntu versions, the two digits after the first decimal are as important as the ones before it.  13.04 and 13.10 are completely different releases (although 13.10 hasn't been released yet).

#2 - By default, the Ubuntu system tray isn't accessible to programs that don't use AppIndicator.  Could it be that Vidalia/Tor does not?

#3 - While a program is running, you can right-click its icon on the launcher and lock it to the launcher.  I'm guessing that launcher is a carryover from your Mint desktop, since Ubuntu doesn't support adding launchers to the desktop anymore.

OK, it's 13.04.

#2- Can this behavior be changed? A bigger deal than Vadalia not using tray is Pidgin not using it (even though I installed the extension that is supposed to allow it to)

#3- Thanks. That worked on everything except Tor. Doing it on Tor results in a non-functional Vidalia icon . I'll just get used to what I have. It's not really a launcher, just a copy of the start-tor script I put on the desktop.

Is the Unity desktop a new thing? It just just feels unfinished, like I missed the 'use advanced settings' option. I know I could just install Cinnamon but that would defeat the purpose of why I installed Ubuntu in the first place (to learn other ways).

Thanks for the tips, much appreciated!

---

### Post by Gilad_Pellaeon on 2013-08-15
> **tom15 said:**
> OK, it's 13.04.
Is the Unity desktop a new thing? It just just feels unfinished, like I missed the 'use advanced settings' option. I know I could just install Cinnamon but that would defeat the purpose of why I installed Ubuntu in the first place (to learn other ways).

Thanks for the tips, much appreciated!

Unity has been around for over a couple years now but it is heavier on older systems. You might be better off trying Xubuntu or even Lubuntu if you want a more snappy system.

---

### Post by tom15 on 2013-08-15
> **Gilad_Pellaeon said:**
> Unity has been around for over a couple years now but it is heavier on older systems. You might be better off trying Xubuntu or even Lubuntu if you want a more snappy system.

Thanks for the reply. My Mint system (all these run in Vbox) is a lot snappier but I believe Ubuntu is the most used distro so I figure I need to be familiar. I can put up with things going a bit slower, just have to figure out how to work everything. I'm getting there slowly :)

---

### Post by newb85 on 2013-08-15
> **tom15 said:**
> #2- Can this behavior be changed? A bigger deal than Vadalia not using tray is Pidgin not using it (even though I installed the extension that is supposed to allow it to)

Please see [http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html](http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html).


Yes, Unity is less configurable than Cinnamon, KDE, LXDE, XFCE, Gnome 3, and for that matter, the classic Gnome 2.  This was a Canonical decision to try to "unify" the Ubuntu experience, that is, to create a sort of trademark look and feel to the Ubuntu experience.  Needless, to say, this decision caused some unrest among the community at the outset.

Edit:  You could install CompizConfig Settings Manager, if you're looking for some advanced settings for Compiz (the window manager).  It includes a few more options for Unity that what's in the default System Settings.

---

### Post by tom15 on 2013-08-16
> **newb85 said:**
> Please see [http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html](http://www.webupd8.org/2013/05/how-to-get-systray-whitelist-back-in.html).


Yes, Unity is less configurable than Cinnamon, KDE, LXDE, XFCE, Gnome 3, and for that matter, the classic Gnome 2.  This was a Canonical decision to try to "unify" the Ubuntu experience, that is, to create a sort of trademark look and feel to the Ubuntu experience.  Needless, to say, this decision caused some unrest among the community at the outset.

Edit:  You could install CompizConfig Settings Manager, if you're looking for some advanced settings for Compiz (the window manager).  It includes a few more options for Unity that what's in the default System Settings.

Thanks so much! I'll give it a shot ;)

---

### Post by tom15 on 2013-08-16
Perfect! Thank you SO much :)

---

