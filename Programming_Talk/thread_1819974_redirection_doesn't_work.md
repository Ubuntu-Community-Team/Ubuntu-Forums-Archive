---
title: "redirection doesn't work"
date: 2011-08-07
forum: Programming Talk
---

### Post by chuchi on 2011-08-07
hi!! I want to capture the output of a program, but when I run "./myprogram > output.txt" the file "output.txt" is empty!!! Why???

Thank you very much!!

---

### Post by GeneralZod on 2011-08-07
Perhaps it's printed to stderr instead of stdout.

---

### Post by chuchi on 2011-08-07
How can I see the output on stderr?

---

### Post by GeneralZod on 2011-08-07
> **chuchi said:**
> How can I see the output on stderr?

A nice page on redirection here:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

---

### Post by unknownPoster on 2011-08-07
It would also help if you provided the source code so we can find any potential errors or problems.

---

### Post by chuchi on 2011-08-08
Thank you very much!! that worked for me!!

---

