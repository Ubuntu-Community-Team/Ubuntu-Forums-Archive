---
title: "jar file as executing program permissions"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by werty2010 on 2011-12-09
can a java program(jar file) which launches from terminal,without sudo privileges,to make any substantial changes to the system generally?
also is there a chance to get/send personal data "outside" without my permission(for example getting data from other applications i use)?

---

### Post by donkyhotay on 2011-12-10
> **werty2010 said:**
> can a java program(jar file) which launches from terminal,without sudo privileges,to make any substantial changes to the system generally?
also is there a chance to get/send personal data "outside" without my permission(for example getting data from other applications i use)?

Without sudo a program can not make any major changes to the system (unless of course you've modified or changed your file permissions). Now your personal data within the 'home' folder is a different story. Most of that stuff can be read/modified without sudo. That is why it is important to only install software from trusted sources. The most trust comes from being able to review the source code yourself (or someone else you trust) who can verify there is nothing fishy in there.

---

### Post by The Cog on 2011-12-10
The fact that it's a java program rather than being written in any other language makes no difference. If you launch a program from your account, it runs with your privileges and can read/write anything that any other program running under your account can read and write. As such, it cannot make changes that you need sudo to do, but it has full read/write access to all the files in your home, and access to the internet.

---

### Post by ilikelinuxitisthebest on 2011-12-10
just a suggestion. could you mark this thread solved? It makes the forums a little more organized. thanks.

---

### Post by werty2010 on 2011-12-10
thank you all for your answers

---

