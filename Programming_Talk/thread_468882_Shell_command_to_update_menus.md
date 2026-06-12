---
title: "Shell command to update menus"
date: 2007-06-09
forum: Programming Talk
---

### Post by FryerFox on 2007-06-09
I'm trying to make a .deb package, and want to add an item to the menus, so I wrote an entry to go in /usr/share/menu

> ?package(timevault):needs="X11" section="Apps/System"\
  title="TimeVault Configuration" command="gksudo '/usr/bin/timevault/timevault --admin'"

When examining other .debs I had lying around (in the apt-cache), I noticed that most put the following in their postinst scripts:
> if [ "$1" = "configure" ] && [ -x "`which update-menus 2>/dev/null`" ]; then
	update-menus
fi

I can't find update-menus on my system, and putting that in my own postinst script doesn't seem to update the menus.

Anyone know what I'm doing wrong?

---

### Post by RedSquirrel on 2007-06-09
You need to install the menu package:

```
sudo apt-get install menu
```

---

### Post by FryerFox on 2007-06-09
I saw that update-menus is in the menu package by searching online, but I did not already have it installed. 

It struck me as very strange that people installing my .deb would have to install 'menu' just to get the menu entries, when I never had to install it for the menu entries in other people's packages.

---

### Post by FuturePast on 2007-06-09
```
update-desktop-database
``` performs a similar function.

---

### Post by FryerFox on 2007-06-09
Thanks,

I realized that what I needed was to make desktop entries in /usr/share/applications rather than menu entries in /usr/share/menu.

Once desktop entries are placed in /usr/share/applications, they appear automagically in the menus.

---

### Post by RedSquirrel on 2007-06-09
> **FryerFox said:**
> I saw that update-menus is in the menu package by searching online, but I did not already have it installed. 

It struck me as very strange that people installing my .deb would have to install 'menu' just to get the menu entries, when I never had to install it for the menu entries in other people's packages.

No, they shouldn't necessarily have to install 'menu' to get the menu entries. To use 'update-menus' (e.g., in the script you quoted above), you need to have 'menu' installed. 

'menu' is the Debian menu, which is not necessarily the same as your regular menu.

EDIT: I just noticed you solved the problem. Good stuff. :)
(your post (#5) arrived while I was composing my reply. Kind of interesting when that happens.)

---

### Post by FryerFox on 2007-06-09
Thanks, though - your post would have sent me in the right direction.

---

