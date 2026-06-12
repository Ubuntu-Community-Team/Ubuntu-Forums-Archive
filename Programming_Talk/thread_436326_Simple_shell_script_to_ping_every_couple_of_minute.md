---
title: "Simple shell script to ping every couple of minutes?"
date: 2007-05-07
forum: Programming Talk
---

### Post by hypersire on 2007-05-07
Hi all - I keep getting kicked off my remote desktop connection (due to inactivity) so I am trying to write a little shell script that will simply ping the remote computer every 2 minutes.

ping -c 4 ipaddress
sleep 120

repeat 

What code could I use to repeat the ping every 2 minutes?

Thanks!

---

### Post by Ayman on 2007-05-07
This is an infinite loop in Bash:
```
while [ 1 ]; do
  # Commands here.
done
```

---

### Post by hypersire on 2007-05-07
Thanks very much Ayman!

---

### Post by bashologist on 2007-05-07
A few other ways of doing an infinite loop:

```
for ((;;)) do
	echo "enter commands here"
	sleep 120
done

while true; do
	echo "enter commands here"
	sleep 120
done
```

---

### Post by DeadEyes on 2007-05-08
what about a simply using the interval switch
ping -i120 ipaddress

---

### Post by hypersire on 2007-05-09
> **DeadEyes said:**
> what about a simply using the interval switch
ping -i120 ipaddress

Even better! I didn't know about the ping interval switch! Thanks!

The only benefit to using the shell script with a loop and and the count flag is that the ping operation completes each iteration, showing you the full stats. With the -i method you won't see the full stats till you end the operation. I don't care about the stats so I am using the ping -i method.

And it works great - my remote desktop connection no longer kicks me off! I just ping the server every 5 minutes.

---

### Post by bLUEbYTE on 2007-05-09
Cron it.

---

