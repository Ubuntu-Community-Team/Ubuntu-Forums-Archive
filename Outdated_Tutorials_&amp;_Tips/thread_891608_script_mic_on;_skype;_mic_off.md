---
title: "script: mic on; skype; mic off"
date: 2008-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by f76 on 2008-08-16
Hi all, 
This is a very basic script for turning on the mic before skype goes on, and off as soon as it is turned off.. I run the script in my AWN launcher but u can run it anywhere.

U need to be using ALSA sound though (i think), and ive only done it on HARDY

First run "amixer controls" in term...
look for this line (or similar)in output:
```

numid=21,iface=MIXER,name='Front Mic Playback Switch'
```

Now we know that our mic switch is numid 21

Now run 'amixer cget numid=21'
```
numid=21,iface=MIXER,name='Front Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=off,off
```

now we se the values are "off, off" - in my case it is cuz i have 2 mics i think..

now start your alsa mixer gui and try this line or equivalent if u only have one mic or other numid:

```
amixer cset numid=21 on on
```

Did your mic turn on?

Now u can make a script that looks like this for example:
call it skypemicscript.sh

```
#! /bin/bash
amixer -q cset numid=21 on on
skype
amixer -q cset numid=21 off off
```

then run ' sudo chmod 755 skypemicscript.sh'
and 'sudo mv skypemicscript.sh /usr/bin/skypemicscript.sh'

now when u run skypemicscript.sh from term or any launcher the mic will be turned on before skye is run, and off after..

---

