---
title: "Can't access start menu, desktop is empty with nothing at the borders."
date: 2014-10-15
forum: New to Ubuntu
---

### Post by Karstahn_Petzer on 2014-10-15
Title says pretty much most of it. the start menu isn't showing up, and due to a problem when I tried to increase fps with Compiz. It said plugins were conflicting, I stupidly clicked through them. Next thing I know, Start menu is gone and I can't see anything except for the firefox tab I had open. Also, most keyboard shortcuts don't work, I can't access terminal. can I reset these settings without needing to use the start menu or anything and I don't have?

---

### Post by grahammechanical on 2014-10-15
It would not be right to give advice without even knowing what version of Ubuntu you are using. What do you mean by "start menu?"

---

### Post by Karstahn_Petzer on 2014-10-15
Sorry about that. I'm using the latest version of Ubuntu, as I downloaded it today. The start menu is the bar on the left side of the screen that shows sys settings, files, etc. Same with the top bar that has the Wifi status, battery, etc. Both are gone.

---

### Post by CantankRus on 2014-10-15
Does ctrl+alt+t bring up a terminal or can you right click on the desktop?

---

### Post by mastablasta on 2014-10-16
crtl+alt+f1 to get into another console to use the terminal.

also yeah, you made a mess... perhaps the easiest way is to remove the whole desktop and reinstall it.

---

### Post by CantankRus on 2014-10-16
> **mastablasta said:**
>  perhaps the easiest way is to remove the whole desktop and reinstall it.
No ...more than likely just needs to reset compiz and once we find out what access he/she has we can do this. :rolleyes:

---

### Post by Karstahn_Petzer on 2014-10-16
> **mastablasta said:**
>  perhaps the easiest way is to remove the whole desktop and reinstall it.

how would I go about reinstalling it, with just a USB stick and no settings to reinstall?

---

### Post by mastablasta on 2014-10-17
> **CantankRus said:**
> No ...more than likely just needs to reset compiz and once we find out what access he/she has we can do this. :rolleyes:
mhm I am sure that is a solution worth exploring as well. I just wouldn't know how to do it.

> **Karstahn_Petzer said:**
> how would I go about reinstalling it, with just a USB stick and no settings to reinstall?

if you install and don't reformat while doing it, it will just overwrite the OS with default settings keeping additional settings and programs. you might want to try reseting compiz first. I don't know how to do this (I also use Kwin anyway), but apparently people here do.

---

### Post by CantankRus on 2014-10-17
> **Karstahn_Petzer said:**
> Title says pretty much most of it. the start menu isn't showing up, and due to a problem when I tried to increase fps with Compiz. It said plugins were conflicting, I stupidly clicked through them. Next thing I know, Start menu is gone and I can't see anything except for the firefox tab I had open. Also, most keyboard shortcuts don't work, I can't access terminal. can I reset these settings without needing to use the start menu or anything and I don't have?
If you can right click on the desktop, choose to create new folder.
Open that folder and navigate to **/usr/share/applications** and right click on "Terminal" and select copy.
Right click on your desktop and select paste.

Open the terminal on your desktop and run this command...
```
dconf reset -f /org/compiz/
```

Log out and back in.
This command will log you out...
```
kill -9 -1
```

---

