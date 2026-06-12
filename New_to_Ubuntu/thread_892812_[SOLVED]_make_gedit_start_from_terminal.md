---
title: "[SOLVED] make gedit start from terminal"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by spydon on 2008-08-17
Hi, I want gedit to start from the terminal but not close down when I close the terminal. I want to keep using the same terminal after I have written fro example:
```
gedit *.java
```

Is it a way to do that?

---

### Post by dje on 2008-08-17
> **spydon said:**
> Hi, I want gedit to start from the terminal but not close down when I close the terminal. I want to keep using the same terminal after I have written fro example:
```
gedit *.java
```

Is it a way to do that?

try this:
```
gedit *.java &
```

dje

---

### Post by spydon on 2008-08-17
Aah thank you, exactly what I wanted!

---

