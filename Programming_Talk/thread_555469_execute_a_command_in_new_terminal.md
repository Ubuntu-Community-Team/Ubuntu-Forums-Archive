---
title: "execute a command in new terminal"
date: 2007-09-20
forum: Programming Talk
---

### Post by mokkai on 2007-09-20
any idea to open a new 

"gnome-terminal ,and execute a command"
on that terminal
 
fron base terminal

i tried like this "gome-terminal -e,-execute =ls --window"

but execution output is not shown in newly created terminal

why ??

---

### Post by BuffaloX on 2007-09-20
Closest I can get is:

gnome-terminal -x sh -c "cal -3; sleep 5"

Which shows the calendar for 5 seconds, then the terminal terminates itself.

---

### Post by Ramses de Norre on 2007-09-20
> **BuffaloX said:**
> Closest I can get is:

gnome-terminal -x sh -c "cal -3; sleep 5"

Which shows the calendar for 5 seconds, then the terminal terminates itself.

```
gnome-terminal -x bash -c "cal -3;bash"
```

---

### Post by mokkai on 2007-09-21
thats i want...
thank you frineds....

---

### Post by W29 on 2011-05-23
> **Ramses de Norre said:**
> ```
gnome-terminal -x bash -c "cal -3;bash"
```
Thank you. This is very helpful.

---

### Post by hakermania on 2011-05-23
mark the thread as solved please :D

---

