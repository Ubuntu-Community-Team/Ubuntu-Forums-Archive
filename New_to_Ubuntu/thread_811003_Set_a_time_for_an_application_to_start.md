---
title: "Set a time for an application to start"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by docetes on 2008-05-28
How do I do this?

---

### Post by drs305 on 2008-05-28
You do this with crontab. Here is a link to get you started:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Or for a really simple solution for a one-time run, you can read about the 'at' command:
```
man at
```

---

### Post by docetes on 2008-05-29
are these the only two commands that could be used

---

### Post by kpkeerthi on 2008-05-29
There is a GUI (for cron & at) if you would like.
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

---

### Post by drs305 on 2008-05-29
> **kpkeerthi said:**
> There is a GUI (for cron & at) if you would like.
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

docetes,

+1 on the above. If you install it you may not get it to show up in the System, Tools menu (right away or at all) as the link suggests. If it doesn't show up, you can add it by editiing the menu (Rt Clk the System icon, Edit Menus, select System Tools, then New Item. The command to put in the 'command' window is 'gnome-schedule'. Or you can just start it with:
```
gnome-schedule &
```

---

