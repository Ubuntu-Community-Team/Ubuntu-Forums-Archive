---
title: "Source code for tail, vmstat, iostat"
date: 2009-03-08
forum: Programming Talk
---

### Post by Asham on 2009-03-08
Hello

These commands are very useful but where do I get to look at the source code to see what's going on? Thanks. /Adam

---

### Post by Zugzwang on 2009-03-08
```

me@myComputer:$ whereis tail
tail: /usr/bin/tail /usr/share/man/man1/tail.1.gz

```

Visit packages.ubuntu.com. Select "Search the contents of packages" and paste "tail". Hit search and find the package "coreutils". Click on it to see the description. Then go to some newly made directory and download the source using apt-get (for this operation, no sudo rights are necessary):

```

apt-get source coreutils

```

Repeat this procedure for the other programs.

---

### Post by Asham on 2009-03-08
Very helpful, and so easy. Thank you!

I was searching with the help of Google. Didn't find much.

---

### Post by bobbocanfly on 2009-03-08
```
dpkg -S $(whereis tail | python -c "print open(\"/dev/stdin\").read().split()[1]")
```

---

### Post by geirha on 2009-03-08
Or, doing it all from the terminal:
```
$ which tail
/usr/bin/tail
$ dpkg -S /usr/bin/tail
coreutils: /usr/bin/tail
$ apt-get source coreutils 

```

---

