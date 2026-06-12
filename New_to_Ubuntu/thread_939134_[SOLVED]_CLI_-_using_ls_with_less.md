---
title: "[SOLVED] CLI - using ls with less"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-05
I want to list a directory with a lot of material but the terminal buffer thing stops the list from z-p so I think I use less but I'm not formating the command correctly.  How's it go?

---

### Post by sisco311 on 2008-10-05
```
ls | less
```
```
ls -al /path/to/dir | less
```

---

### Post by adamogardner on 2008-10-05
Ahh ok thanks cisco.  I needed a pipe.

---

### Post by Joeb454 on 2008-10-05
Don't forget to mark as solved :)

Learning the CLI is always a good idea :) I know I'm glad I know it reasonably well

---

