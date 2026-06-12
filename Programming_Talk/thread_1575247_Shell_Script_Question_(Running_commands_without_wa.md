---
title: "Shell Script Question (Running commands without waiting for one another)"
date: 2010-09-15
forum: Programming Talk
---

### Post by mashimaro on 2010-09-15
Hi guys, 
I'm not sure how to explain this. But anyway, let me try my best.

In a shell script is there a way to execute each query without them waiting for one another?

For example, 

./myprogram &
will run it in the background, but once the shell script stops executing, it still runs. I want the shell script to cancel the process once it is done with the script.

What do you guys think?
mashi

---

### Post by arrange on 2010-09-15
I don't know if it's the correct way to do this, but I use the PID of the background process and then I kill it```
something &
echo $! > $PidFile
## some more code
# .....
kill $(cat $PidFile) || exit 1

exit 0
```

---

### Post by mashimaro on 2010-09-15
Cool Thanks!

I'll try it out :)

---

