---
title: "How to make Python 3.2 default in Ubuntu 11.10?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by kramer65 on 2012-01-03
Hello,

I've got Ubuntu 11.10 installed and I now want to make Python 3.2 the default (instead of Python 2.7). Does anybody know how this would be possible?

Thanks in advance! :D

---

### Post by oldfred on 2012-01-03
You cannot without severe breakage of Ubuntu as much of it runs on python.

You should just be able to use python3 at command line or in programs make the first line like below. I have both installed and just changed this line by adding the 3. The only errors I had in a small program were my debugging print statements that then needed the ().

#!/usr/bin/python3

---

### Post by kramer65 on 2012-01-03
Ah, that seems like a good solution too.. :)

Thanks!

---

