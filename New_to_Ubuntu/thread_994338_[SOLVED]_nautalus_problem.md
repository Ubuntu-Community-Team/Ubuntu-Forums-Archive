---
title: "[SOLVED] nautalus problem"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-26
Hi, Can anyone help me?

My os has become slow, Bash doesn't seem to reveal all I have in the Trash, which I cant open:

nick@nick-desktop:~$ ls -lh .local/share/Trash
total 8.0K
drwx------ 2 nick nick 4.0K 2008-11-26 21:21 files
drwx------ 2 nick nick 4.0K 2008-11-26 21:21 info
nick@nick-desktop:~$ 


-And N is throwing up an error message:

" Nautilus cannot be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem."

---

### Post by Olivier2371 on 2008-11-26
Did you try to right click on the bin icon, then empty the bin folder.

---

### Post by ibuclaw on 2008-11-26
Can you post some details about the current state of your filesystem/CPU usage?

```
df -ha
```
```
top -n1
```

Regards
Iain

---

