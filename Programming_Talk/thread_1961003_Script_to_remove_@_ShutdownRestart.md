---
title: "Script to remove @ Shutdown/Restart"
date: 2012-04-18
forum: Programming Talk
---

### Post by frogotronic on 2012-04-18
Hi,

  I need some help writing a script (and where to put it, pm-utils???) to manually unload tangerine at shutdown and/or restart.

- CH

---

### Post by frogotronic on 2012-04-18
Something like this...


```
#!/bin/bash
#Code from http://ubuntuforums.org/showthread.php?t=1387211

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    rfkill block tangerine
    ;;
    thaw|resume)
    rfkill unblock tangerine
    ;;
    *)
    ;;
esac

exit
```

and would it go in /etc/pm/power.d  ?

- CH

---

### Post by pafoo on 2012-04-18
You need to create a case script and put it in the /etc/rc.d/rc3 ot rc5. Those are the start up and stop scripts. You can copy any other startup script and just modify it for your purpose. Just make sure the name of the script starts with a captial letter. That way everytime your server stops the program will stop etc.

---

### Post by frogotronic on 2012-04-18
> **pafoo said:**
> You need to create a case script and put it in the /etc/rc.d/rc3 ot rc5. Those are the start up and stop scripts. You can copy any other startup script and just modify it for your purpose. Just make sure the name of the script starts with a captial letter. That way everytime your server stops the program will stop etc.

hmmm...those look really complicated...

---

