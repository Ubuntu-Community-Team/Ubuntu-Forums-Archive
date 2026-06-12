---
title: "[SOLVED] Screenlet just won't stay dead."
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Zachx65 on 2008-10-11
I had used the SysMonitor screenlet before and ended up deciding not to use it. When I was using it I had it marked to start at log-in. When I removed it I unchecked that box in the screenlets manager, reset screenlet config, and removed it from the start-up box in 'Sessions.' For some reason it still loads at start-up every time. I didn't want to just delete it figuring that will give me errors, any ideas? :KS

---

### Post by Victormd on 2008-10-13
That's very odd. You seem to have covered all the bases.
You unchecked the startup option on the screenlet manager. I think there's an option through right click on the screenlet. Did you check that as well?

Also, what version of screenlets are you using (and what version of ubuntu)?

---

### Post by dhughes on 2008-10-13
It's not just you, the same thing happened to me but I stopped using Screenlets, I never did investigate what was going on.

 I did right click and deleted the Screenlet but it still came back.

---

### Post by jpangamarca on 2008-10-13
Did you try:

```
$ sudo apt-get purge screenlets
```?

This should wipe Screenlets from your system.

---

### Post by Zachx65 on 2008-10-13
Ubuntu 8.0.4.1
Screenlets Ver 0.1.2

Fixed it I guess. Not sure how, saw it running in current session, removed it and hit remember current session. I tried recreating the problem but no luck. 

Thanks for the replies.

---

