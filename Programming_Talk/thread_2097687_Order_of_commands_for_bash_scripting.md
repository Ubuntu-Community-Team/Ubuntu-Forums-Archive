---
title: "Order of commands for bash scripting"
date: 2012-12-24
forum: Programming Talk
---

### Post by CaptainMark on 2012-12-24
I wish to make to bash script where two commands run simultaneously and a third command will run only once the first two have finished, I've been playing around with different bash shortcuts but can't seem to quite get it right, so for an example```
sleep 60 &
echo command1;
echo command2
```How would I change this so the "sleep 60" timer will start and echo will print "command1" to screen immediately but the second echo will not print "command2" until at least the sleep timer is done and "command1" has finished (whichever is the last to finish)

Thanks for any help
Regards
Mark

---

### Post by fdrake on 2012-12-24
> bash script where two commands run simultaneously and a third command will run only once the first two have finished,

```

!#/bin/bash
command 1 &; 
command 2 &;
wait 
command 3;

```

edited:

---

### Post by CaptainMark on 2012-12-24
The first example waits for command1 to finish to execute command2, I tried changing the && to & just in case thats what you meant but then commands 1,2&3 all run at once, the second example is perfect though, I've not come across the wait command before but I can see it will be useful to know.

Many thanks

---

### Post by fdrake on 2012-12-24
i fixed the post.

---

