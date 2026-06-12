---
title: "huge issue with conky"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-05
my computer froze which is the first time this has ever happened since i installed ubuntu and now my conky will now show up when i reload...

the error message im getting is.

```
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: statfs '/media/disk1': No such file or directory
Conky: one or more $endif's are missing
Conky: desktop window (10000b6) is subwindow of root window (1a6)
Conky: window type - normal
Conky: drawing to created window (3a00001)
Conky: drawing to double buffer
Conky: statfs '/media/disk1': No such file or directory
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket

```

anyone know whats going on

---

### Post by PatrickMoore on 2008-07-05
it just loaded up but im still concerned

---

### Post by ChameleonDave on 2008-07-05
> **PatrickMoore said:**
> it just loaded up but im still concerned

It looks like there was a problem with a device being unmounted or removed.

But now you say it's fine?  Don't worry about it then.

---

### Post by PatrickMoore on 2008-07-05
> **ChameleonDave said:**
> It looks like there was a problem with a device being unmounted or removed.

But now you say it's fine?  Don't worry about it then.

i restarted and its not loading at all.

---

### Post by PatrickMoore on 2008-07-05
i think i fixed it i was missing a line

---

### Post by ChameleonDave on 2008-07-05
> **PatrickMoore said:**
> i restarted and its not loading at all.

Conky is the problem?

Do this:

```

sudo apt-get purge conky
sudo apt-get install conky
conky &

```

---

### Post by PatrickMoore on 2008-07-05
i fixed conky now my only issue is that its getting cut off at the bottom and i have to kill it then restart to show everything. any idea on how to fix that

---

