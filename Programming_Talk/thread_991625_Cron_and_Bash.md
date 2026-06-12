---
title: "Cron and Bash"
date: 2008-11-24
forum: Programming Talk
---

### Post by tlsarles on 2008-11-24
There is probably a better way of doing this... but here is the situation...

I have a process I want ran quite frequently.
What I have done so far is... make a bash script that runs a process every quarter of a second, and this is kicked off every min by cron 

```

#!/bin/bash
COUNTER=0
while [ $COUNTER -lt 240 ]; do
	php /var/www/game/step.php
	let COUNTER=COUNTER+1
	sleep 0.25
done

```

the problem with this approach is that the process being ran by the bash script doesn't complete before the next instance is run, which causes more to bog down, and eventually max the cpu.

Is there a way to make sure the previous process has completed before starting another? Does bash wait for the process to complete or fork it to the background?

---

### Post by rakris on 2008-11-24
If you want to run this every quarter second and u have already implemented that in the script, why do you need cron??? :O

Just add this script to sessions (at startup services)

---

### Post by geirha on 2008-11-25
Bash will wait for your step.php script to finish before continuing, unless your script forks into the background. So after step.php has run, it waits another 0.25 seconds before starting the next step.php. This means that it will take more than one minute to run through the loop, so your problem is probably that cron starts a new instance of your script before your old one has finished.

There are several ways you could go about this, but it all depends on the intentions. In cron, you could change the command to 
```
* * * * * pidof /path/to/script >/dev/null || /path/to/script
```
which will only run the script if the previous script has finished, that may cause a gap of nearly a minute in running your step.php scripts though.

Another way could be to use the same type of logic in your bash script, by starting the step.php scripts in the background, then after 0.25 seconds check if it is still running and only start a new one if it is finished.

```

#!/bin/bash
for i in `seq 240`; do
    pidof /var/www/game/step.php >/dev/null || php /var/www/game/step.php &
    sleep 0.25
done

```

I think the best way would be to implement this in step.php though, have it run constantly, doing whatever it does every .25 seconds. 

Also, I'm not sure its a good idea to have an offline script in the /var/www folder. If that folder is being served by apache, someone could instruct their browser to the step.php script and have it run when it shouldn't be run ...

---

### Post by tlsarles on 2008-11-29
I like that last approach. Thanks

---

### Post by Mr.Macdonald on 2008-11-30
one thing I saw is that you are running a loop 240 times, each time it sleeps .25 secs. 240 * .25 = 60 secs. the php script would have to run in 0 sec (light speed, infinitely fast, etc.).

how could you expect a program in cron, that takes at least a minute and reruns every minute, to not over lap.

if you want a process run forever, use recursion or
```
while ["" == ""];do <code>;done
```

---

