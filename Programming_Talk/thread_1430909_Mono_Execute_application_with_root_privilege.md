---
title: "Mono: Execute application with root privilege"
date: 2010-03-15
forum: Programming Talk
---

### Post by fmigpaulo on 2010-03-15
Is there any way to execute an application with root privileges from Mono IDE?

---

### Post by soltanis on 2010-03-15
By running the IDE under root? Not a good idea.

---

### Post by Simon17 on 2010-03-16
Are you using monodevelop?

Have you tried Project > Options > Custom Commands ?

---

### Post by fmigpaulo on 2010-03-16
I've tried now.

EXECUTE
Command: gksu

When i execute, a window pops up and then we must indicate the object that compilation has created. I choose run it as root and OK_button.

If we don't indicate the compiled object: "Custum command failed (exit code: 1)



That will do. Thanks Simon17.

---

