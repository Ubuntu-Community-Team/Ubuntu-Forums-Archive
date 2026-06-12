---
title: "python multiplatform single instance check"
date: 2010-02-14
forum: Programming Talk
---

### Post by giuspen on 2010-02-14
Hi,

I'm searching for a way to check whether another instance of my python app is already running, but googleing I did not find a working solution.
Can anyone help me with a couple of lines of code?
My app runs also on windows, so I need this solution to be cross platform.
Thanks in advance.

---

### Post by Reiger on 2010-02-14
The easy thing to do is to create a lock file.

---

### Post by giuspen on 2010-02-14
I tried locking with
[PHP]fd = open(LOCK_PATH, 'w')
fcntl.lockf(fd, fcntl.LOCK_EX)[/PHP]
but the problem is that further instances when launched do not give any error but just wait for the file to be unlocked :(

---

### Post by giuspen on 2010-02-14
for who interested, this solves the problem:
[PHP]fcntl.lockf(fd, fcntl.LOCK_EX | fcntl.LOCK_NB)[/PHP]

---

