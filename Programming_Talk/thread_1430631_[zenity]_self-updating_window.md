---
title: "[zenity] self-updating window?"
date: 2010-03-15
forum: Programming Talk
---

### Post by breek on 2010-03-15
using zenity i've done this script, a simple gui for upsc command (nut) that reports ups status.
status is updated every 15 seconds but new informations are added after old ones, not replaced.
is there a way to clear old infos in order to have only last status?

thanx


here is the script

```


#!/bin/bash

(
while true ;
do
date +%F_%T ;
echo "" ;
upsc myups 2>&1 ;
sleep 15 ;
echo "" ;
echo "------------------------------------------------" ;
echo "" ;
done
) | zenity --text-info --title="ups status" --height=500 --width=300


```

---

### Post by cubeist on 2010-03-15
I don't think this can be done in zenity.  just so I understand, your trying to keep the window open all the time and just show the updates every 15 seconds?

if this is the case, I would recommend a conky script that is permanent on your desktop.

or some other options are notify-send or whiptail

---

### Post by breek on 2010-03-15
yes, what i'm trying to do is to check this infos for a certain time, but not always.

to me the most interesting seems notify-send.

i did this script

```

while true ;
do
notify-send "ups status" "`upsc myups 2>&1`" ;
sleep 15 ;
done

```

it's ok if it is launched from a terminal, since it can be closed using control+c but how can it be stopped if it is launched from an icon?

thanx

---

### Post by aeiah on 2010-03-16
you'd have to do 
```
killall 'scriptname'
```

or make a toggle script, so when you click the icon it stops the program (and notifies you via notify-send that it's closing or something) if it's already running. this script has to be a different one to the ups_script because if it checked for its own existence, it would always return true.

```


#!/bin/sh

# Test to see if scriptname is already running
if ps -ef|grep -v grep|grep -i ups_script
then
# use send-notify to tell user that script is about to close
send-notify 'ups script is closing'
#
killall ups_script

exit
else
#launch script
./ups_script &

fi
exit


```

---

### Post by breek on 2010-03-17
that's really good, especially the double grep part ;)
but are the "exit" necessary?

i've made my script... i need time to test it and then i'll put it here on the forum :)

thanx!

---

### Post by roccivic on 2010-03-18
[PHP]#!/bin/bash
(
while true ;
do
date=$(date +%F_%T);
ups=$(upsc myups 2>&1);
echo "message: $date \n $ups";
sleep 15;
done
) | zenity --notification --listen[/PHP]

Another alternative, but I guess would drive anyone nuts after a while...

---

### Post by cubeist on 2010-03-19
> **roccivic said:**
> [PHP]#!/bin/bash
(
while true ;
do
date=$(date +%F_%T);
ups=$(upsc myups 2>&1);
echo "message: $date \n $ups";
sleep 15;
done
) | zenity --notification --listen[/PHP]

Another alternative, but I guess would drive anyone nuts after a while...

That looks like a bash script, not PHP.

---

### Post by roccivic on 2010-03-19
Does it now?

Well, since the only easy enough way to get some color in the script is to wrap it in PHP CODE tags, that's exactly what I done. The syntax is close enough for highlighting purposes :P

---

### Post by cubeist on 2010-03-19
> **roccivic said:**
> 
Well, since the only easy enough way to get some color in the script is to wrap it in PHP CODE tags, that's exactly what I done. The syntax is close enough for highlighting purposes :P

Huh! I didn't know that, cool :P

---

