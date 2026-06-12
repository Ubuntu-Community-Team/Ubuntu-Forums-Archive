---
title: "Call PL/SQL procedure through CRON"
date: 2008-04-01
forum: Programming Talk
---

### Post by bioShark on 2008-04-01
Hi

I am a database developer, and currently working on a database that is located on a Linux (SuSE 10; I am a Ubuntu user, but still pretty rooky to Linux) server. I need to implement a cron job that calls a procedure.
I have already implemented several cron jobs, so I know how they work. I have also created shell scripts that are called through cron. Now my question is, how do I create a shell script that connects to SQL, and calls a procedure. Then I place in the cron file the call to the shell script.

Thx.

---

### Post by bioShark on 2008-04-02
I have figured it out by myself:

```
#!/bin/sh
<path>sqlplus user/psw @something.sql
```

---

