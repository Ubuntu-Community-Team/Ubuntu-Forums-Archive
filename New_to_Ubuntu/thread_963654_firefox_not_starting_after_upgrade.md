---
title: "firefox not starting after upgrade"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by lolwhites on 2008-10-30
I just upgraded to 8.10 with a fresh install. Whenever I try to run Firefox, either by clicking on the icon on top, or in a terminal, I get the message 
> Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

It doesn't appear in the System monitor, and typing *killall firefox* or *killall firefox-bin* into a terminal gets the response *no process killed* (but it still won't start).

Any ideas?

---

### Post by unutbu on 2008-10-30
Open a terminal and type
```

rm ~/.mozilla/firefox/*.*/lock
```
I believe firefox uses a lock file to indicate that a firefox session is open.

---

### Post by frankleeee on 2008-10-30
A restart will kill it if that is the actual problem. Do you have all processes ticked in system monitor?

---

### Post by cosine352 on 2008-10-30
sorry wrong post

---

### Post by lolwhites on 2008-10-30
> **unutbu said:**
> Open a terminal and type
```

rm ~/.mozilla/firefox/*.*/lock
```
I believe firefox uses a lock file to indicate that a firefox session is open.

Hmm, that didn't work, and restarting didn't help either. What if I deleted the .mozilla file completely and replaced it with my old one from a previous backup?

---

### Post by unutbu on 2008-10-30
If you remove the ~/.mozilla folder, you will lose your bookmarks and preferences. However, if you have those backed up, you might want to try that.

Note that there might be incompatibilities between different versions of firefox. If your old .mozilla was for a Firefox v2 installation, it may not be compatible with Firefox v3. In this case, it might be best to remove the ~/.mozilla folder, then launch Firefox v3. A new ~/.mozilla will be created. Then just copy the bookmarks.html file. I'm not sure if the prefs.js file is compatible, so you might have to redo your preferences.

---

### Post by lolwhites on 2008-10-30
It seems to have done the trick!

---

