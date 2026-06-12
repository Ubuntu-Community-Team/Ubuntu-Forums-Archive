---
title: "Noob dir permissions question"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by porteclefs on 2008-11-18
This is a ridiculously nooby question.

How do I make it so that any user can add, delete and read my directory " ../Pictures " ??

This is a question about permissions. I'm working from the terminal so I'm looking for a command...

Thanks in advance!

---

### Post by rampageoberon on 2008-11-18
```
chmod 777 /path/to/directory
```

Be careful giving full read, write, execute access to all

---

