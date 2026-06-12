---
title: "how many jobs am i running?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by gotquestions on 2008-08-25
Hello :)
I have a Konsole with many sessions like 5 or 6. The problem is that I have some jobs running and I dont know which session it is. I could easily do like a Ctrl-Z and they type "jobs" then do a kill %x . 

Is there a cmd in which I can find out all of my jobs running on all of my sessions?

---

### Post by sisco311 on 2008-08-25
```
ps ux
```
or
```
ps aux
```

for more info read the man page:
```
man ps
```

---

### Post by Ryadt on 2008-08-25
Try ```
ps -ef
```

---

### Post by gotquestions on 2008-08-25
[ ps -ef ]

Wow it shows me a lot of things. With that command how do I:

1. just see the jobs run today  
2. and also a date range like from aug 1 to Aug 25?

---

