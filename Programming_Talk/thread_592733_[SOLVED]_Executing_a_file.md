---
title: "[SOLVED] Executing a file"
date: 2007-10-26
forum: Programming Talk
---

### Post by Zer0d on 2007-10-26
I'm making a small program in C++ and compiling it into .out file format. I have no problem running it on my computer but when I transfer it to a friend's computer and try to run it in SSH(Logged in as root) I only get error message:
```

cd *folderwithfile*
root@*:/*/*# ./1.out
bash: ./1.out: Permission denied

```
It's like the computer doesn't understand the file format so I also tried only naming it to 1. It also has chmod 777 rights. I don't have any problems running this program on my own computer with same command. Why is that?

---

