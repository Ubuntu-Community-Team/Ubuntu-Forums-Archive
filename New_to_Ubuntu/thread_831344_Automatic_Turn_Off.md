---
title: "Automatic Turn Off"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by D|F on 2008-06-16
Hello, Im using ubuntu 7.10 gutdy gibbon (KDE desktop). 
i have some question here, there is the way that i can turn off my system automatic? if i watching movie, then after ending movie it will be shut down automaticly...

---

### Post by cariboo on 2008-06-16
You can use the shutdown command:

```
shutdown -h <time>
```

for instance in a termianl you can enter:

```
shutdown -h 20
```

this will shutdown the computer after 20 minutes has elapsed

For further in fo on the shutdown command in a terminal type:

```
man shutdown
```

One final thing, just minimize the terminal as closing it will stop the shutdown command.

Jim

---

### Post by D|F on 2008-06-16
Thanxs Bro ...

---

