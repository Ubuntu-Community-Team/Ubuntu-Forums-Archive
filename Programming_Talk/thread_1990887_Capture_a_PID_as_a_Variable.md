---
title: "Capture a PID as a Variable"
date: 2012-05-30
forum: Programming Talk
---

### Post by Living2007 on 2012-05-30
I'm writing a small program which involves a background process. I'm using the "&" attribute with UNIX and it prints the PID, but not in the script. I know it's been stored somewhere, but I want to capture the PID, so when the user want to close the script, the background process is killed by that stored PID!

---

### Post by diesch on 2012-05-30
```
background_process &
PID="$!"
```

---

### Post by sisco311 on 2012-05-30
[http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)

---

### Post by Living2007 on 2012-06-05
Awesome, I'll give those a try!!

---

