---
title: "Loading script outputs as variables concurrently"
date: 2015-12-12
forum: Programming Talk
---

### Post by jack163 on 2015-12-12
I am having trouble with how to properly word this issue which is making it hard to lookup. Sorry if this has been asked and answered but I haven’t found it.

I have a Bash script that grabs the state of multiple remote light switch and tells me if it is "ON" or "OFF". I then call that script from another in order to build a web front end for easy viewing.
I load the responses into variables like:
SW1=$(./Light state 1)
SW2=$(./Light state 2)
...
which works.
I want to run these variable assignments concurrently so I don't have to wait the 10 seconds for each two second call to run 5 times.
I have tried.
SW1=$(./Light state 1 &)
SW1=$(./Light state 1) &
SW1=`./Light state 1 &`
SW1=`./Light state 1` &
I have even built Functions that call for the data and have run them using '&'... It either takes the same amount of time or the variable is empty.
I have proven that I can run the primary call script concurrently so I know that isn't the road block.
Any Ideas?

The equipment is Ubuntu server 14.04.3 LTS

---

### Post by blm-ubunet on 2015-12-12
I guess the returned value assignment to var stops each call to light running in parallel.
Returning a variable value from a sub-shell looks tricky, easier to use the trusty filesystem.

This method (using files works)
```
#!/bin/bash

(./light 1 > sw1) &
(./light 2 > sw2) &
(./light 3 > sw3) &
wait

cat sw1 sw2 sw3
```

where "light" is just:
```
#!/bin/bash

echo $1
sleep 2
```
The "sleep" is just there to show that all (3) sub-shells sleep concurrently.

Skinning dead cats...

---

### Post by kkaldroma on 2015-12-13
Great Idea (OP by the way, the UBUone SSO is playing with my account again).
I have implemented your suggestion but am having problems with the accuracy of the data being retrieved. I can't tell if it is the code or if the remote switches are acting up again.
I have had to write the sw? files to the tmp directory since www-data apparently can't write to the local file it has created... very odd.
But, mission accomplished, the system is very fast.

For the accuracy problem I have added sleep breaks between runs to prevent the same script from being called in rapid secession in case that is the problem, no luck yet.
I will continue playing with the code and if I get it working as expected I will post any fixes and mark as solved.

Thanks again.

---

### Post by blm-ubunet on 2015-12-13
The point of using sub-shells () and not waiting for return was so all calls to "Light" script were in parallel.

Your code in "Light" script has to consider/handle any required resource locking.
If each "Light" script instance polls a different/independent networked device then you shouldn't need to do anything.
If they share the same server interface it should still work if server can handle multiple connections.

Using temporary files makes the variables persistent between calls to the same switch; you might want to set the file "value" to unread/zero.

---

### Post by kkaldroma on 2015-12-15
I guess the SSO issues aren't fixed because I cannot mark the Thread as SOLVED....
Thanks blm-ubunet, 
I wipe out the temp files and things are a bit cleaner.
Part of the issue is that I am using wemo switches that are independent and Insteon switches that all use the same coms HUB. The HUB isn't happy when it is flooded with requests so there is some more tweaking to do.

[SOLVED]

---

### Post by blm-ubunet on 2015-12-18
Probably the HUB device only handles limited (max 4?) connections.
You could try to limit the packet rate to certain IP address of the HUB.

---

