---
title: "Make a script work all the time"
date: 2012-12-01
forum: Programming Talk
---

### Post by cazz on 2012-12-01
What is the best idea to run a script all the time

I like to run a script every 60 sec and is is crontab the best idea or a deamon


I have never work with deamon before?

---

### Post by cybergalvez on 2012-12-01
> **cazz said:**
> What is the best idea to run a script all the time

I like to run a script every 60 sec and is is crontab the best idea or a deamon


I have never work with deamon before?

it depends on what you are trying to do, will the script alway be done within the 60sec time limit? what happends if you start more than one instance of the sript? 

In general crontab is designed to do exactly what you are asking run scrtipts at specific time intervals, however given the frequency you might want to simply have a deamon running all the time that can do what you need and monitor the outcome.

Sorry, I guess I would need more info before commiting to an answer

---

### Post by cazz on 2012-12-01
Ahh ok

It going to read if a computer is close by ping it for me.
if it close by it going to active a camera so it take a snapshot.

So as long the computer is not close it going to take a picture every 60 sec.

---

### Post by pbrane on 2012-12-01
Another way, without cron is to add this to the end of your script.
```

sleep $delay
exec $0

```

Where **$delay** would be whatever delay you want in seconds. And **exec $0** simply executes this script again.

---

### Post by cazz on 2012-12-01
Hmm ok

I can do it three way then

I try now with crontab to see if it works and does not use to much CPU or anything like that.

---

### Post by KdotJ on 2012-12-01
Chances are, cron is already running on your machine anyway
.. so CPU cycles shouldn't be an issue as far as cron is concerned

---

