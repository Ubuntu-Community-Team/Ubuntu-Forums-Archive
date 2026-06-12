---
title: "[SOLVED] regular expression / shell script help needed please."
date: 2007-07-26
forum: Programming Talk
---

### Post by punky on 2007-07-26
Basically, i'm trying to write a shell script that wil capture the result of a ping, so I can monitor a server's uptime. Dunno if its the best way of doing it, but hey-ho.

Anyways, I just can't get the regexp right.

Here's what I have up to:

```
ping -c 1 -t 2 the.host.com | grep received
```

which outputs:

> 1 packets transmitted, 1 packets received, 0% packet loss

I want to isolate the "1" out of "1 packets received" as a variable. That way if its 1 the script can ignore it (server is up), or if its 0, server is down and the script will log it/email, whatever.

What's the best way of islotating the figure I need in the middle? 

Many thanx in advance.

---

### Post by jyba on 2007-07-26
Well, it's a bit of a manky solution but it seems to work...:lolflag:
```
ping -c 1 -t 2 the.host.com | grep -o ", [0-9]\+.*received" | grep -o "[0-9]\+"
```

---

### Post by stylishpants on 2007-07-26
Don't even bother capturing the output. Just check the return code.

```

if ping -q -c 1 -t 2 $HOST > /dev/null 2>&1
then
   echo "up"
else
   echo "down"
fi
```

---

### Post by compwiz18 on 2007-07-26
You can also capture the exit number of the command - if the server doesn't respond, ping will die with exit code 1, and if it works, the exit code is 0.  It might be easier then the other way, but since you already have it working I'm not sure it matters... :)

---

### Post by punky on 2007-07-27
Many thanx for all your help guys :)

---

