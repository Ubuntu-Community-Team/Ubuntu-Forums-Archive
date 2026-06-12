---
title: "Problem with Firefox's Sync"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by czgirb on 2013-06-01
I sync my Firefox between **desktop (XP)** and **lappie (Ubuntu)**. But lately I found that MOST ... the sync is late.

**Example:**
When I open a **lappie's**, the FF still remains to the last time I closed the app when I used **lappie's** and about 5~10 minute more, the sync is works.
When I open a **desktop's**, the FF still remains to the last time I closed  the app when I used **desktop's** and about 5~10 minute more, the sync is works.
Why? It always **LATE** ?????

And now, it's more than an hour ... but it sync no more ... why?
Any suggestions ???

---

### Post by flanagan on 2013-06-01
Under Firefox preferences, go to the Sync tab and under Manage Account choose View Quota. My guess is that some tremendous amount of uncleared History, Tabs, or Add-Ons is being synced. See [https://support.mozilla.org/en-US/kb/how-do-i-manage-my-firefox-sync-account]("https://support.mozilla.org/en-US/kb/how-do-i-manage-my-firefox-sync-account") for more info.

---

### Post by czgirb on 2013-06-01
> **flanagan said:**
> Under Firefox preferences, go to the Sync tab and under Manage Account choose View Quota. My guess is that some tremendous amount of uncleared History, Tabs, or Add-Ons is being synced. See [https://support.mozilla.org/en-US/kb/how-do-i-manage-my-firefox-sync-account](https://support.mozilla.org/en-US/kb/how-do-i-manage-my-firefox-sync-account) for more info.

OK ... I see the biggest amount is **History** ... strange ... the add-on **Click & Clean** will always works everytime I closed the application.
How can the amount is still so big (MB) ??? Is there any suggestion ???

---

### Post by czgirb on 2013-06-01
Un-checked the huge (**History=5.9MB**) one ... but still there is nothing happen with my Firefox.
Even if I re-start the Firefox ... even after the system (Ubuntu/Lappie) was re-start.
Any suggestion?

---

### Post by AaronMT on 2013-06-01
Hi,

I checked the twitter account for Mozilla Services and it looks like there's a known performance issue that is impacting a number of users. Perhaps you are running into this [1]. Also the Mozilla Services status web-site indicates that they are investigating a load-balance issue [2], which sounds related to the late Sync you are seeing. 

[1] [https://twitter.com/mozservices/status/340586699736379392](https://twitter.com/mozservices/status/340586699736379392)
[2] [https://services.mozilla.com/status/](https://services.mozilla.com/status/)

---

