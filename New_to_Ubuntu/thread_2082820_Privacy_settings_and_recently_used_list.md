---
title: "Privacy settings and recently used list"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by Thee on 2012-11-10
Im using 12.10, I've turned off every logging feature in the Privacy settings, but the list of recently used files (in the open/save window) keeps piling, and those files also get indexed so when I type something the HUD, it finds those files as well. I don't want that. If I turned logging of files off, I wont that turned off as well. How can I solve this?

---

### Post by SysBoot on 2012-11-10
> **Thee said:**
> Im using 12.10, I've turned off every logging feature in the Privacy settings, but the list of recently used files (in the open/save window) keeps piling, and those files also get indexed so when I type something the HUD, it finds those files as well. I don't want that. If I turned logging of files off, I wont that turned off as well. How can I solve this?

There should be a little "Record activity" button in the lower right hand corner, switch it to off.

---

### Post by Thee on 2012-11-10
I did. It still records recently used files.

---

### Post by deadflowr on 2012-11-10
The privacy settings affects the Dash, not programs.
Using HUD while in a program like libre writer will still bring up recently used files regardless of whether you fiddled with the privacy settings or not.
How other programs control their settings is up to them.

---

### Post by Thee on 2012-11-10
> **deadflowr said:**
> The privacy settings affects the Dash, not programs.
Using HUD while in a program like libre writer will still bring up recently used files regardless of whether you fiddled with the privacy settings or not.
How other programs control their settings is up to them.

Hm, well that sucks, since the programs done offer any privacy settings. Is there a way to remove the recently used option in the open/save windows then? Or any other way to resolve this?

---

### Post by deadflowr on 2012-11-10
You'll have to look into the various programs you use and see if you can delete the histories.
As I said, it's program to program.

---

### Post by Thee on 2012-11-10
Well Image Viewer is one of the programs, and he doesn't offer such settings. Maybe I should try a different viewer then.

Thanks for clearing that up ;)

---

### Post by deadflowr on 2012-11-10
You can install something like bleachbit(be careful though).
Since you're only clearing recent file lists no need to run as root.
Click and mark the recent documents list in the system section. That should clear the lists up. 

Be careful with bleachbit though, and try not to run as root as people have a tendency to over do it and delete more than they should. Running as root will allow you to remove almost any file, which people do and causes plenty of grief. So just don't run as root.

---

### Post by Thee on 2012-11-10
Ok, that cleared the list.
Thank you!

---

