---
title: "Shell Scripting Pause Command?"
date: 2006-10-02
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-02
Is there a BASH command that creates a pause of x amount of seconds before allowing the program to continue?

Best,
Tom

---

### Post by eeGhoong0ais on 2006-10-02
```
sleep 5s
```waits for five seconds
```
sleep 2m
```waits for two minutes
... etc.
```
man sleep
```gives you the complete details.

---

### Post by thomasaaron on 2006-10-02
Thank you.

Tom

---

