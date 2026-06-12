---
title: "[SOLVED] Restarting crashed application"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by BenWT on 2008-09-19
I'm new to Ubuntu and started using Amarok. It has frozen up a couple of times, and so I've done what I would have in windows - clicked the "close" x, and selected "force quit" when I'm told the program isn't responding. But after amarok shuts down like this, I can't get it to restart without restarting my whole computer. The icon's still there but nothing loads when I click it. What's going on here? Is it a specific problem with Amarok, or is this standard for applications in Ubuntu?

---

### Post by bwang on 2008-09-19
Go to a terminal and type:
```
killall amarok
```

Then type:
```
amarok
```

and hit enter

---

### Post by MegaJim on 2008-09-19
Probably the application didn't terminate properly, you can force it to exit by issuing the command

```
killall amarok
```

from the terminal, or you can get a task manager type application by hitting alt+f2 then typing gnome-system-monitor if you prefer to have a look for yourself at all running processes.

---

### Post by BenWT on 2008-09-19
Thanks, I'll try that next time it happens. And thanks for directing me to the system monitor, I'd been wondering where something like that was.

---

