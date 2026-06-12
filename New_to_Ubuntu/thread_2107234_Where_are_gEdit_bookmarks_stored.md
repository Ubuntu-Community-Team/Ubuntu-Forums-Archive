---
title: "Where are gEdit bookmarks stored?"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by maboventi on 2013-01-21
Hi all,

When I open a specific file in gEdit the text is automatically displayed at a specific line-column.
I think this happens because that particular text location was once been marked with a bookmarks plugin which is now uninstalled. Despite this, i think the filename and text position are still written someplace but I can't figure where.

Someone has any clue?

(gEdit 3.4.1 on Ubuntu 12.04 - Cannot remember which was the bookmarks plugin I used)

---

### Post by mc4man on 2013-01-21
I'm on 13.04 atm so this may be different.
At least here gedit's line & cursor position on a previous opened/closed file is stored in
~/.local/share/gvfs-metadata probably in the "home" file which is a binary.
(- gedit can't create that file so if you were to delete or rename you'd need to log out/in to restore function in gedit (as seen in 13.04

(- gedit's file history is stored in ~/.local/share/recently-used.xbel as are histories/recent for other apps

---

### Post by maboventi on 2013-01-21
Many thanks, mc4man!
[[COLOR=Navy]_Here_[/COLOR]]("http://comments.gmane.org/gmane.comp.freedesktop.tracker/6831") I've also found interesting informations on the subject you suggested.

---

