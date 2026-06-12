---
title: "the path from root ..."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Langstracht on 2008-09-23
I wonder if anyone can tell me why this command:

0 15 * * * /usr/bin/update-manager

does not start up the update-manager.

I imagine it's because I don't know what I'm doing with the path.  But, what should it (the path) be?

Thanks in advance for any and all help.

---

### Post by Mornedhel on 2008-09-23
```
which update-manager
```

Will output the location of the update-manager binary.

---

### Post by Langstracht on 2008-09-23
I'm not sure that I understand your question ... but the one

"written by Michiel Sikkes and Michael Vogt as an apt update manager for the GNOME Desktop of the Ubuntu distribution."

Is that what you are asking?

---

### Post by kellemes on 2008-09-23
> **Langstracht said:**
> I'm not sure that I understand your question ... but the one

"written by Michiel Sikkes and Michael Vogt as an apt update manager for the GNOME Desktop of the Ubuntu distribution."

Is that what you are asking?

No, he is suggesting to open a terminal window and start typing..
```
which update-manager
```
This will show you the path to the update-manager package.

Assuming update-manager is in /usr/bin you should type..

```
gksudo /usr/bin/update-manager
```

---

### Post by Mornedhel on 2008-09-23
Uh, sorry, it was not really a question. I meant the "which" command :

```
NAME
       which - locate a command

SYNOPSIS
       which [-a] filename ...

DESCRIPTION
       which returns the pathnames of the files which would be executed in the
       current environment, had its arguments been  given  as  commands  in  a
       strictly  POSIX-conformant  shell.   It does this by searching the PATH
       for executable files matching the names of the arguments.

```

See also : whereis. (And just for kicks, note the commands : who and whoami.)

---

### Post by Langstracht on 2008-09-23
O.k. sorry for my stupidity/misinterpretation.

The response to "which update-manager" is "/usr/bin/update-manager", which, if I understand whats going on here, takes us (well me) right back to where I started ...

---

### Post by Mornedhel on 2008-09-23
> **kellemes said:**
> Assuming update-manager is in /usr/bin you should type..

```
gksudo /usr/bin/update-manager
```

Did you try it with gksudo as kellemes suggested ? I don't have update-manager installed anymore since I apt-get update/upgrade manually, but it's possible it requires admin rights to run.

Also, are you sure you are not confusing update-manager with update-notifier ? Does "ps aux" return update-manager in the list after the cron job supposedly starts ?

---

### Post by Langstracht on 2008-09-23
I guess I misunderstood again.


I thought "type it" meant in terminal - where simply usr/bin/update-manager works just fine (which is why I thought it would work in crontab).

However I will change the crontab "command" and see what happens.

---

