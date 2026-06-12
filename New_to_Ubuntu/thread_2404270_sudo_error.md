---
title: "sudo error"
date: 2018-10-22
forum: New to Ubuntu
---

### Post by jiaming66 on 2018-10-22
I am trying to install Pandas, and pip. But got this same error:
>>> sudo apt-get install python-pip
  File "<stdin>", line 1
    sudo apt-get install python-pip
           ^
SyntaxError: invalid syntax
>>> sudo apt-get install python-pandas
  File "<stdin>", line 1
    sudo apt-get install python-pandas
           ^
SyntaxError: invalid syntax

What is wrong? Seems I got this same error whatever I try to install. Thanks.

---

### Post by Holger_Gehrke on 2018-10-22
The prompt and the error message make me think you're trying to enter shell commands in the python interpreter. That obviously won't work.

Holger

---

