---
title: "How to extract a specific file from the archive to a specific location?"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by aayus on 2013-06-08
I am trying to extract a file using this command in the open_data folder:

```
tar  xvf  archive1.tar  ./rayinvr/tramp/amp.f  -C  ./open_data/
```

but it always extract the file back in the home folder.

---

### Post by sum1nil on 2013-06-08
From the folks at StackOverflow: [http://stackoverflow.com/questions/9249603/how-to-extract-a-single-file-from-tar-to-a-different-directory](http://stackoverflow.com/questions/9249603/how-to-extract-a-single-file-from-tar-to-a-different-directory)


> The problem is that your arguments are in incorrect order. The single file argument must be last.

E.g.

$ tar xvf test.tar -C anotherDirectory/ testfile1

should do the trick.
...

The thread was closed at that answer, but I can't say I have tried it.
Hope it works for you.

---

