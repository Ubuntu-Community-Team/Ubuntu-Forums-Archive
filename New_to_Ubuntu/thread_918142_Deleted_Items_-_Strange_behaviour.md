---
title: "Deleted Items - Strange behaviour"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by birkopf on 2008-09-12
I am new Kubuntu 'Hardy' user. I have two partitions 
1st: /
2nd: /usr
Ext3 filesystem. 
 
I have noticed when I am removing files from my "Deleted files" (by clicking Empty deleted items folder) they being silently transferred to straight to:

*/root/.local/share/Trash/files/*

and everysingle one of them has got file in:

*/root/.local/share/Trash/info/*

called  'nameofthefile'.trashinfo

That's causing a lot of problems to me. I can delete them manually, but I don't understand why this is happening.  

- Can anyone help ?

---

### Post by Pro-reason on 2008-09-12
That's strange.  Are you using KDE 3 or KDE 4?

---

### Post by birkopf on 2008-09-27
> **Pro-reason said:**
> That's strange.  Are you using KDE 3 or KDE 4?
I am using KDE3, without any changes - installed straight from Kubuntu 8.04 Disk.

---

### Post by mc4man on 2008-09-27
It may be because you have home separate from /
Have you tried enabling the 'bypass trash' option? (may not work due to above

Easiest way to set (if you haven't)
In bottom panel r. click add applet. Choose 'Settings'

open Settings -> KDE Components -> File Manager -> Behavior. You'll see the option in there

---

### Post by birkopf on 2008-09-27
> **mc4man said:**
> It may be because you have home separate from /
Have you tried enabling the 'bypass trash' option? (may not work due to above
Easiest way to set (if you haven't)
In bottom panel r. click add applet. Choose 'Settings'
open Settings -> KDE Components -> File Manager -> Behavior. You'll see the option in there
It's hard to say 100% now but I tried to delete something and it seems to be working. Thank you very much for help!

---

### Post by birkopf on 2008-12-27
> **birkopf said:**
> It's hard to say 100% now but I tried to delete something and it seems to be working. Thank you very much for help!

I can confirm it now - I upgraded to Kubuntu 8.10 and re-partitioned my HDD. Now with system on one partition and /home on second, everything is absolutely fine.

---

