---
title: "[C] Need Just a Bit of Help! (System Command)"
date: 2010-11-21
forum: Programming Talk
---

### Post by The Elite Noob on 2010-11-21
**Hiya!** :KS

I was programming in **C** and needed to use some command in the **bash shell directly** and output in my C command.

Basically I'm trying to use **[ notify-send Test "This is a Test 123." ]**
in my C program using **system():**
However it is not working since it is not being executed in the bash shell.
So how can i run this command from **my C program into the bash shell**?

**Thanks!**
**=D**

:KS

---

### Post by spjackson on 2010-11-22
Why do you think that the shell used is the cause of your problem? If that really is what's wrong, then you cannot change the shell that is executed - it will always be /bin/sh. However, if you need bash syntax, then the normal way around this is either to do system("/bin/bash -c 'The Command'") or to place the command in a script and call that from system.

---

### Post by ziekfiguur on 2010-11-22
You could also use a combination of FORK(2) and EXEC(3), that would be a bit more complex, but you have much more control over what happens.
In combination with PIPE(2) and DUP(2) you could also read the output of the executed command from your program.

for more info, run `man 2 fork', `man 3 exec' etc. in a terminal

---

### Post by The Elite Noob on 2010-11-22
> **spjackson said:**
> Why do you think that the shell used is the cause of your problem? If that really is what's wrong, then you cannot change the shell that is executed - it will always be /bin/sh. However, if you need bash syntax, then the normal way around this is either to do system("/bin/bash -c 'The Command'") or to place the command in a script and call that from system.

[B]Thanks!
That works Perfectly Thank You Mate![/B]

:KS:KS

---

### Post by karlwbloedorn on 2010-11-23
You can also use the notify library directly:


#include <libnotify/notification.h>
#include <libnotify/notify-enum-types.h>
#include <libnotify/notify.h>

The functions are:
notify_notification_new
notify_notification_show

Heres some documentation:
[http://www.galago-project.org/docs/api/libnotify/notification_8h-source.html](http://www.galago-project.org/docs/api/libnotify/notification_8h-source.html)

---

