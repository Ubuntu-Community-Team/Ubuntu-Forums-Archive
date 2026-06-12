---
title: "Cron Job Help"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Go3Team on 2008-10-04
I'm trying to do a script that will ping something like google, and if the ping fails, it resets a router using an X10 device. (long story short, the router is a wireless client bridge, but not designed as such and needs periodic reboots for the wireless side to work again)

I found this script but need help in getting it to how I need it.
```

#!/bin/bash
 
# add ip / hostname separated by while space
HOSTS="cyberciti.biz theos.in router"
 
# no ping request
COUNT=1
 
# email report when
SUBJECT="Ping failed"
EMAILID="me@mydomain.com"
for myHost in $HOSTS
do
  count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{ print $2 }' | awk '{ print $1 }')
  if [ $count -eq 0 ]; then
    # 100% failed
    echo "Host : $myHost is down (ping failed) at $(date)" | mail -s "$SUBJECT" $EMAILID
  fi
done
```

I don't need it emailed to me, I need the following commands done which is done from the command line:

```

heyu off c3

```

wait for 15-30 seconds, then:

```

heyu on c3

```

Any help would be appreciated.

---

### Post by hyper_ch on 2008-10-04
[http://www.ss64.com/bash/sleep.html](http://www.ss64.com/bash/sleep.html)

---

### Post by mike2357 on 2008-10-04
I'm not sure exactly what you're trying to do, but the command line has a "sleep" command that will wait for a specified number of seconds.  So you could write a script as follows:

#!/bin/sh
put_your_first_command_here
sleep 30
put_your_second_command_here

---

### Post by bodhi.zazen on 2008-10-04
Sounds like you need to change the if from :

> if [ $count -eq 0 ]; then
    # 100% failed
    echo "Host : $myHost is down (ping failed) at $(date)" | mail -s "$SUBJECT" $EMAILID
  fito

```

 if [ $count -eq 0 ]; then
    # 100% failed
    
heyu off c3
sleep 30
heyu off c3
fi

```Then to make it a cron job, use sudo crontab -e

[http://www.codewalkers.com/c/a/Server-Administration/Introduction-to-crontab/](http://www.codewalkers.com/c/a/Server-Administration/Introduction-to-crontab/)

---

### Post by unutbu on 2008-10-04
If you take the script posted in post #1, and change the HOSTS line to

HOSTS="phony.address"

and run the script, I think you'll get the following:

ping: unknown host phony.address
/home/me/bin/test.sh: line 16: [: -eq: unary operator expected

When given a phony address (or any address when your network connection is down)
the variable count gets set to an empty string -- it is not a number, so the script exits with an error instead of completing.

Perhaps try this instead:
```

#!/bin/bash
 
# add ip / hostname separated by while space
HOSTS="google.com xyz.blah gzaouhtn routerip"
 
for myHost in $HOSTS; do
    count=$(ping -c 1 "$myHost" 2>/dev/null)
    if [ -z "$count" ]; then
	echo "Host : $myHost is down (ping failed) at $(date)" 
	heyu off c3
	sleep 15
	heyu on c3
    else
	echo "$myHost connected"
    fi
done

```

Then type
```

sudo crontab -e
```

and add a line like this:
```

*/15 * * * *  /path/to/isconnected.sh
```
This will run the isconnected.sh script once every 15 minutes.

---

### Post by Go3Team on 2008-10-04
> **unutbu said:**
> 

This will run the isconnected.sh script once every 15 minutes.

Thanks unutbu, the script works great.

---

