---
title: "Empty/Full Trashbin Icons on desktop"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kestal on 2008-04-27
Is there any way to specifically switch the icons for empty/full trashcans on that specific user?

I activated the desktop icon from gconf-editor but do not seem to find anything that would let me change the icons for it. Thanks for the help.

Just right-clicking and going to properties doesn't really do it specifically for empty/full separately. Is there any easy-ish way to do this?

---

### Post by mgmiller on 2008-04-27
As far as I know, the trash bin icon should change as you change the icon set you are using for your theme.
Click on System > Preferences > Appearance.

Find the theme you are using and go to its icon tab.  As you click on different icon sets, you will see all your icons change.

A good place to find more icons is at:
[http://www.gnome-look.org/]("http://www.gnome-look.org/")

Have fun, almost everything is configurable if you look hard enough.  You can waste a lot of time playing with the appearance.  :lolflag:

---

### Post by kestal on 2008-04-27
Indeed. thanks for the quick response. I assumed I had to go through appearance and select themes, but what if I want to edit a specific theme? where would the icon be for trash cans? On that note, I think I found my theme folder that has 5-6 different sizes when it comes to trashcans, would I have to edit all of those specifically?

or is there an easier way to do it? (as I will only have it on the desktop, anyway, could I just edit one of those or...?)

---

### Post by skrribble on 2008-04-27
> what if I want to edit a specific theme? where would the icon be for trash cans?
my trash icons are located in 
```
/home/jacob/.icons/black-white_2-Gloss_big/scalable/places
```
there 14 different trash icons in there for whatever reason, but that is where you'd have to put the icons for gnome to find them.  the names of the icons in mine (full or empty) are:

edittrash  (full)
emptytrash  (empty)
gnome-fs-trash-empty
gnome-fs-trash-full
gnome-stock-trash  (empty)
gnome-stock-trash-full
stock-trash-full
trashcan_empty
trashcan_full
user-trash  (empty)
user-trash-empty
user-trash-full
xfce-trash_empty
xfce-trash_full

You wouldn't need the last 2 for sure, but all the others are used for various things.  HOpe that helps

---

### Post by mgmiller on 2008-04-27
Go to gnomelook.org and look at some icon sets.  If you see one you like, save it and just drag it over the open theme window.  It should install.  Then, when you look in your theme at the icon tab, there will be more choices.

---

