---
title: "Script help wakeonlan"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by bilboubu on 2012-08-15
Hi I want to modify this start script to that it only runs if the remote computer is off.

#!/bin/bash

/usr/bin/wakeonlan xx:xx:xx:xx:xx:xx

sleep 60

exit



I presume some sort of if statement required?

---

### Post by bilboubu on 2012-08-15
is it something like ping -q -c1 -W5 ?

---

### Post by bilboubu on 2012-08-15
The below seems to work from the command line but I cant get it to work on start up.


ping -c 2 -s 100 -w 1 192.168.0.2 >/dev/null
if [ $? -eq 1 ] ; then
/usr/bin/wakeonlan 00:1d:92:dd:1a:0d
sleep 45
else
echo 'one'
fi

exit 0

tried it in rc.local & /etc/xbmc/live.d no joy.

---

