---
title: "Start and Stop program"
date: 2008-04-13
forum: Programming Talk
---

### Post by saj0577 on 2008-04-13
After looking at [compiz-switch/]("http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/") i decided i wanted to make a simple program that does the following.

Checks to see if a program is running (i.e apache, amsn)
If its running stops it if its not running starts it.

What language would be best to do this and how would i go about doing this. i.e checking if a program is running.

Saj

---

### Post by nanotube on 2008-04-14
> **saj0577 said:**
> After looking at [compiz-switch/]("http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/") i decided i wanted to make a simple program that does the following.

Checks to see if a program is running (i.e apache, amsn)
If its running stops it if its not running starts it.

What language would be best to do this and how would i go about doing this. i.e checking if a program is running.

Saj

seems that this is a good job for a shell script. something along the lines of the code below should do the trick:

```

if $(ps ax |grep 'yourprogram' |grep -v 'grep'; then
    pkill 'yourprogram'
else
    /path/to/yourprogram &
```

---

### Post by ghostdog74 on 2008-04-14
```

#!/bin/bash
if [ ! -z "$(pidof program)" ] ;then  
    pkill program
else 
    /path/program &
fi

```

---

### Post by Jussi Kukkonen on 2008-04-14
Plain killing may work, but the right way to do something like this is to use start_stop_daemon with PIDFILE -- take a look at just about any startup script in /etc/init.d (hal should be a good example).

---

### Post by saj0577 on 2008-04-14
Cheers. 

Saj

---

