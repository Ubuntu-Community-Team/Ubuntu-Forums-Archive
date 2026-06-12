---
title: "need help from CronTab expert"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by s1baker on 2012-09-25
hi everybody,
I am trying to learn about the crontab command and I can't find out how to do something, and I have looked everywhere on the web.

Sometimes I set my background pics to cycle from a list using a refresh command by setting crontab
( I know there are programs that do this, I haven't been able to find one that works with xubuntu, so I want to use crontab )

here is what I did using this command : "EDITOR=gedit crontab -e"
```
 */12 * * * * DISPLAY=:0.0 xfdesktop --reload > /dev/null 2>&1 
```so that I could refresh my desktop background from a list ever 12 minutes.

After several hours I take this command out of crontab by putting
a '#' in front of the command and then saving crontab.


question:
Is there a way to set crontab that will allow this repetivive command to run for only, say, 3 hours?

---

### Post by spjackson on 2012-09-25
Put the appropriate range in the hour field, e.g.
```

*/12 12-14 * * * DISPLAY=:0.0 xfdesktop --reload > /dev/null 2>&1

```

---

### Post by s1baker on 2012-09-25
thanks spjackson, but wouldn't that also repeat every day from 12 to 14?

---

### Post by spjackson on 2012-09-25
Yes, unless you fill in the day and month fields. In that case it will run again in a year's time.

What exactly are you trying to achieve? Is it to run a fixed number of times at fixed intervals starting at some given point and then stop, never to run again? If so, I don't believe you can express that with crontab syntax. You would have to do something like your original then add an "at" job to run at the end time that updates crontab to remove the expired entry.

It might be easier to do it all with "at".

---

### Post by s1baker on 2012-09-25
I want to allow my desktops backgrounds to cycle at ( for example ) every 12 minutes, but for only, say, 3 hours, and then that is all.
Like you say, I think I would have to set the hours for it to run at say,
15-18, and set the day to what ever day it was.

If I knew how to use the 'at' command to comment out the background refresh command in the crontab file with a '#' at the beginning of the line, I could do that by setting up a script to do that after, say, 3 hours.

---

### Post by spjackson on 2012-09-25
Something like this:
```

#!/bin/bash
# ~/bin/comment-out.sh
crontab -l | sed  '/xfdesktop/s/^/#/' > crontab.new
crontab crontab.new

```

```

echo  $HOME/bin/comment-out.sh | at 'now + 3 hours'

```

---

### Post by s1baker on 2012-09-25
thanks, I'll try that

---

### Post by Hadaka on 2012-09-25
Hi, you can make gedit your contrab default editor with this command..

```
echo "export EDITOR=gedit" >> .bashrc 
```

---

### Post by s1baker on 2012-09-27
thaks guys, everything worked like a charm.

---

