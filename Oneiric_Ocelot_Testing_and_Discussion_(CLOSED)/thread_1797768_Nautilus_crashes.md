---
title: "Nautilus crashes"
date: 2011-07-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-07-05
Is anyone else seeing nautilus crashing while trying to rename a file? If so please add your me too, to bug #[lpbug]805783[/lpbug].

---

### Post by Quackers on 2011-07-05
I just renamed a txt file and it went ok. I then ran all current updates and rebooted and tried again to rename the same file. No crashing Nautilus here.

EDIT However, when I try the specific method you describe in the bug report nothing happens when the delete key is pressed, then Nautilus hangs for a few seconds then crashes.
I've added my me too.

---

### Post by dino99 on 2011-07-05
dont confirm on i386, i've renamed a xsession-errors.old without trouble.

---

### Post by coffeecat on 2011-07-05
Yes, I get this too on a 64-bit system. I've done a me-too.

The whole desktop crashed earlier taking me back to the login screen. I was three-quarters of the way through writing a complicated post. :( Serves me right for not using a text editor and making regular saves while posting from an alpha. I don't know what the triggering factor for the desktop crash was.

---

### Post by Bowmore on 2011-07-05
Yeah, had this problem too with Nautilus. An even worse problem was that Firefox started up with an empty window and had to kill it or after testing other ~/.mozilla contents crashed all the time. Removing  ~/.mozilla however worked.

I traced that down to a globalmenu problem, then removed these packages:
- appmenu-gtk3
- indicator-appmenu
- indicator-appmenu-gtk

and everything works fine again except for the loss of the globalmenu which I dislike anyway.

---

### Post by tlcstat on 2011-07-05
Greetings, 
I've had problems renaming files but the big issue for me is a crashing with "sudo nautilus".  I worked around by installing Midnight Commander and use "sudo mc" which works fine.  
tlcstat

---

### Post by sparker256 on 2011-07-05
> **tlcstat said:**
> Greetings, 
I've had problems renaming files but the big issue for me is a crashing with "sudo nautilus".  I worked around by installing Midnight Commander and use "sudo mc" which works fine.  
tlcstat
This has been a on going issue and wonder why this is such a hard bug to squash.

Bill

---

### Post by tlcstat on 2011-07-05
Greetings,
This matter is not much of an aggravation compared with the fact that there is no user manager.  Since this is a testing version will have to wait for the fix. The developers have their own priorities and using a testing version means reporting and waiting out the process. Just part of the fun. Actually, everything that I do regarding software with this release works smoother than Natty or even Maverick.  
tlcstat

---

### Post by Harry33 on 2011-07-05
> **cariboo907 said:**
> Is anyone else seeing nautilus crashing while trying to rename a file? If so please add your me too, to bug #[lpbug]805783[/lpbug].

I can rename a file in my setups (32-bit and 64-bit) if I do not use an arrow key.
But using an arrow key makes nautilus crash, also with "gksu nautilus".

---

### Post by mc4man on 2011-07-05
It started with a nautilus upgrade but is attributed to glib, should be a new package shortly
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/805797](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/805797)

---

