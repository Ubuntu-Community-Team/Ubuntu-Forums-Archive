---
title: "How can I test if a shell script is already running?"
date: 2007-10-06
forum: Programming Talk
---

### Post by kvonb on 2007-10-06
-

---

### Post by dwhitney67 on 2007-10-06
Try something like:

```
#!/bin/sh

REMOTE_IP=www.yahoo.com
MY_PROCESS=foo
CHECK_DELAY=1

while true
do
        ping -c 1 $REMOTE_IP > /dev/null

        if [ $? != 0 ]
        then
                PROC_STAT=`ps -w | grep $MY_PROCESS | cut -d " " -f7`
                if [ "${PROC_STAT}x" == "x" ]
                then
                        echo $MY_PROCESS is not running
                else
                        echo $MY_PROCESS is running
                fi
        fi

        sleep $CHECK_DELAY
done

```

---

### Post by kvonb on 2007-10-06
-

---

