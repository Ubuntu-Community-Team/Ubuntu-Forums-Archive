---
title: "incrontab and mbsync"
date: 2019-04-26
forum: Programming Talk
---

### Post by frrobert on 2019-04-26
I wrote a 3 line script and an incrontab job to notify me of new email brought down by mbsync.

The script is simply:
 ```
#!/bin/bash
export DISPLAY=:0.0
/usr/bin/notify-send "St. Nectarios has New Mail"

```

The incrontab job is 
```
/home/frrobert/Mail/stnectarios/INBOX/new IN_CREATE /home/frrobert/bin/newmailst.sh
```

If I copy or create a file in the new directory, the incrontab job is triggered and I get the notification.
If i run mbsync and mbsync creates a file in the new directory, I do not get the notification.

I know I am missing something.  

Thanks.

---

