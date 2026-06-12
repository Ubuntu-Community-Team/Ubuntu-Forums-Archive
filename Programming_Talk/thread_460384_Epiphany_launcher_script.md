---
title: "Epiphany launcher script"
date: 2007-05-31
forum: Programming Talk
---

### Post by htor on 2007-05-31
Hi,
Here is the script (I didn't want to deal with writing epiphany extensions) that I use in my epiphany launcher in order to keep him clean :

```
#! /bin/sh

epiphany &
sleep 5

while [ `ps -C epiphany -o cmd|wc -w` -eq 2 ]
do
sleep 5
done

rm -r /home/papa/.gnome2/epiphany/mozilla/epiphany/Cache 
rm /home/papa/.gnome2/epiphany/mozilla/epiphany/cookies.txt 
rm /home/papa/.gnome2/epiphany/ephy-history.xml
```

What do you think? anyone has suggestions how can I to improve this script ?

---

### Post by seamless on 2007-05-31
Another way you could check to see if it is still running is to check /proc for the pid instead of calling ps every time. You may want to add a redirect for any errors with the rm in case one of th items you are deleting doesn't exist. (think you call the script twice).

The script would be changed to look like this:
```
#! /bin/sh
epiphany &
PID=$!
sleep 5

while [ -d /proc/$PID ]; do
	sleep 5
done

rm -r /home/papa/.gnome2/epiphany/mozilla/epiphany/Cache 2>&-
rm /home/papa/.gnome2/epiphany/mozilla/epiphany/cookies.txt 2>&-
rm /home/papa/.gnome2/epiphany/ephy-history.xml 2>&-
```

---

### Post by htor on 2007-06-01
Thanks, your version looks much more elegant.

---

