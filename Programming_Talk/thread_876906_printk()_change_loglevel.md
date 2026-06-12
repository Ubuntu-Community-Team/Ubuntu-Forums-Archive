---
title: "printk() change loglevel???"
date: 2008-08-01
forum: Programming Talk
---

### Post by raedbenz on 2008-08-01
Hi,,
I can see what printk() printed only in "/var/log/kern.log".
nothing appears on screen. even if i change KERN_ALERT to KERN_INFO or whatever of the 8 loglevels.

i have read some where that if i use this command then it will display onscreen the output. but still doesnt work (i have ubuntu 8.04).
```
# echo 8 > /proc/sys/kernel/printk
```

How can i achieve that?

---

### Post by jinksys on 2008-08-24
> **raedbenz said:**
> Hi,,
I can see what printk() printed only in "/var/log/kern.log".
nothing appears on screen. even if i change KERN_ALERT to KERN_INFO or whatever of the 8 loglevels.

i have read some where that if i use this command then it will display onscreen the output. but still doesnt work (i have ubuntu 8.04).
```
# echo 8 > /proc/sys/kernel/printk
```

How can i achieve that?

echo 8 > /proc/sys/kernel/printk will print all kernel messages to active consoles, not xterm windows like gnome-terminal.

---

