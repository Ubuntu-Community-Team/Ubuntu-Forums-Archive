---
title: "signal interrupt"
date: 2011-08-23
forum: Programming Talk
---

### Post by rockom on 2011-08-23
Hi,

I'm looking for a method to give me an interrupt when something is logged to dmesg or syslog.
Specifically, when USB over-current is logged.  Right now I scan dmesg every 5 minutes for the 'over-current' event.  I'd rather get an interrupt when dmesg has some activity and then scan.  

Any type of signal I can capture?
Any ideas at all?

I'm using C (no C++).

Thanks,
-Rocko

---

### Post by Toz on 2011-08-23
Its not C code, but how about using inotifywait from the package inotify-tools. You can use it in a bash script to notify you in real-time when a change occurs to a file. Something like:
```
#!/bin/bash

while true
do
   while inotifywait -e modify /var/log/syslog; do
      if (grep -i "over-current" /var/log/syslog); then
         do_something_here
      fi
   done
done

```

---

