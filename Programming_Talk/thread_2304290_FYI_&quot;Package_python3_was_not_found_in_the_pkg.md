---
title: "FYI: &quot;Package python3 was not found in the pkg-config search path.&quot; solved"
date: 2015-11-25
forum: Programming Talk
---

### Post by sanderj on 2015-11-25
FYI (as I couldn't find this info via Google):

I got

```
$ pkg-config --cflags --libs python3
Package python3 was not found in the pkg-config search path.
Perhaps you should add the directory containing `python3.pc'
to the PKG_CONFIG_PATH environment variable
No package 'python3' found
```


Solution was:

```
sudo apt-get install python3-dev
```

Proof:

```
$ pkg-config --cflags --libs python3
-I/usr/include/python3.4m -I/usr/include/x86_64-linux-gnu/python3.4m  -lpython3.4m

```

HTH

---

