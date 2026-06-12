---
title: "Bash script not working when copied to /etc/init.d"
date: 2007-07-20
forum: Programming Talk
---

### Post by RedTiger84 on 2007-07-20
Hello,

I wrote a small script to start a little tool. Since I want to start it at system startup and check whether the program is still running from time to time and restart it if necessary (kind of buggy little tool), I wrote the following:

```
#! /bin/bash

RES=`ps -A | grep toolname -c`

if [ $RES -lt 1 ]
then
        /usr/sbin/toolname > /dev/null 2> /dev/null &
        echo "tool started"

else
        echo "tool already running"
fi
```

This script works perfectly fine when placed in my homedir. But it stops working when copied to /etc/init.d. When the script is copied there and is called, it always tells me that the tool is already running. When I print the results of a `ps -A` command in this script, it returns a list processes that is definitely not up to date. If I run `ps -A` from this directory from the normal shell, everything is fine.

Can anybody explain this behaviour?

I am using Ubuntu 7.04 with all available updates.

Thanks and regards,
 Christoph

---

### Post by Mr. C. on 2007-07-20
Depending upon how processes are scheduled, your grep command itself will appear in ps output, causing you to match two lines of output, or one line which is the grep only.

Don't use that method to determine if your program is running.  You can use ps -C toolname instead.

Your startup script doesn't conform to the options required for an rc.d (init.d) type of script.  It must respond to the arguments **start**, **stop**, **restart**, **reload**, etc.  Take a look at the other init.d scripts for examples.

Othewise, place scripts you want started in the rc.local script.

MrC

---

