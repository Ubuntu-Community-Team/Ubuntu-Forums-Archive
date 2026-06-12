---
title: "[SOLVED] Can I change the owner of a file/folder?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-07
I was just wondering if that was possible. I know that I can change the permissions with chmod, but can I change the owner?

---

### Post by tuxxy on 2008-09-07
Yes use the change ownership command;

```
chown
```

for usage do

```
man chown
```

---

### Post by slughappy1 on 2008-09-07
Sweet, thanks

---

### Post by tuxxy on 2008-09-07
No problem, you can mark the thread as solved now too.

Heres a quick example that would change ownership of the file-1 to the user slughappy1

```
chown slughappy1 file-1
```

---

### Post by matt79 on 2008-09-07
Just use "chown USERNAME /directory"
Put the in place of the user name the new owner's name and then put the path to the file you want to change in place of the directory.

---

### Post by Xiong Chiamiov on 2008-09-07
You usually want to change the group, as well, if you're changing from, say, root to you.
```

sudo chown [user]:users [file]

```

For a folder, if you want to change the ownership of all the files inside it, add a -R to the end for recursive.

---

