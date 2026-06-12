---
title: "[Questions] how to detect the status of a python thread?"
date: 2007-03-19
forum: Programming Talk
---

### Post by 3togo on 2007-03-19
Could anyone kind enough to tell me how to determine the status of a python thread started by "thread.start_new_thread". How to tell whether the thread is still running or not

Many thanks

---

### Post by thumper on 2007-03-20
From a quick read of the docs it seems like you can't.

However check out the threading module, and specifically the Thread object.  You'll probably find that this gives you the functinality that you are after.

---

### Post by pmasiar on 2007-03-20
you may want to ask Real Python Gurus on python-users mailing list on python.org, maybe you have better luck.

---

