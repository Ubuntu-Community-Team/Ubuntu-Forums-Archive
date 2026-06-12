---
title: "Fluxbuntu and XDG-Menu"
date: 2008-04-24
forum: Other OS Talk
---

### Post by Mark76 on 2008-04-24
Can anyone tell me how to get the xdg-menu available from [www.roscidus.com](www.roscidus.com) to work with Fluxbuntu? Every time I try to get it working I get this singularly unhelpful error message.

> ParsingError: ParsingError in file '/etc/xdg/menus/applications.menu', File not found

I copied the fluxbuntu menu file from usr/share to /etc/xdg/ but I'm really, REALLY, stuck now.

Please help :(

---

### Post by kerry_s on 2008-04-24
in terminal or console(ctrl+alt+f2->f6):

[B]sudo apt-get install menu-xdg
sudo update-menus
[/B]
done

---

### Post by Mark76 on 2008-04-24
Still getting the same error :(

---

### Post by kerry_s on 2008-04-25
do you already have menu?-> **sudo apt-get install menu**
then **sudo update-menus** again.

---

### Post by Mark76 on 2008-04-25
Yes.

When I did sudo apt-get install menu-xdg it created a folder in etc/xdg called menus with a symlink in it to a file in /var/lib/menu-xdg/menus called debian-menus.menu. However, my xdg-menu app seems to be looking for something called applications.menu.

I'm going to try renaming.

Yay! It worked :D

---

