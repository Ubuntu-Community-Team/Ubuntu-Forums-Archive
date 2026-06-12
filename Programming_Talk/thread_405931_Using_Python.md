---
title: "Using Python"
date: 2007-04-10
forum: Programming Talk
---

### Post by LaRoza on 2007-04-10
I have a few questions about Python. I have a feeling I know who is going to answer...

I do not have an internet connection at home, so downloading tools is not feasible.

My questions are:

1. Can I connect to a MySQL database with what I have?

2. Can I use my Python programs on Windows?

3. Can I connect to any other database,OO Base or MS Access?

Thanks for your help.

---

### Post by rufius on 2007-04-10
I can confidently say the answer to questions 1 and 2 is yes. As for question 3, I'm about 95% sure that you can.

---

### Post by LaRoza on 2007-04-10
Thanks. With MySQL, I don't need the others.

---

### Post by pmasiar on 2007-04-10
1, 3) sqlite is library,not full server. Single user, but simpler. Of course you can use any database for whih you have binding, including Oracle :-)

2) Yes - Python is rather portable. Check os module - path separator is different etc, so you need to take care.

---

