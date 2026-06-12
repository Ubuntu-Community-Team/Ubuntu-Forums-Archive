---
title: "Running a binary created by server without chmod +x"
date: 2009-11-23
forum: Programming Talk
---

### Post by Eathuz on 2009-11-23
I've been programming something in C that in cooperation with PHP should make the server create a binary file and afterwards execute it. But since chmod +x is not an option, do you guys have any alternatives, or is it simply a no-go?

---

### Post by A_Fiachra on 2009-11-23
No go.

That would be a massive security bug!

---

### Post by dwhitney67 on 2009-11-23
> **Eathuz said:**
> I've been programming something in C that in cooperation with PHP should make the server create a binary file and afterwards execute it. But since chmod +x is not an option, do you guys have any alternatives, or is it simply a no-go?

The C-library offers a chmod() function.  I'm not sure I quite understand your post in its entirety, namely what is inferred by 'binary file'.

---

