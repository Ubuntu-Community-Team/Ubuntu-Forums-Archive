---
title: "else command script not working"
date: 2014-01-01
forum: Programming Talk
---

### Post by prao060 on 2014-01-01
```
#!/bin/bash
iec9581on="
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
"
if [ "$amixer get 'IEC958',1" = "$iec9581on" ];
then
amixer set 'IEC958',1 off
else 
echo stuffed up
fi

```

are there issues with the script? the idea is to scan the output of "amixer get 'IEC958',1" and if it is on, execute "amixer set 'IEC958',1 off". for some reason this is not working. Instead, it always outputs "stuffed up", even when "amixer get 'IEC958',1" gives the message i assigned to "$iec958on" If you could modify the script to work and then explain your changes, that would be greatly appreciated.
Thanks in advance

---

### Post by sudodus on 2014-01-01
Maybe you forgot the parenthesis. Try

```
"$(amixer get 'IEC958',1)"
```

---

### Post by prao060 on 2014-01-01
nah, didn't work. im still having trouble
EDIT- this worked. Massive mind screwup when i said this didn't. i just didn't do this properly :) I LOVE U SUDODUS

---

### Post by Dave_L on 2014-01-01
Running the script with some debugging options may help:

```
sh -vx script
```

---

### Post by steeldriver on 2014-01-01
aside for the issue mentioned by sudodus, I think your other issue is the multiline string match - in particular your

```

iec9581on="
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
"

```

has an extra newline before and after - so it's never going to match with the "$(amixer get 'IEC958',1)" output, youd need to do EXACTLY

 ```

iec9581on="Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]"

```

Matching long strings like this is something I would try to avoid personally - is there a single field that you could extract and match against?

---

### Post by prao060 on 2014-01-01
sorry guys, false alarm. The first answer actually did work. I just needed to experiment a bit more. finally, here is my finalised script. It belongs on my desktop, and i set it to also output a log file there. I am very proud of this :) im just new to scripting.
```
#!/bin/bash
{ iec9581on="Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]"
  iec9581off="Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]"
if [ "$(amixer get 'IEC958',1)" = "$iec9581on" ]; then
 amixer set 'IEC958',1 off
elif [ "$(amixer get 'IEC958',1)" = "$iec9581off" ]; then
 echo FIRST ONE was already off
else 
 echo FIRST ONE had a problem
fi
iec9582on="Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]"
  iec9582off="Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]"
if [ "$(amixer get 'IEC958',2)" = "$iec9582on" ]; then
 amixer set 'IEC958',2 off
elif [ "$(amixer get 'IEC958',2)" = "$iec9582off" ]; then
 echo SECOND ONE was already of
else 
 echo SECOND ONE had a problem
fi
iec95816on="Simple mixer control 'IEC958',16
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]"
  iec95816off="Simple mixer control 'IEC958',16
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]"
if [ "$(amixer get 'IEC958',16)" = "$iec95816on" ]; then
 amixer set 'IEC958',16 off
elif [ "$(amixer get 'IEC958',16)" = "$iec95816off" ]; then
 echo THIRD ONE was already off
else 
 echo THIRD ONE had a problem
fi } > ~/Desktop/amixerredlight.log
```

however, to all who replied after, Thanks for your posts and they have given me a lot to work with after :)

---

### Post by prao060 on 2014-01-01
steeldriver- no, there isn't. I knew that would be easier, however, amixer wont give me a single field that would define on and off. The only way i could find was this lengthy field. Although, your shortening of the field helped as i was unable to perform this without it. Thanks a lot :D

Dave_L- I didn't know about this. Very interesting. yessss...... This is something i was looking for

---

### Post by steeldriver on 2014-01-01
Could you not do it with a regex match? something like

```

$ if [[ $(amixer get "'IEC958',0") =~ \[on\] ]]; then echo "On"; else echo "Not on"; fi

```

If you need case insensitive matching (on/ON) you can try setting the nocasematch shopt

---

### Post by prao060 on 2014-01-01
I only know of regex. I will look into it however

---

