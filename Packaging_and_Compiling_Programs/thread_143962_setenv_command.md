---
title: "setenv command"
date: 2006-03-13
forum: Packaging and Compiling Programs
---

### Post by frogotronic on 2006-03-13
I am trying to compile a program which requires me to execute the command
setenv ACEDB_MACHINE LINUX_4. However, Ubuntu replies setenv command not found. Please advise.

Thanks,
Andor

---

### Post by muted on 2006-04-20
i second this :](*,)

---

### Post by lovebyte on 2006-04-21
setenv is used by tcsh.  With bash you do:
export ACEDB_MACHINE=LINUX_4

(I think)

---

