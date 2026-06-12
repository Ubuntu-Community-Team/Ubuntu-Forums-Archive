---
title: "Restarting pypanel in a script"
date: 2008-08-02
forum: Programming Talk
---

### Post by minus24 on 2008-08-02
I'm sure this is a trivial question, but here goes...

I'd like to add a script to restart pypanel from the openbox menu.  The following line works from a terminal:

> pkill pypanel && (sleep 2; pypanel) &

However, in a bash script, the kill works but pypanel is never restarted.  Any ideas?

---

### Post by ghostdog74 on 2008-08-02
show your script and how you executed it

---

### Post by minus24 on 2008-08-02
The script is:
```
#!/bin/bash
pkill pypanel && (sleep 2; pypanel) &

```

I execute it thus:
> ~/bin/restart_pypanel.sh

---

### Post by minus24 on 2008-08-06
The script also fails (i.e., pypanel is not restarted) if I execute it thus:
```
cd ~/scripts
./restart_pypanel.sh
```
Why the difference between executing those commands in a script vs. directly from a shell?

---

