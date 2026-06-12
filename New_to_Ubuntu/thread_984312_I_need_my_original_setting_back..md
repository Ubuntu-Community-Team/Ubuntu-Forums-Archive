---
title: "I need my original setting back."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by MoreCowBell on 2008-11-16
When I click onto a Folder icon to open a sub-folder (for example My Videos folder from within the Home Folder), a new window opens on top of the current window.  It used to open within the same window and I could navigate back and forth within that same window.  Can someone please tell me how I can restore my original setting so that I don't have so many windows open at the same time?

---

### Post by blackened on 2008-11-16
Open a file browser window, click Edit->Preferences. On the Behavior tab, make sure "Always open in browser windows" is checked. Close all Nautilus windows. You may even have to open a terminal and
```
killall nautilus
```

Open a file browser and check it to make sure it's fixed.

---

### Post by MoreCowBell on 2008-11-16
Problem Solved!  Thanks.

---

