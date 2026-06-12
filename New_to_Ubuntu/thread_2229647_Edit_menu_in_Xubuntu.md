---
title: "Edit menu in Xubuntu"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by jayshomebrew on 2014-06-14
Simply: would like to add "software updater" to list on menus on xubuntu 14.04.

I would like to add it here:
[ATTACH=CONFIG]253948[/ATTACH]

But I'm confused by these options in menu editor:
[ATTACH=CONFIG]253949[/ATTACH]

on 13.04 it was simply clicking the check boxes:
[ATTACH=CONFIG]253947[/ATTACH]

Any help for an old guy ?

---

### Post by Toz on 2014-06-14
Haven't you heard? 40 is the new 20!

1. The first list of applications are your "Favourites". To add an item to that list, find it in the menus on the right, right-click and select "Add to favourites". It will then show up.

2. The categories list at the bottom lists which submenu the item will show up in. 
The options on the right:
- Run in Terminal = have an app start up in a terminal window (only good for scripts)
- Use startup notification = displaying the spinning cursor to indicate that an application is starting. Note that the application needs to support this for it to work (not all do).
- Hide from menus = don't show this item in the menus

3. You can still use the old menu style. Simply add the Applications Menu plugin to the panel (and remove the new whisker-menu plugin).

---

### Post by jayshomebrew on 2014-06-14
[ATTACH=CONFIG]253950[/ATTACH]
Software updater doesn't seem to appear in the menus, so I can't seem to add it to favorites.  Thanks again.

---

### Post by Dennis N on 2014-06-14
To get Software Updater to appear under the System Category (in Whisker Menu):

Method 1 (also see alternative below):

Edit the file **/usr/share/applications/update-manager.desktop** and remove "Settings" from Categories. 

You want:

**[FONT=Courier New]Categories=System;[/FONT]**

Log out and back in. Software Updater should now appear under System in Whisker Menu. It will no longer appear in the Settings Window.

Alternative Method:

An alternative method is to copy update-manager.desktop to ~/.local/share/applications and make you changes there. Changes made there can be done without sudo and will override the key entries in the other location.

(Note: I just tested this to be sure, and it works. I used the alternative method.)

---

### Post by The Cog on 2014-06-14
I had a quick fiddle, picked on gigolo in the System section, and added the Game category to it. Gigolo then appeared in the games section (as well as in System). I had a devil of a time getting rid of it from games again. Editing the Gigolo entry in the games section had no effect. Eventually, I edited the Giglo entry in the System section and removed the Game category from that, and doing that got rid of the on in the Games section. Wacky. 

I then found that if you delete the Settings category from System/Software Updater, it then appears in the menu, but not in the settings panel that you launch from the All Settings button at the bottom of the menu. So the category has some influence on where a launcher will appear, but there are some hidden rules at play that don't make much sense to me.

There is a help link behind the cog button top-right of menulibre, but it just explains how to use the GUI and not about the hidden rules (such as "Items that have a Settings category will not be shown in the menus even if they are given other categories" and "If you add a second category to an item such that it appears in two menus, then editing the non-original item has no effect").

---

### Post by egeezer on 2014-06-14
> **Toz said:**
> Haven't you heard? 40 is the new 20!

3. You can still use the old menu style. Simply add the Applications Menu plugin to the panel (and remove the new whisker-menu plugin).

That's the best advice, from the standpoint of a REALLY older (80).  That's what I did to get back the classic menu, along with all the notifications in the upper panel.

Highly recommended.

---

### Post by jayshomebrew on 2014-06-14
I tried both options, ended up just adding an additional menu item as shown. Thanks.
[ATTACH=CONFIG]253955[/ATTACH]

---

### Post by flamenco108 on 2014-12-03
I had the same problem and solved it as an getting old one - just reinstalled previous menu editor:

```

sudo apt-get install alacarte
alacarte &
```
Then I made visible, what I wanted. Of course, in the canonical Menu Libre I added also the Alacarte activator icon to have an easy opportunity to edit menu again.

---

