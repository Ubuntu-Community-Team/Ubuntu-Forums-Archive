---
title: "Execution of a.out"
date: 2012-01-16
forum: Programming Talk
---

### Post by achuth on 2012-01-16
Why is it necessary to include **./** when we execute **a.out** eventhough we are in the folder where **a.out** is located?

---

### Post by Bachstelze on 2012-01-16
It's a security measure so that if you have an executable in the CWD that has the same name as a common command, you will not accidentally execute that program (in case it's malicious).

---

### Post by Arndt on 2012-01-17
> **achuth said:**
> Why is it necessary to include **./** when we execute **a.out** eventhough we are in the folder where **a.out** is located?

The directories mentioned in $PATH are inspected. If "." is not there (and it may be a good idea not to have it there), you have to prefix the name of the executable.

---

### Post by Simian Man on 2012-01-17
You can get around this by appending "." to your PATH by putting "export PATH=$PATH:." into you ~/.bashrc file.  This avoids the problem Bachstelze mentioned because the shell will search the places builtin programs live (/bin, /usr/bin, /usr/local/bin) first and only use . when the command isn't found in the default places.

---

