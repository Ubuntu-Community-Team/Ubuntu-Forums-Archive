---
title: "I need some help with a very simple bash file..."
date: 2008-03-07
forum: Programming Talk
---

### Post by Yes on 2008-03-07
I'm trying to write a program that will output the current state of mpd.

Here's what I have so far:

```
#!bin/sh

mpc_stopped=`exec mpc | grep stopped | cut -c 2-3`
mpc_paused=`exec mpc | grep paused | cut -c 2-3`
mpc_playing=`exec mpc | grep playing | cut -c 2-3`
echo $mpc_stopped
echo $mpc_paused
echo $mpc_playing

if [ "$mpc_stopped" == "st"]
then
	echo "STOPPED"
elif ["$mpc_paused" == "pa"]
then
	echo "PAUSED"
elif ["$mpc_playing" == "pl"]
then
	echo "PLAYING"
fi
```

And here's the errors...

```



pl
[: 19: missing ]
[: 19: missing ]
mpc.sh: 19: [pl: not found
```

So I have no idea why it's doing that.  Can anyone help?

---

### Post by olejorgen on 2008-03-07
I think you need ; after if [ ..], like this if [ ... ]**;**, also you need to separate the ] and [ from the test arguments with a space.

```

#!bin/sh

mpc_stopped=`exec mpc | grep stopped | cut -c 2-3`
mpc_paused=`exec mpc | grep paused | cut -c 2-3`
mpc_playing=`exec mpc | grep playing | cut -c 2-3`
echo $mpc_stopped
echo $mpc_paused
echo $mpc_playing

if [ "$mpc_stopped" == "st" ]; # [ and ] must be "surrounded" by spaces
then
	echo "STOPPED"
elif [ "$mpc_paused" == "pa" ];
then
	echo "PAUSED"
elif [ "$mpc_playing" == "pl" ];
then
	echo "PLAYING"
fi
```

---

### Post by Yes on 2008-03-07
Ok, thanks.  But now I have a new error:

```
[: 19: ==: unexpected operator
[: 19: ==: unexpected operator
[: 19: ==: unexpected operator
```

You do use == to compare two strings, don't you?

---

### Post by WW on 2008-03-07
Be sure you have spaces after [ and before ].

---

### Post by Yes on 2008-03-07
Like 

```
if [ "$mpc_stopped" == "$st" ];
```

right?

---

### Post by ghostdog74 on 2008-03-07
use case, neater. and i believe you only have 1 type of status output..

```

mpa_status=`mpc | egrep "stopped|paused|playing" | cut -c 2-3`
case $mpa_status in
 "st" ) echo "stop";;
 "pa") echo "pause";;
 "pl" ) echo "play";;
esac

```

---

### Post by Whiffle on 2008-03-08
#!bin/sh

should be

#!/bin/sh

---

### Post by olejorgen on 2008-03-08
Either use only one "=", or use double  brackets. ie. [[ ... ]] or [ ... = ... ]

---

