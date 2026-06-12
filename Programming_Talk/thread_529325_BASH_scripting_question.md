---
title: "BASH scripting question"
date: 2007-08-19
forum: Programming Talk
---

### Post by Greeface on 2007-08-19
I have a BASH script, and in this script I want to run a command.  This command doesn't exit, so I want my script to start the command and then move on leaving the command to run.  When the script exits I still want this command to be running.  I have no idea how to do this, so any help is appreciated.

Thanks

---

### Post by Compyx on 2007-08-19
If I'm not mistaken, you can put an ampersand (&) behind the command you want to run and detach from the script, something like:
```

compiz --replace **&**

```

---

### Post by Greeface on 2007-08-19
I'll give that a shot, thanks.

Edit:  Works like a charm, why didn't I think of this? :)

---

