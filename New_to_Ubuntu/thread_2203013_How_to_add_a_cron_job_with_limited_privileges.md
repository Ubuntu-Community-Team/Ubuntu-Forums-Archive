---
title: "How to add a cron job with limited privileges"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by frogwarrior on 2014-02-01
I want to add a weekly cron job which deletes some of the crap in the .cache folder, heres the script:
```
#!/bin/bash

cacheDir="$HOME/.cache"
deleteDir=()


deleteDir[0]="thumbnails"
deleteDir[1]="mozilla"
deleteDir[2]="chromium"


for delDir in ${deleteDir
[*]}
do
	rm -rf ${cacheDir}/${delDir}
done
```

but I'm cautious about using rm -rf just in case something goes wrong, and it points to somewhere unintended. Is there a way I can make it so the script only has permission to use the $HOME/.cache folder? I notice I can't even add anything to /etc/cron.daily/ without running sudo, so the script I add to it ends up being owned by root. Is it only root that can have jobs in the cron.daily/cron.weekly folders? If so, I'm guessing I best use crontab -e instead, but again, is there a way I can limit my scripts ability to access directories?

---

### Post by ian-weisser on 2014-02-01
One way is to simply hard code the cache dir. Running as root is less relevant if you have it on a tight leash:
```
#!/bin/sh
/bin/rm -rf /home/<USER>/.cache/thumbnails/*
/bin/rm -rf /home/<USER>/.cache/mozilla/*
/bin/rm -rf /home/<USER>/.cache/chromium/*

```

Your script is elegant, but will delete from /root/.cache instead of your user(s) if you cron it as root.

Another way is to use a user-level cron job instead of a root-level cron job. Yeah, crontab -e.
In that case your script should specify $HOME (cron may not know it), and use full path names.
Obviously, if the system is off at cron time, the job won't run.

Yet another way is to use Upstart. This method runs at login (not startup) as you (not root), and complements the user-level cron job.
```
# Save me as ~/.config/upstart/clear-cache.config
#
description "Clear cache upon login"

start on startup

script
   /bin/rm -rf /home/<USER>/.cache/thumbnails/*
   /bin/rm -rf /home/<USER>/.cache/mozilla/*
   /bin/rm -rf /home/<USER>/.cache/chromium/*
end script
```

---

### Post by Lars Noodén on 2014-02-01
You might also try to delete only the older files.  That can be done with [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html).  Below deletes files older than 5 days.  

```

find /home/*user*/.cache/thumbnails/ -type f -mtime +5 -delete

```

Otherwise, if you just delete all the files present you might zap something in active use.

---

