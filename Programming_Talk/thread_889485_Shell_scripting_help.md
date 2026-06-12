---
title: "Shell scripting help"
date: 2008-08-14
forum: Programming Talk
---

### Post by frog4044 on 2008-08-14
How would I make a shell script that would open up another shell script on my desktop 5 times at the same time?

---

### Post by dtmilano on 2008-08-14
```
#! /bin/bash
for n in $(seq 5)
do
   myscript&
done

```

---

### Post by ghostdog74 on 2008-08-14
in bash
```

for i in {0..4}
do
 ...
done

```

---

### Post by jinksys on 2008-08-14
> **frog4044 said:**
> How would I make a shell script that would open up another shell script on my desktop 5 times at the same time?


dtmilano's answer is correct.

Were you going to run this script on your own, or did you wish it to run at a specific time?  The latter would require a cron job, which is an easy thing to setup.

---

### Post by frog4044 on 2008-08-14
> **jinksys said:**
> dtmilano's answer is correct.

Were you going to run this script on your own, or did you wish it to run at a specific time?  The latter would require a cron job, which is an easy thing to setup.

No thanks I am just going to manually do it at random times but thank you.

---

