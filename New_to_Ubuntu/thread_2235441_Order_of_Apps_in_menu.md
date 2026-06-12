---
title: "Order of Apps in menu"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by tom119 on 2014-07-21
Hi,
everything seems ok so far, but somehow the apps in the menu aren't quite in the right alphabetically order. (most of them are, some aren't) Can you tell me how to fix this?

---

### Post by Gordonbp531 on 2014-07-21
What do you mean by the "menu bar"?
If you mean the Launcher on the left hand side of the window, just drag and drop to your preferred arrangement...

---

### Post by tom119 on 2014-07-21
I don't mean the bar on the bottom but the lubuntu main menu - where all the apps are listed in different categories.

---

### Post by Gordonbp531 on 2014-07-21
I don't know Lubuntu, but have you tried right-clicking in the menu to see if there are any sort options?

---

### Post by Dennis N on 2014-07-21
> **tom119 said:**
> Hi,
everything seems ok so far, but somehow the apps in the menu aren't quite in the right alphabetically order. (most of them are, some aren't) Can you tell me how to fix this?

This is strange. The application menu is created anew every log in [edit: probably wrong - see post #7 and #9] , and sorting is part if the process. It is redone immediately if you add/modify files in one if the magic locations where .desktop files are parsed. On mine, each category appears alphabetical using the values of Name= in the .desktop files. Evidence: You can change that value, and the position adjusts immediately to reflect that. Check carefully if there something peculiar about the value of those entries in the .desktop files causing the incorrect order you see.

---

### Post by tom119 on 2014-07-21
I installed the menu editors "menulibre" and "alacarte". Maybe something went wrong there. At least, when I go on"reset" in "alacarte" everything is as it should be. But when I deleted alacarte (because I prefer "menulibre"), the alphabetical order in the menu is gone again.

---

### Post by Dennis N on 2014-07-21
> **tom119 said:**
> I installed the menu editors "menulibre" and "alacarte". Maybe something went wrong there. At least, when I go on"reset" in "alacarte" everything is as it should be. But when I deleted alacarte (because I prefer "menulibre"), the alphabetical order in the menu is gone again.

Hmmm...I must be wrong about the menu being generated each time you log in, otherwise how could the changes you did be retained. 

So is there is an editable menu menu file somewhere that the system uses and alacarte modifies? They could be here:

```
dmn@Roxanne:~/.cache/menus$ ls -l
total 28
-rw------- 1 dmn dmn 13881 May 14 07:31 3230170310f16354866301e80bb95c5a
-rw------- 1 dmn dmn 12131 Jul 21 09:09 adfdd8f7c4b36010e64e844ab591ee17

```
Each is a text file of menu categories and entries. One is timed exactly to when I logged on this morning at 9:09 am - was it rebuilt at that time? Why is the older one still there? Does alacarte work with these, or does it add and modify .desktop files that are used to construct the menu? Are there other locations with menu files? 

Looks like there is a command line tool to install new menu entries  - is this used by alacarte?
[http://linux.die.net/man/1/xdg-desktop-menu](http://linux.die.net/man/1/xdg-desktop-menu)
A lot of information on that page to read over (which I haven't yet).

Other References:
[http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html)
[http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)

Any comments?

---

### Post by tom119 on 2014-07-21
Wow, now it works. I looked up where the menu-files are (.../.cache/menus) and just deleted them. It seems that a brand new menu-file got created that way and everything is in the correct order again. Thanks guys.

---

### Post by Dennis N on 2014-07-21
> **tom119 said:**
> Wow, now it works. I looked up where the menu-files are (.../.cache/menus) and just deleted them. It seems that a brand new menu-file got created that way and everything is in the correct order again. Thanks guys.

Very interesting. Definitely it is being created from the .desktop files in the magic locations since the saved menus are gone. Now, if you edit with alacarte, do you get a new menu file in there right after editing? Or if we add a new .desktop file, does that cause a new menu to be generated there? If so, the system at startup can just use the newest menu there and only generates a new file when the .desktop files are modified  (or someone deletes the menu). Sound reasonable?

---

