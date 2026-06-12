---
title: "Firefox Ubuntu bug?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by bpgunner on 2008-10-21
My Firefox is dissapearing off the page when I minimize it, then I need to go to the shortcut to open it back up.
I've been using Firefox for at least 2 years and Firefox 3 since it was in early beta (using windows). I am very familiar with it and the way I set it up to my preferences. Back to the problem.
I need to use the shortcut to open FF back up after every time I minimize it. After a few hours of this I noticed my RAM usage was extremely high, as if FF was running more than 1 time, but I don't think this is possible and the system monitor shows it running 1 time. At this point it looks like self induced operator error, and FF is simply opening a new page every time I hit the shortcut, but where does it go when I minimize it? Now, to try and narrow the problem down, I disable all add-ons, extensions, etc, shutdown FF from it's close tab and fully power down the comp before I reboot, not just a restart. FF is set to clear my history when I close it. Now I start the comp and hit the FF shortcut, everyone of my minimized pages from before the shutdown all pop up at once. Seems like a bug to me. Before I type another paragraph about what I've done since, does anybody know how to fix this?

(I haven't looked under the desk yet, but thats where it looks like the pages are going.)

---

### Post by bpgunner on 2008-10-21
Help...?

---

### Post by wolfen69 on 2008-10-21
go to synaptic and completely remove firefox. then in terminal: ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
``` then reinstall firefox. hopefully a fresh start will clear this up.

---

### Post by stoogiebuncho on 2008-10-21
I don't know much, but have you tried running firefox from the terminal (I believe the command is just "firefox"), and see if it gives you any error messages when this happens?  That might help narrow things down.

---

### Post by cariboo on 2008-10-21
Instead of reinstalling firefox, you probably won't fix your problem anyway. Save your bookmarks and delete ~/.mozilla. This will delete all your Firefox settings. When you restart Firefox a new profile will be created.

Jim

---

### Post by greg@localhost on 2008-10-22
Are you running Gnome? I had an issue when I used to run Gnome, where the bottom panel disappeared and the only way to get to minimised windows was to ALT+Tab

Are you seeing this with all apps or just Firefox?

---

### Post by rosswmcgee on 2008-10-25
Go to add panel and add window list, then you will  see it.

---

