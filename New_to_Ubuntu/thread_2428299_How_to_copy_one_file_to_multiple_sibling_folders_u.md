---
title: "How to copy one file to multiple sibling folders using the terminal?"
date: 2019-10-02
forum: New to Ubuntu
---

### Post by jafshredder on 2019-10-02
I have folders:  a  b  c  d  and  e  and in folder a I have a file I want to replicate to b c d and e   . Example: 1.txt is the file, so I want to have   a/1.txt b/1.txt  c/1.txt d/1.txt  e/1.txt     . How do I achieve that with one command? I tried   cp -R 1.txt  ../*/1.txt but it doesn't work. Any solution? Thanks!!

---

### Post by Holger_Gehrke on 2019-10-02
'cp' accepts multiple sources but only one target. This can lead to ... interesting ... problems if you give multiple sources by using a glob and forget the target ...
In your example you'd have to do something like 'cp a/1.txt b;cp a/1.txt c;cp a/1.txt d;cp a/1.txt e' or perhaps 'for i in b c d e ; do cp a/1.txt "$i"; done'. A discussion of other ways to do this -- some of them rather involved but offering some gains in speed when copying multiple large source-files to multiple targets -- can be found in this thread on [superuser.]("https://superuser.com/questions/32630/parallel-file-copy-from-single-source-to-multiple-targets")

Holger

---

### Post by spjackson on 2019-10-02
```

for dir in b c d e ; do  cp a/1.txt "$dir" ; done

```

---

### Post by The Cog on 2019-10-02
Or if you want to use symlinks instead of making actual file copies - retain one copy of the file and link to it from many places - whether you want to do this depends on your application:
```
for dir in b c d e ; do  ln -s a/1.txt "$dir/1.txt" ; done
```

---

