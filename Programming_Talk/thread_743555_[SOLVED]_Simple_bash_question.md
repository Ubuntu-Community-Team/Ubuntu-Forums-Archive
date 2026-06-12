---
title: "[SOLVED] Simple bash question"
date: 2008-04-02
forum: Programming Talk
---

### Post by WarMonkey on 2008-04-02
Is there a single command I can use for merging directories?

---

### Post by finer recliner on 2008-04-02
```

davef@laptop:~$ mkdir test1 test2     #create directories test1/ and test2/
davef@laptop:~$ cd test1                  #go into test1/
davef@laptop:~/test1$ touch a b c     #create empty files a b and c
davef@laptop:~/test1$ cd ../test2      # go into test2/
davef@laptop:~/test2$ touch d e f     #create empty files d e and f
davef@laptop:~/test2$ cd ..              # go up one level (back to home directory)
davef@laptop:~$ mv test1/* test2     #move all files in test1/ into test2/    **this is the command you want! **
davef@laptop:~$ ls test2/                 #show contents of test2/
a  b  c  d  e  f
davef@laptop:~$ ls test1/                  #show contents of test1/    (nothing)
davef@laptop:~$

```

enjoy

---

