---
title: "[SOLVED] small script problem"
date: 2007-11-05
forum: Programming Talk
---

### Post by Tuge on 2007-11-05
hello...

i'm trying to do a script that checks what groups user belongs to (on ad) and based on that mounts proper network places for this user. here is the part of the script that isn't working:

---

case $( wbinfo -r $USER ) in
     513 ) mount.cifs ... ;;
     514 ) mount.cifs ... ;;
          *) echo "not okay";;
esac

--- 

it always ends up to *) case... i've checked that wbinfo -r $USER returns proper groups on shell...

---

### Post by geirha on 2007-11-05
I don't have the wbinfo command, but according to the man-page, your command lists several groups. case will match all the output of the command, so if the output is "513 203 405" it will only match "case 513 203 405 )". I would try something like this:

```
for gid in $( id -G ) ; do
  if [ $gid -eq 513 ] ; then
    echo "We are in group 513"
    break
  elif [ $gid -eq 514 ] ; then
    echo "We are in group 514"
    break
  else
    echo "no match on $gid"
  fi
done
```

---

### Post by Tuge on 2007-11-05
Huge thanks! It worked like a charm...

---

