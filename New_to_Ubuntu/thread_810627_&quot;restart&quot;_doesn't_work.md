---
title: "&quot;restart&quot; doesn't work"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by spotteddog on 2008-05-28
For the last few days, "restart" stopped working. :confused:

If I click on restart, the PC freezes at the Ubuntu logo. Even after several hours, it's still frozen.
But if I click on "shutdown", it shuts down properly.

This started happening after the kernel update of last weekend. I don't know if it is related to that, but I haven't made any other changes.

Thanks

---

### Post by strattonbrazil on 2008-05-28
What happens if you use the shutdown command?

sudo shutdown -r now

Also, what type of computer are you running on?  

If you go to 'System>Administration>System Log' you might find more information.  I would look first in Xorg.0.log.

---

### Post by spotteddog on 2008-05-28
> **strattonbrazil said:**
> What happens if you use the shutdown command?

sudo shutdown -r now

Also, what type of computer are you running on?  

If you go to 'System>Administration>System Log' you might find more information.  I would look first in Xorg.0.log.
If I use the shutdown -r command, the PC restarts fine.

There are no error or warning messages in Xorg.O.log.

PC is Dell XPS 410, Intel dual Core

---

### Post by Dr Small on 2008-05-28
What about:
```
sudo reboot
```

??

---

### Post by spotteddog on 2008-05-28
> **Dr Small said:**
> What about:
```
sudo reboot
```

??
"sudo reboot" works.

And now everthing seems to be back to normal. That is, I can do a restart with no problems. 
Stange. 
I spent the last 2 days having to do a "hard" shutdown to get out of Hardy, now, without doing anything to fix it, all seems fine.

Thanks for all the quick responces.

---

