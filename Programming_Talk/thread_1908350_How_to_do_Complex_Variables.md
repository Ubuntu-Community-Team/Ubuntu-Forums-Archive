---
title: "How to do Complex Variables"
date: 2012-01-13
forum: Programming Talk
---

### Post by Fenlig on 2012-01-13
Hey Guys,

So im a novice with scripting so be gental.

Okay this is my script:
> 
#!/bin/bash

echo "What process do you need?"
read PROCESS
INPUT="ps aux |grep $PROCESS | grep -v grep | awk '{print $2}'"
kill $INPUT


Now the INPUT is what is giving me issues as when it runs this line the $process doesnt get picked up. Can anyone suggest a better way of doing this?

Kind regards,
Fenlig

---

### Post by nothingspecial on 2012-01-13
You need to use command substitution. In your script $INPUT is the string inside the double quotes. So instead of 

```
INPUT="ps aux |grep $PROCESS | grep -v grep | awk '{print $2}'"
```

You need

```
INPUT=$(ps aux |grep $PROCESS | grep -v grep | awk '{print $2}')
```

See here [http://mywiki.wooledge.org/BashGuide/SpecialCharacters](http://mywiki.wooledge.org/BashGuide/SpecialCharacters)

Also always quote your variables and use lower case variables.

---

### Post by Fenlig on 2012-01-13
> **nothingspecial said:**
> You need to use command substitution. In your script $INPUT is the string inside the double quotes. So instead of 

```
INPUT="ps aux |grep $PROCESS | grep -v grep | awk '{print $2}'"
```You need

```
INPUT=$(ps aux |grep $PROCESS | grep -v grep | awk '{print $2}')
```See here [http://mywiki.wooledge.org/BashGuide/SpecialCharacters](http://mywiki.wooledge.org/BashGuide/SpecialCharacters)

Also always quote your variables and use lower case variables.


Aw wow thanks dude this is some good stuff thanks :)

---

