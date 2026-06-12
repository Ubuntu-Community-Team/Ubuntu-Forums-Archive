---
title: "[bash, udev]: How do you detach a script?"
date: 2009-03-16
forum: Programming Talk
---

### Post by unutbu on 2009-03-16
I would like to launch a script via a udev rule:

```
cat /etc/udev/rules.d/81-local.rules
SUBSYSTEM=="block", SUBSYSTEMS=="usb", KERNEL=="sd?1", RUN+="/home/user/bin/test.sh"
```

The problem is test.sh takes a long time to run (it is a backup script), and HAL does not mount the partitions correctly if test.sh takes too much time. 

This problem is discussed here: /usr/share/doc/udev/writing_udev_rules/index.html
> 
[the script] must not run for any extended period of time, because udev is effectively paused while these programs are running. One workaround for this limitation is to make sure your program immediately detaches itself. 

How do you write a script that detaches itself?

I've tried modifying the udev rule by putting an ampersand at the end of the command
```

SUBSYSTEM=="block", SUBSYSTEMS=="usb", KERNEL=="sd?1", RUN+="/home/user/bin/test.sh &"
```

This does not work.

So here is my crude workaround:
```

cat test.sh
#!/bin/sh
test2.sh &

cat test2.sh
#!/bin/sh
<...insert backup commands here...>
```

This works, but it feels wrong. Is there a more elegant way to do this?

---

### Post by geirha on 2009-03-16
Try grouping the commands in the script, and send the group to the background.
```

#!/bin/sh
{
<...insert backup commands here...>
} &

```

---

### Post by unutbu on 2009-03-16
Thank you geirha, this works great! :)

---

### Post by monkeyking on 2009-03-16
> **geirha said:**
> Try grouping the commands in the script, and send the group to the background.
```

#!/bin/sh
{
<...insert backup commands here...>
} &

```

Thats a new one,
I guess this is worth remembering.

---

### Post by ghostdog74 on 2009-03-16
> **monkeyking said:**
> Thats a new one,
I guess this is worth remembering.
That's not new at all. All documented. See here [example 3-1](http://tldp.org/LDP/abs/html/special-chars.html)

---

### Post by dubariam on 2012-04-22
This is indeed worth remembering... I've been searching quite a long time for a solution to this udev run script detach problem. Never imagined the solution to be so easy to solve:-)

Very elegant=D>

---

