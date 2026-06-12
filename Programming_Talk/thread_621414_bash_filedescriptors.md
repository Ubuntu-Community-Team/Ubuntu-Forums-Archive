---
title: "bash filedescriptors"
date: 2007-11-23
forum: Programming Talk
---

### Post by go_beep_yourself on 2007-11-23
What does this do in bash?

command >&- 2>&-

---

### Post by dwhitney67 on 2007-11-23
Here's you answer:

Something stupid.  It will create a file called "-" in the local directory, undoubtedly containing the error from doing "*command* >&-".

---

