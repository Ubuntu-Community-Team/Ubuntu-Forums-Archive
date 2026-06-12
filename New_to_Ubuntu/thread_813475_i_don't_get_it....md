---
title: "i don't get it..."
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-30
i removed mplayer but it still continues this is what htop says.
Here is an image.
How do i kill it?

---

### Post by quelx on 2008-05-30
```
sudo killall -9 mplayer
```

---

### Post by cristo-father on 2008-05-30
> **quelx said:**
> ```
sudo killall -9 mplayer
```

Thanks. What does the nine stand for?

---

### Post by quelx on 2008-05-30
from **man kill** (hehe)

```
SIGNALS
       The  signals  listed  below  may  be available for use with kill.  When
       known constant, numbers and default behavior are shown.

       Name     Num   Action    Description
       0          0   n/a       exit code indicates if a signal may be sent
       ALRM      14   exit
       HUP        1   exit
       INT        2   exit
       KILL       9   exit      this signal may not be blocked
       PIPE      13   exit
       POLL           exit
       PROF           exit
       TERM      15   exit
```

and a better explanation than I could ever give

[http://www.linuxjournal.com/article/1332](http://www.linuxjournal.com/article/1332)

---

