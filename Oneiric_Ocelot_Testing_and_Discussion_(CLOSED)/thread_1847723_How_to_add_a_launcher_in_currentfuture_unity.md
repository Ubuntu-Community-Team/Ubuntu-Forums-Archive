---
title: "How to add a launcher in current/future unity"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gnurfos on 2011-09-21
I'd like to add a custom launcher (not only running a program, but program + arguments, or any given command). I have found a few resource on the net about how to do that, but this seems to have changed over time with versions of unity, and I could not find a way that works for my Oneiric.

How can I do that ? and will this method be the final one, or do I risk having to change it later ?

Thanks.

---

### Post by mc4man on 2011-09-21
Not much has changed, only the r. click option to create desktop launchers is gone. ([see here]("http://ubuntuforums.org/showthread.php?p=11239843")

You can create custom .desktops, preferably in ~/.local/share/applications & use your command or scriptname on the Exec= line (path/to/scriptname if not in path

Also quicklist entries can use any command that runs in Alt+F2 or again can use a script on the quicklist's Exec= line

If your launcher is for the unity launcher & there is any value to you for a Drag & Drop of files on to it then add appropriate MimeType= line to your custom .desktop

---

