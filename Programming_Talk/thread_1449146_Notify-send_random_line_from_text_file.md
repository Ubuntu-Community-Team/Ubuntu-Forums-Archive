---
title: "Notify-send random line from text file"
date: 2010-04-07
forum: Programming Talk
---

### Post by skooter1121 on 2010-04-07
I've got a text file of famous quotes. Each quote is on a separate line. I'd like to send a random line to be displayed by notify-send   in the notify-osd.

notify-send -i /home/stephen/SYSTEM/Icons/MAIN/bulb2.png "Keyboard Templates" "`tail /home/stephen/Template.txt`"

Will give me a popup with a title of Keyboard Templates and then display the text of Template.txt.

I know that I'm limited to 3 lines for the "Title" and ten lines for the "Body".

I can't figure out how to use tail to pull a random line.

Any suggestions?

-S

---

### Post by sisco311 on 2010-04-07
```
shuf -n1 path/to/file
```
or
```
rl -c1 path/to/file
```

---

### Post by skooter1121 on 2010-04-07
Thanx.

Both worked, after I installed rl (random-lines) ans shuf (shuffle).

Any benefit to using one over the other?

-S

---

### Post by skooter1121 on 2010-04-07
sisco311

Thought you might like to see how I used your suggestions. I have it set to run every 20 minutes.

Next I'll try to have e-speak say it also. 


Again,

THANX
-S

---

### Post by kaibob on 2010-04-07
> **skooter1121 said:**
> ...I can't figure out how to use tail to pull a random line....
The solution provided by sisco311 is best. Just for the sake of completeness, you can use the sort command with the random-sort option and tail:

```
sort -R file | tail -n1
```

---

### Post by sisco311 on 2010-04-07
> **skooter1121 said:**
> sisco311

Thought you might like to see how I used your suggestions. I have it set to run every 20 minutes.

Next I'll try to have e-speak say it also. 


Again,

THANX
-S

You're welcome!

Thanks for sharing your script. To be honest, I have no idea about the differences between rl and shuf.

I also like to play with notify-send, here is the script I use to turn on/off my monitor. It's highly customized for my needs so I doubt it's useful for others :)

```
 #!/bin/bash

STANDBY=600
SUSPEND=900
OFF=1200

STANDBYOFF=2
SUSPENDOFF=8
OFFOFF=16

ICONPATH="/home/sisco/.icons/notify"
ONICON="monitor-on.png"
OFFICON1="monitor-off-vid.png"
OFFICON2="monitor-off.png"

NOTIFYARG="-h string:x-canonical-private-synchronous:true -h string:x-canonical-private-icon-only: \"notify\" "

function message
{
  echo "$*" > /dev/stderr
} 

function onoff 
{
  [ $(xset q | awk '/Standby/ && /Off/{print $2}') -eq $STANDBYOFF ] && turnon || turnoff
}

function turnoff
{
  xset dpms "$STANDBYOFF" "$SUSPENDOFF" "$OFFOFF"
  [ "$(pidof mplayer)" ] && \
    notify-send -i $ICONPATH/$OFFICON1 $NOTIFYARG || \
    notify-send -i $ICONPATH/$OFFICON2 $NOTIFYARG
  message "turn off"
}

function turnon 
{
  STAT="$(xset q | grep "Monitor is On")"
  xset dpms "$STANDBY" "$SUSPEND" "$OFF"
  xset dpms force on
  [ "$STAT" ] || sleep 5 && echo notify-send -i $ICONPATH/$ONICON $NOTIFYARG  
  notify-send -i $ICONPATH/$ONICON $NOTIFYARG
  message "turn on"
  message $STAT
}

onoff

```

A couple of weeks ago my hard disk crashed & I lost my other scripts, but that's another story...

---

