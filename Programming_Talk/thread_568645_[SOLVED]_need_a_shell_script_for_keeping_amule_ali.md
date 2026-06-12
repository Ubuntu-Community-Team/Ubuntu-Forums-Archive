---
title: "[SOLVED] need a shell script for keeping amule alive..."
date: 2007-10-06
forum: Programming Talk
---

### Post by hopelessone on 2007-10-06
hi all,

can someone help me make a shell script keep amule alive, it keeps crashing overnight sometime...i checked amule forums no help..

i want to put a timer on the script to check every 30 mins if running if not start amule...so far i got....

```
#!/bin/sh
alarm -r a +3000
	
function a.alarm {

SERVICE='amule'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE running, everything is fine"
else
    echo "$SERVICE is not running"
   /aMule/bin/amule start
fi
}
```

but i don't know if this will work?...as im away from my linux box...

thanks

---

### Post by Zootropo on 2007-10-06
Why don't you create a cron job?

---

### Post by hopelessone on 2007-10-06
hi,

thanks did it...

```
if [ "$(pidof amule)" ] 
then
  echo "running amule" > ~/test.txt
else
  echo "not running amule" > ~/test.txt
  exec /usr/bin/amule 
fi
```

how can i skip```
 then
  echo "running amule" > ~/test.txt
``` ???

thanks

---

### Post by dwhitney67 on 2007-10-06
It seems that you do not care about the PID itself, but only for the info as to whether amule is running.

Thus something like this would probably suffice:

```
#!/bin/sh

pidof amule >/dev/null

if [ $? != 0 ]
then
    # amule is not running; start it (again)
    exec /usr/bin/amule
fi
```

---

### Post by hopelessone on 2007-10-07
cool thanks...

how can i log the times its not there?

i wanna say something like:

amule went down at Sunday 12:54:18 restarting...
amule went down at Monday 17:54:18 restarting...

so far i got 
```
date +%A%_T > ~/amule.log
```

but it writes over the file each time...

thanks

---

### Post by dwhitney67 on 2007-10-07
You were almost there. You need to use >> in lieu of the single >.  Therefore:

```
echo "amule is not running as of `date +%c`; restarting..." >> ~/amule.log
```


P.S.  Note the single-quotes surrounding the date command are the ones paired with the ~ key on your keyboard.

---

### Post by hopelessone on 2007-10-07
Thanks !!

---

### Post by dwhitney67 on 2007-10-07
You're welcome.  Before you get all excited though, I would add to your script a delay of some sort so that it does "constantly" check if amule is running or not.

Alternatively, use Zootropo's advice and set up a cron job that will call your script, say every 5 minutes, or whatever time period you choose.

---

