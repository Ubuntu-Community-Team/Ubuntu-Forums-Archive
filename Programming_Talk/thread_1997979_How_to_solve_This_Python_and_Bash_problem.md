---
title: "How to solve This Python and Bash problem ?"
date: 2012-06-06
forum: Programming Talk
---

### Post by prismctg on 2012-06-06
how to put "ls -a" output in a variable in Python 3.x  ?

---

### Post by Bachstelze on 2012-06-06
This sounds like a bad idea. What exactly do you want to do?

---

### Post by prismctg on 2012-06-06
just list all file name and print them in Python

---

### Post by PeterP24 on 2012-06-06
why don't you use the functionality provided in the os module?

import os
listofdirs = os.listdir(os.getcwd())

---

