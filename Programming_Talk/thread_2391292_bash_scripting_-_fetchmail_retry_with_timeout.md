---
title: "bash scripting - fetchmail retry with timeout"
date: 2018-05-08
forum: Programming Talk
---

### Post by marchello_lippi2 on 2018-05-08
Hi together, 
I would like to improve my current fetchmail crontab record. 
Right now it just waits 10 seconds, checks if there is already running fetchmail process, exits if yes, fetches mail if no.
```
*/59 9-23 * * * bash -c "sleep 10; if pgrep fetchmail; then exit; else fetchmail --nosyslog --nodetach -vvv; fi" > /dev/null
```

What I'd like to do is wait 1 minute if fetchmail fails (happens with some servers sometimes) and then retry again, increase timeout before each next retry, exit if the amount of retries is more than 10. 
Please advise. Thanks ahead.

---

### Post by TheFu on 2018-05-08
I would start by creating a script. 1-liners are fun, but hard to use and harder to maintain. Then just call the script from the user's crontab.   That way you can follow scripting best practices and perform the more complicated things you seek. I'd probably overwrite a ~/ftch-timeout file as my logic required at the end of any run.  Either resetting it to 1 minute on success or adding to the amount on failure (probably using sed). This assumes running fetchmail in daemon mode isn't sufficient.  If you use a crontab to start run it, you'll need a way to pass information about the prior run ... hence the need for a text file to be checked later.

I haven't used fetchmail in a while, but when I did, ran it in daemon mode with a 60 min attempt.
**set daemon 3600** inside the .fetchmailrc 

BTW, if you are on a systemd init system, the you can let systemd automatically restart fetchmail in daemon mode.  It is actually good at that.  Basically, start it at boot and forget it.

So, I would 
a) run in daemon mode
b) let systemd handle all restarting
c) not worry about longer delays. No harm in trying once every 5 minutes, right?
d) not use the crontab method at all.

But there are 500 different ways to solve this. Whatever works AND makes sense to you is the best answer.

---

### Post by SeijiSensei on 2018-05-08
> **marchello_lippi2 said:**
> What I'd like to do is wait 1 minute if fetchmail fails (happens with some servers sometimes) and then retry again, increase timeout before each next retry, exit if the amount of retries is more than 10. 
Please advise. Thanks ahead.
As TheFu says, you'd need to write a script for this.  You could use iteration in bash to encase the process.  Something like this:

```

#!/bin/bash

TIMEOUT=60
INC=60
for i in {1..10}
do
    run fetchmail with timeout $TIMEOUT
    test for failure
    if okay 
    then 
       exit 0 
    else
       TIMEOUT=$(expr $TIMEOUT + $INC)
    fi
done
exit 1

```

You'd have to write the guts of this, but you probably get the idea.  The for loop will cycle ten times and either exit upon success (with code 0) or repeat with a longer timeout if fetchmail fails.  If all ten cycles fail, the script exits with a failure code (1).

See [https://www.cyberciti.biz/faq/bash-for-loop/](https://www.cyberciti.biz/faq/bash-for-loop/) for details.

---

### Post by marchello_lippi2 on 2018-05-09
Cool to have your help guys. Not that I have solved it on my side yet, will have to play around, though thx anyway.

---

